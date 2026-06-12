---
title: "Clean breezy installation failure"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by janlin1975 on 2005-12-16
Hi 

Please help

My target system is P3, 256MB RAM, 80GB HD, mounted an ethernet card without any network connection yet

Burning with my laptop burner on my XP system

Using md5ummer md5 check.

Sum generated on md5ummer.

Compared that visually with ubuntu-5.10-install-i386.iso.md5 file which has a value of 126751a2dc5528c2f9044d9e4ee36d61

So i presume md5 check okay

Proceeded to installation.

Got up to the point where it starts "installating packages" after rebooting.

Generates an error message

config fdutils

68%

It hangs and a message

ext3fs error device and some other codes

reboot the system

and it gives a message

fsck failed

root filesystem mounted read only

remount it r/w

# mount -n-o remount,rw/

typed this on the prompt exited and rebooted. same error appears.


I am a newbie. I have burned 3 cds at lower speeds progressively down to 1200k/s

all sum check seem okay.

Many thanks.

---

### Post by janlin1975 on 2005-12-19
Still having a problem with my installation on my P3 system.

Good news is that I have successfully installed on my P2 system.

Can this be a hardware firmware problem. Not the hard disks, as the P2 hd was used for the P3 and the same problem arose. Read in the manual that pre os virus scan should be disabled. Did that and with the video shadowing disabling and alas…. The same failure messages.

The system hangs while installing packages. It has an error code as below. 



[1359.146994} EXT-fs error (device hda1): ext3_free_blocks_sb: bit already cleared for block 1425853

[1359.1477171] Remounting filesystem read-only



Can anyone make out the meaning of the error codes down below?
After reboot

Uncompressing linux... Ok, booting the kernel.
[4294667.296000] ACPI: unable to locate RSDP

Loading please wait...

FATAL: Error inserting fan (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/fan.ko): No such device
FATAL: Error inserting thermal (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/thermal.ko): No such device
/contains a file system with errors, check forced.
Deleted inode 82601 has zero dtime. FIXED
Duplicate or bad block in use!
Multiply-claimed block(S) in inode 117268: 256189
Multiply-claimed block(s) in inode 117406: 256189
(There are 2 inodes containing multiply-claimed blocks.)
File /usr/share/man/man/man8/dmesg.8.gz (inode #117268, mod time Tue Sep 17:43:35 2005
has 1 multioly-claimed block(s), shared with 1 file(s):
/usr/share/doc/tar (inode #117406, mod time Mon Dec 19 12:29:59 2005)
UNEXPECTED INCONSISTENCY; Run fsch MANUALLY.
(ie without -a or -p options)
fsch failed. Please repair manually and reboot. Please noe that the root file system is currently mounted read-only. to remount it read-write:
# mount -n -o remount,rw /
CONTROL-D will exite from this shell ans reboot the system.
bash: lesspipe: command not found
bash: dircolors: command not found


Many thanks.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

