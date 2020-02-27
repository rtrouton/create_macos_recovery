# create_macos_recovery
Tool for repairing the Recovery volume (APFS) or partition (HFS+) on Macs running macOS 10.13.x or later.

This script uses a macOS 10.13 and later installer application to repair the Recovery volume (APFS) or partition (HFS+).

**Pre-requisites**

1. This script
2. An installer from Apple's Mac App Store for one of the following versions of macOS:

* 10.13.x
* 10.14.x
* 10.15.x


**Running the script**

Run the `create_macos_recovery.sh` script with one argument: the path to an "Install macOS.app".

`/path/to/create_macos_recovery.sh "/path/to/Install macOS [Name].app"`


Example usage: 

If you have a macOS Catalina 10.15.x installer available, run this command:

`sudo /path/to/create_macos_recovery.sh "/Applications/Install macOS Catalina.app"`

This should replace the existing Recovery volume or partition with a fresh install, using the Recovery installation tools available from the macOS installer app.


What the script does:

1. Downloads the following installer package from Apple's Software Update service: `SecUpd2020-001HighSierra.RecoveryHDUpdate.pkg`

2. Expands `SecUpd2020-001HighSierra.RecoveryHDUpdate.pkg` into a directory in `/private/tmp` in order to get access to the `dm` tool included with this installer package.

3. Uses the `dm` tool and the Recovery installation tools available from the macOS installer app to rebuild the Recovery volume or partition.

4. Cleans up by removing the downloaded `SecUpd2020-001HighSierra.RecoveryHDUpdate.pkg` and expanded package contents.

This script has been tested with the following OS installers from the Mac App Store:

* macOS 10.13.6
* macOS 10.14.6
* macOS 10.15.0
