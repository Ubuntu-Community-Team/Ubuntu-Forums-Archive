---
title: "Plan for reinstall on secured laptop"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by John Wiersba on 2009-01-09
I'm planning ahead for easy upgrades on my laptop.  One of my goals is to have a simple configuration which allows for testing of the next release.  Also, I want my hard disk encrypted for security.

Here's what I've done so far and my reasoning.  Can anyone comment on the viability of this plan or offer suggestions for a better configuration?

I installed my laptop from the 8.10 alternate CD, creating two physical partitions: boot + an encrypted partition with LVM inside containing 4 logical partitions: /, home, swap, and a spare-/.

I used this configuration because I intend to be able to do the following major administration tasks:
[LIST=1]
   [*]Normal operation: Cold boot, prompt for passphrase/USBkey, then automatically log into my user account with everything unlocked (including wireless keychain). That is, I want to enter credentials only once (at the post-grub prompt for unlocking my encrypted partition).
   [*]Boot from Live Desktop CD, load modules, etc., and use it as a rescue CD where I can still access the logical LVM partitions described above.
   [*]Create a Live Rescue CD which includes all the prerequisites for doing #2 already on the CD (so I don't need a network).
   [*]My plan for upgrading to a the next Ubuntu release is to do a fresh install instead of an upgrade. For this I will want to install the new version of Ubuntu (Jaunty) in the spare-/ logical partition I've set aside above, in order to try Jaunty out. To do that I will need to be able to install into an already existing logical partition inside an encrypted partition. After installation, I will need to be able to switch at boot time (from the grub menu) to either the old / partition (8.10) or the new / partition (9.4) at will. The old / will mount my home partition on /home, but the new / will not (it will be self-contained within one partition). Once I'm confident that everything is working in the Jaunty install, I will shuffle things around a bit and then mount my home partition onto /home in the Jaunty partition and make that my default.

[/LIST]

---

### Post by John Wiersba on 2009-01-29
After thinking some more about this, here is what I implemented
[LIST]
[*]I really like the LUKS-encrypted LVM partition for a single-user laptop configuration.  It allows you to have one passphrase to unlock everything and set everything after that (automatic login, automatic connect to network, task-based scripts containing hardcoded passwords, etc) without needing to worry about the need to secure things so much, since the entire disk is already secured (when the laptop is shut down).
[*]In order to support reinstallation of a new OS version (or even the same OS version), I decided that /home/USER, which contains all the version-specific rc files and directories should be on the root (OS-version-specific) partition.  That way when the OS is reinstalled, all the rc files and dirs are cleaned up.
[*]My personal data, which is OS-independent, is kept in /data and symlinked into /home/USER.  This is the data which is invariant between OS versions.  Certain things (like the firefox configuration in ~/.mozilla) are kept on /data, whereas most other tool configurations are left under the / partition (in /home/USER/.*).
[*]Therefore, I create 3 LVM partitions inside my LUKS-encrypted container: swap, root, data.
[*]Instead of planning for a second OS installation on my laptop's harddisk, I am now making room for it on my external USB backup harddisk.
[*]To boot from my second OS installation on my external harddisk, I can set my BIOS flag to boot from USB.  Or I can copy the /boot/grub/menu.lst items from the boot partition on my external USB harddisk (along with the referenced files) to my laptop's main /boot/grub/menu.lst and /boot directory.
[*]Actually, I turn off USB booting so that I don't get a boot error when I leave a USB thumb drive (without a bootable partition) plugged in.
[*]I use my USB external disk as a rescue system, as it's much faster than the live CD.
[*]I have two external backup drives so that I can reformat or play around with one of them and still have a working current backup.
[*]I use rsnapshot to make incremental backups of /boot, /etc, /home, /data.
[/LIST]

---

