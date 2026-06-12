---
title: "Newbie - problem with Wubi"
date: 2008-10-25
forum: General Help
---

### Post by SteveKnn on 2008-10-25
HI, I am trying to load Ubuntu Hardy Heron.  I got the distro Live Cd with the bookUbuntu for Non-Geeks (3rd Ed)

Ubuntu seems to work fine as a live Cd

I loaded it in Windows and on the reboot got the following:

[INDENT][B]-----
BusyBox v.1.1.3 (Debian 1.1.3-5ubuntu12) Built-in Shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)[/B][/INDENT]
------
What do I need to do?
Thanks for help, Steve

---

### Post by jmszr on 2008-10-26
This has worked for me. I don't know if it will work for you,but it's certainly worth a try:

This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solution: 1) Boot into Windows, Go to "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using Ubuntu now.

---

### Post by ago on 2008-10-26
Please post the output of:

cat /proc/cmdline
cat /proc/partitions
cat /proc/mounts
grep err /casper.log
grep mount /casper.log

PS use of wubi 8.10 is recommended now

---

### Post by SteveKnn on 2008-10-26
Try The Following Solution: 1) Boot into Windows, Go to "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using Ubuntu now.[/QUOTE]

**jmszr:  Thanks for the try.  I tried your suggestion to no avail.  Same problem continues.  Now to ago's suggestions, though I have to think about how to do that, since Linux is not working.  I will (1) try to get the infor from within windows, and if not then (2) perform a LiveCD boot.  I am afraid the latter will overwrite the info we are looking for.**

---

### Post by SteveKnn on 2008-10-26
I suspect that there is an easy way to post the output of the commands you requested in the state I am in (i.e. at the initramfs propmpt) **** Any hints?****

Here are some of the shorter responses:

cat /proc/partitions

[B]major   minor   #blocks   name
  8       0      488386584   sda
  8       1       48163      sda1
  8       2      15728640    sda2
  8       3      462367744   sda3[/B]

grep err /casper.log

[B]ntfs.attr-pread: ntfs:-pread failed: input/output error
Failed to read NTFS $bitmap:  Input/output error[/B]

grep mount /casper.log

**it and mount a different device unter the /dev/mapper/directory (e.g.) mlunt: mounting /dev/sda3 on /isodevice failed.success cannot mount mount /dev/sda3 on /isodevice**

Does this help? Do you need the rest?

---

### Post by ago on 2008-10-26
If Ubuntu is installed in sda3 (the 450GB partition) then it appears that it cannot be mounted. Could you post the error text again, but exactly?

grep err /casper.log -A 5 -B 5
grep mount /casper.log -A 5 -B 5

---

### Post by SaddaGocaraRupa on 2008-10-27
Same problem as the OP here. Did a wubi install of hardy.

System specs:
E8400, 4GB RAM, ATi HD4870, Gigabyte EP45-DS3 mobo, Asus Xonar DX audio, Pioneer SATA DVDR, 2x Samsung SATAII 500GB drives

> **ago said:**
> Please post the output of:

cat /proc/cmdline
root=UUID=D470C40770C3EDF4 loop=/ubuntu/disks/root.disk ro quiet splash
> 
cat /proc/partitions
major minor #blocks name
> cat /proc/mounts
roofs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /dev tmpfs rw, relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
> grep err /casper.log
grep: /casper.log: no such file or directory
> grep mount /casper.log
grep: /casper.log: no such file or directory


Thanks!

---

### Post by ago on 2008-10-27
@SaddaGocaraRupa

cat /proc/partitions 

does not show any partition, it means that your hard drive is not visible. Look for the make and model and see if you need any special module

---

### Post by SaddaGocaraRupa on 2008-10-27
> **ago said:**
> @SaddaGocaraRupa

cat /proc/partitions 

does not show any partition, it means that your hard drive is not visible. Look for the make and model and see if you need any special module

I actually fixed it by burning the .iso to CD and installing it like that. Thanks anyway though :)

---

### Post by SteveKnn on 2008-10-27
> **ago said:**
>  Could you post the error text again, but exactly?

grep err /casper.log -A 5 -B 5
grep mount /casper.log -A 5 -B 5

**When I am at the initramfs prompt, is there an easy way for me to get the error text into an email, other than trying to write it down and then type it in when I return to windows?**

---

### Post by ago on 2008-10-27
You have to manually mount the windows partition then you can redirect the output to a file in there, or copy files directly

es

mkdir /winpart
mount /dev/sda1 /winpart #assuming the windows partition is on sda1
cp casper.log > /winpart/casper.log

---

### Post by SteveKnn on 2008-10-27
OKay here we go:

[B]ntfs-attr-pread: ntfs-pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent , or you have a SoftRAID/FakeRAID hardware.  IN the first case run chkdsk /f on WIndows then reboot Windows TWICE.  The usage of the /f parameter is very important! IF ou have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1).  {lease see the "dmraid' documentation for the details.

mount: Mounting /dev/sta3 on /isodivice fialed: Success
Cannot mount /dev/sda3 on /isodevice[/B]

I did run the chkdsk /f and got a disk is clean message after a long run.  I rebooted windows twice as suggested.  NO CHANGE.  I do not have a SoftRAID/FakeRAID hardware. as far as i know.


**NOW WHAT?**

---

### Post by SteveKnn on 2008-10-28
ago,

Does the above sound like a software or hardware problem?

I have uninstalled and reinstalled form the same CD and got the same result.

Do you hae some other suggestions?
Should I be trying 8.04.1?
Should I be trying 8.10?
If I was to bypass the wubi approach of installing into windows, and went to a dual boot installation of ubuntu, would i find hte smae problems?

Thankls for your patience.
Steve

---

### Post by ago on 2008-10-28
Certainly try 8.10
You have a raid if you have 2 (or more) hard disks, which either look a single large hard disk to the OS or are in mirroring mode. If you only have 1 hd then you certainly have no raid.

---

### Post by SteveKnn on 2008-10-28
> **ago said:**
> Certainly try 8.10
You have a raid if you have 2 (or more) hard disks, which either look a single large hard disk to the OS or are in mirroring mode. If you only have 1 hd then you certainly have no raid.

Well, only one hard disk

I have loaded 8.10 and am having the same problems. 
   (note: I uninstalled 8.04, ran chkdsk /f and rebooted twice)

Still stops with the same type of error message:

**BusyBox v1.1..2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)**

When I run the Ubuntu boot in verbose mode, it travels much too fast to read it all, but I believe I saw DRDY ERR and Err NCC

Any hints now?

---

### Post by ago on 2008-10-28
to read the log:
more /casper.log

---

