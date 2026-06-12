---
title: "Stopped installing"
date: 2008-08-16
forum: General Help
---

### Post by HpZ on 2008-08-16
Ubuntu has stopped installing from the live CD. It's stuck at 92% and I can't hear the disc spinning, though that seems to be the only thing that has stopped working on the live CD. The application hasn't crashed and this must be the 10th time that its done the same thing. Here is my installer log.

> Ubiquity 1.0.12
Sat, 16 Aug 2008 09:47:28 INFO     switched to page stepLanguage
ubiquity: Starting up '['/usr/lib/ubiquity/localechooser/localechooser']' for ubiquity.components.language.Language
ubiquity: Watching for question patterns ^languagechooser/language-name
Sat, 16 Aug 2008 09:47:50 INFO     Step_before = stepLanguage
Sat, 16 Aug 2008 09:47:51 INFO     switched to page stepLocation
Sat, 16 Aug 2008 09:47:51 INFO     Step_after = stepLocation
ubiquity: Starting up '['/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
ubiquity: Watching for question patterns ^time/zone$
Sat, 16 Aug 2008 09:47:58 INFO     Step_before = stepLocation
Sat, 16 Aug 2008 09:47:58 INFO     switched to page stepKeyboardConf
Sat, 16 Aug 2008 09:47:58 INFO     Step_after = stepKeyboardConf
ubiquity: kbd-chooser prepare
ubiquity: Starting up '['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser']' for ubiquity.components.kbd_chooser.KbdChooser
ubiquity: Watching for question patterns ^kbd-chooser/method$, ^console-keymaps.*/keymap$, ERROR
ubiquity: apply_keyboard: uk
ubiquity: apply_keyboard: layout gb
ubiquity: Display map: {u'Swedish': u'se-latin1', u'Icelandic': u'is-latin1', u'Estonian': u'et', u'Romanian': u'ro', u'Italian': u'it', u'Latin American': u'la-latin1', u'Dutch': u'nl', u'Brazilian (EUA layout)': u'br-latin1', u'Belgian': u'be2-latin1', u'Danish': u'dk-latin1', u'Bulgarian': u'bg', u'Turkish (F layout)': u'trfu', u'Hungarian': u'hu', u'Macedonian': u'mk', u'Lithuanian': u'lt', u'French': u'fr-latin9', u'Norwegian': u'no-latin1', u'Slovakian': u'sk-qwerty', u'Russian': u'ru', u'Dvorak': u'dvorak', u'Slovene': u'slovene', u'Finnish': u'fi-latin1', u'British English': u'uk', u'Spanish': u'es', u'Greek': u'gr', u'Canadian French': u'cf', u'Latvian': u'lv-latin4', u'American English': u'us', u'Croatian': u'croat', u'Portuguese': u'pt-latin1', u'Czech': u'cz-lat2', u'Ukrainian': u'ua', u'Japanese': u'jp106', u'Belarusian': u'by', u'Turkish (Q layout)': u'trqu', u'German': u'de-latin1-nodeadkeys', u'Hebrew': u'hebrew', u'Polish': u'pl', u'Brazilian (ABNT2 layout)': u'br-abnt2', u'Swiss French': u'fr_CH-latin1', u'Swiss German': u'sg-latin1', u'Serbian (Cyrillic)': u'sr-cy'}
ubiquity: Untranslated choices: [u'by', u'bg', u'croat', u'cz-lat2', u'sg-latin1', u'de-latin1-nodeadkeys', u'dk-latin1', u'us', u'uk', u'dvorak', u'et', u'es', u'la-latin1', u'fi-latin1', u'fr-latin9', u'be2-latin1', u'cf', u'fr_CH-latin1', u'gr', u'hebrew', u'hu', u'is-latin1', u'it', u'lt', u'lv-latin4', u'jp106', u'mk', u'no-latin1', u'nl', u'pl', u'pt-latin1', u'br-abnt2', u'br-latin1', u'ro', u'ru', u'sk-qwerty', u'slovene', u'sr-cy', u'se-latin1', u'trfu', u'trqu', u'ua']
ubiquity: Choices: [u'Belarusian', u'Bulgarian', u'Croatian', u'Czech', u'Swiss German', u'German', u'Danish', u'American English', u'British English', u'Dvorak', u'Estonian', u'Spanish', u'Latin American', u'Finnish', u'French', u'Belgian', u'Canadian French', u'Swiss French', u'Greek', u'Hebrew', u'Hungarian', u'Icelandic', u'Italian', u'Lithuanian', u'Latvian', u'Japanese', u'Macedonian', u'Norwegian', u'Dutch', u'Polish', u'Portuguese', u'Brazilian (ABNT2 layout)', u'Brazilian (EUA layout)', u'Romanian', u'Russian', u'Slovakian', u'Slovene', u'Serbian (Cyrillic)', u'Swedish', u'Turkish (F layout)', u'Turkish (Q layout)', u'Ukrainian']
ubiquity: console-keymaps-at/keymap db: uk
Sat, 16 Aug 2008 09:48:08 INFO     switched to page stepLocation
ubiquity: ['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser'] exited with code 10
ubiquity: Starting up '['/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
ubiquity: Watching for question patterns ^time/zone$
Sat, 16 Aug 2008 09:48:24 INFO     Step_before = stepLocation
Sat, 16 Aug 2008 09:48:24 INFO     switched to page stepKeyboardConf
Sat, 16 Aug 2008 09:48:25 INFO     Step_after = stepKeyboardConf
ubiquity: kbd-chooser prepare
ubiquity: Starting up '['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser']' for ubiquity.components.kbd_chooser.KbdChooser
ubiquity: Watching for question patterns ^kbd-chooser/method$, ^console-keymaps.*/keymap$, ERROR
ubiquity: apply_keyboard: uk
ubiquity: apply_keyboard: layout gb
ubiquity: Display map: {u'Swedish': u'se-latin1', u'Icelandic': u'is-latin1', u'Estonian': u'et', u'Romanian': u'ro', u'Italian': u'it', u'Latin American': u'la-latin1', u'Dutch': u'nl', u'Brazilian (EUA layout)': u'br-latin1', u'Belgian': u'be2-latin1', u'Danish': u'dk-latin1', u'Bulgarian': u'bg', u'Turkish (F layout)': u'trfu', u'Hungarian': u'hu', u'Macedonian': u'mk', u'Lithuanian': u'lt', u'French': u'fr-latin9', u'Norwegian': u'no-latin1', u'Slovakian': u'sk-qwerty', u'Russian': u'ru', u'Dvorak': u'dvorak', u'Slovene': u'slovene', u'Finnish': u'fi-latin1', u'British English': u'uk', u'Spanish': u'es', u'Greek': u'gr', u'Canadian French': u'cf', u'Latvian': u'lv-latin4', u'American English': u'us', u'Croatian': u'croat', u'Portuguese': u'pt-latin1', u'Czech': u'cz-lat2', u'Ukrainian': u'ua', u'Japanese': u'jp106', u'Belarusian': u'by', u'Turkish (Q layout)': u'trqu', u'German': u'de-latin1-nodeadkeys', u'Hebrew': u'hebrew', u'Polish': u'pl', u'Brazilian (ABNT2 layout)': u'br-abnt2', u'Swiss French': u'fr_CH-latin1', u'Swiss German': u'sg-latin1', u'Serbian (Cyrillic)': u'sr-cy'}
ubiquity: Untranslated choices: [u'by', u'bg', u'croat', u'cz-lat2', u'sg-latin1', u'de-latin1-nodeadkeys', u'dk-latin1', u'us', u'uk', u'dvorak', u'et', u'es', u'la-latin1', u'fi-latin1', u'fr-latin9', u'be2-latin1', u'cf', u'fr_CH-latin1', u'gr', u'hebrew', u'hu', u'is-latin1', u'it', u'lt', u'lv-latin4', u'jp106', u'mk', u'no-latin1', u'nl', u'pl', u'pt-latin1', u'br-abnt2', u'br-latin1', u'ro', u'ru', u'sk-qwerty', u'slovene', u'sr-cy', u'se-latin1', u'trfu', u'trqu', u'ua']
ubiquity: Choices: [u'Belarusian', u'Bulgarian', u'Croatian', u'Czech', u'Swiss German', u'German', u'Danish', u'American English', u'British English', u'Dvorak', u'Estonian', u'Spanish', u'Latin American', u'Finnish', u'French', u'Belgian', u'Canadian French', u'Swiss French', u'Greek', u'Hebrew', u'Hungarian', u'Icelandic', u'Italian', u'Lithuanian', u'Latvian', u'Japanese', u'Macedonian', u'Norwegian', u'Dutch', u'Polish', u'Portuguese', u'Brazilian (ABNT2 layout)', u'Brazilian (EUA layout)', u'Romanian', u'Russian', u'Slovakian', u'Slovene', u'Serbian (Cyrillic)', u'Swedish', u'Turkish (F layout)', u'Turkish (Q layout)', u'Ukrainian']
ubiquity: console-keymaps-at/keymap db: uk
Sat, 16 Aug 2008 09:48:27 INFO     Step_before = stepKeyboardConf
Sat, 16 Aug 2008 09:48:27 INFO     switched to page stepUserInfo
Sat, 16 Aug 2008 09:48:27 INFO     Step_after = stepUserInfo
ubiquity: Starting up '['/usr/lib/ubiquity/user-setup/user-setup-ask', '/target']' for ubiquity.components.usersetup.UserSetup
ubiquity: Watching for question patterns ^passwd/user-fullname$, ^passwd/username$, ^passwd/user-password$, ^passwd/user-password-again$, ERROR
ON STATE: 1
ON STATE: 2
ON STATE: 3
ON STATE: 4
ON STATE: 5
ON STATE: 6
ON STATE: 7
ON STATE: 8
Sat, 16 Aug 2008 09:48:36 INFO     Step_before = stepUserInfo
Sat, 16 Aug 2008 09:48:36 INFO     switched to page stepPartDisk
Sat, 16 Aug 2008 09:48:36 INFO     Step_after = stepPartDisk
ubiquity: Starting up '/bin/partman' for ubiquity.components.partman.Partman
ubiquity: Watching for question patterns ^partman-auto/select_disk$, ^partman-auto/.*automatically_partition$, ^partman-partitioning/new_size$, ^partman/choose_partition$, ^partman/confirm.*, type:boolean, ERROR, PROGRESS
unsupported
kernelmodules_basicfilesystems
kernelmodules_ext3
kernelmodules_jfs
kernelmodules_reiserfs
kernelmodules_xfs
umount_target
parted
dump
update_partitions
filesystems_detected
auto_mountpoints
autouse_swap
backup
Sat, 16 Aug 2008 09:48:43 INFO     switched to page stepPartAuto
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
Sat, 16 Aug 2008 09:48:46 INFO     switched to page stepReady
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
ubiquity: Watching for question patterns ^ubiquity/summary$
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
umount /target/
swapoff /dev/hda5
chroot: cannot run command `apt-get': No such file or directory
Sat, 16 Aug 2008 09:50:51 INFO     progress_loop()
ubiquity: Starting up '['/usr/share/ubiquity/install.py']' for ubiquity.components.install.Install
ubiquity: Watching for question patterns ^.*/apt-install-failed$, CAPB, ERROR, PROGRESS
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
ubiquity: Starting up '['sh', '-c', '/usr/lib/ubiquity/localechooser/post-base-installer && /usr/lib/ubiquity/localechooser/prebaseconfig']' for ubiquity.components.language_apply.LanguageApply
Reading package lists...
Building dependency tree...
Skipping locales, it is already installed and upgrade is not set.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
E: Couldn't find package localization-config
Reading package lists...
Building dependency tree...
Skipping console-tools, it is already installed and upgrade is not set.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubiquity: Starting up '['/usr/share/ubiquity/apt-setup']' for ubiquity.components.apt_setup.AptSetup
/usr/lib/ubiquity/apt-setup/generators/01setup: line 7: /target/etc/apt/sources.list: No such file or directory
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release [34.8kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages [619kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages [4571B]
Fetched 659kB in 2s (224kB/s)
Reading package lists...
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources [255kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources [1478B]
Fetched 257kB in 1s (198kB/s)
Reading package lists...
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [50.9kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [284kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [6702B]
Fetched 342kB in 1s (202kB/s)
Reading package lists...
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [76.1kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [983B]
Fetched 77.1kB in 0s (113kB/s)
Reading package lists...
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [154kB]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [8706B]
Fetched 213kB in 1s (173kB/s)
Reading package lists...
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Fetched 1B in 0s (2B/s)
Reading package lists...
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [30.9kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [983B]
Fetched 31.9kB in 0s (51.7kB/s)
Reading package lists...
Sat, 16 Aug 2008 09:57:00 INFO     keeping language packs for: en
ubiquity: Starting up '['/usr/lib/ubiquity/tzsetup/prebaseconfig']' for ubiquity.components.timezone_apply.TimezoneApply
ubiquity: Starting up '['/usr/share/ubiquity/clock-setup']' for ubiquity.components.clock_setup.ClockSetup
ubiquity: Starting up '['/usr/lib/ubiquity/kbd-chooser/prebaseconfig']' for ubiquity.components.kbd_chooser_apply.KbdChooserApply
ubiquity: Starting up '['/usr/lib/ubiquity/user-setup/user-setup-apply', '/target']' for ubiquity.components.usersetup_apply.UserSetupApply
ubiquity: Starting up '['/bin/hw-detect']' for ubiquity.components.hw_detect.HwDetect
find: WARNING: Hard link count is wrong for /lib/modules/2.6.15-23-386/kernel: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.


---

### Post by linux_tech on 2008-08-16
Try download again, make new cd, run install - [http://releases.ubuntu.com/8.04.1/](http://releases.ubuntu.com/8.04.1/)

What are the system specs?

---

### Post by Tom--d on 2008-08-16
At 92%, for me its configuring my hardware. So the CD will not spin at that time.

^^ above, get a new cd and post your system specs.

It maybe due to lack of RAM?

---

