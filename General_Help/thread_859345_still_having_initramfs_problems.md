---
title: "still having initramfs problems"
date: 2008-07-14
forum: General Help
---

### Post by pat351 on 2008-07-14
I have looked through every thread and done everything I can to get past this initramfs problem at the startup of wubi ubuntu. There are some people that give really confusing instructions and I am still a major newb at any sort of linux software (i just tried to figure it all out yesterday). Can someone please step me through a process that will allow me to get past the initramfs screen at startup? Thanks.

Screen:
Busybox v1.1.3 (Debian...Built in shell (ash)
type help for available commands

(initramfs)

---

### Post by ago on 2008-07-14
What is the output of

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions

---

### Post by plastichero on 2008-07-15
I also got the same thing and was astonished. The solution is simple: From windows, after running the WUBI installer, replce "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that is selected for Ubuntu installation, it may be different for you)

also, is your drive FAT32 formatted? make it NTFS.

---

### Post by pat351 on 2008-07-27
yeah its already in ntfs, and im going to try the change thing

---

### Post by pat351 on 2008-07-27
my menu.lst is not in disks but in install is that ok?

---

### Post by pat351 on 2008-07-27
ok so changing the code didnt work, and ago, im kind of confused about what your asking me? are those commands i type after initramfs on the weird start screen?

---

### Post by pat351 on 2008-07-27
oh and my fat32 is already in ntfs

---

### Post by ago on 2008-07-29
yes those are commands you type at the busybox prompt, then post here the output

---

### Post by pat351 on 2008-07-30
ok ago, there was a lot as you probably were expecting:

for cat /proc/cmdline:
debian-installer/custom -installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktopi386.iso automatic-ubiquity noprompt all_generic_ide boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode=--

for cat /proc/mounts:
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0

for cat /proc/partitions:
major  minor    #blocks   name
    8      0   117220824   sda
    8      1   229697338   sda1
    8      2           1   sda2
    8     16   117220824   sdab

thanks a lot ago, for all your help

---

### Post by pat351 on 2008-07-30
i hope you can understand the partitions output, the post kind of messed it up, every space is in the new category

---

### Post by pat351 on 2008-07-30
also should i put the all_generic_ide's back to quiet splash in the program?

---

### Post by ago on 2008-07-31
can you also provide the output of 

grep err /casper.log
grep mount /casper.log

---

### Post by pat351 on 2008-07-31
ok so for grep err /casper.log:

stdin: I/0 error (says this 6 times)
Could not find the ISO /ubuntu/install/ubuntu-8.04.1-desktop-i386.iso. This could happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows. After this you should be able to reboot again and resume the installation.

for grep mount /casper.log:

Begin: Running /scripts/casper-premount ...
/scripts/casper-premount/20iso_scan: /scripts/casper-premount/20iso_scan: 45: cannot open /dev/scd0: No medium found (it just says this part three times)
(Then it just repeats the 'Could not find ISO' speech from the first one)

---

### Post by jualin on 2008-07-31
> **pat351 said:**
> also should i put the all_generic_ide's back to quiet splash in the program?

Have you tried adding **all_generic_ide** to your boot line? Remember that you needed to erase the Quiet Splash part of it. My friend was having this problem yesterday and adding that to the boot line solved his problem. Hope this helps!

---

### Post by ago on 2008-07-31
First: is it a raid array?

From the previous post the only available partition is sda1 which means partition 1 on hd 1. If you installed on a different partition then that is the issue. If you installed on sda1 then looks like it is not possible to mount the partition where you installed ubuntu which, as suggested, might be because the fs is corrupted.

---

### Post by Orlsend on 2008-07-31
So theres no Solution, I have the Same problem.

NTFS and no "file g:\ubuntu\disks\boot\grub\menu.lst"

---

### Post by pat351 on 2008-07-31
ago, im not going to lie you kind of lost me there. I'm not familiar with raid array and which partition I installed it on, how do I check? Isn't wubi supposed to do this? I thought that it partitioned it for you. Should I try a reinstall?

so many questions

---

### Post by Orlsend on 2008-08-01
Yeah, I dont think anyone hare is able to answer them...

---

### Post by cypherstream on 2008-08-01
I would be interested if this problem gets solved.  Now I'm at the same point....  My thread is here:
[http://ubuntuforums.org/showthread.php?t=875570](http://ubuntuforums.org/showthread.php?t=875570)

I think in my situation is that it's looking for the install on the wrong partition, but I can't simply move the ubuntu folder because the other partition is way too small.

---

### Post by Orlsend on 2008-08-01
I Tried reinstall, that dint work. I did a correct shut down and Restart,No work Either

Whe checked for Errors with the "Chkdsk /r" that say we were perfectly fine.

---

### Post by thawkins1 on 2008-08-01
I have the same problem. I've tried reinstall still goes to busybox screen after I restart.

---

### Post by Orlsend on 2008-08-01
Welcome to the Club, but...

[IMG]http://ihasahotdog.files.wordpress.com/2008/07/funny-dog-pictures-dog-waits-in-line-for-food.jpg[/IMG]

We hope some one will help us.

---

### Post by thawkins1 on 2008-08-01
> **Orlsend said:**
> Welcome to the Club, but...

[IMG]http://ihasahotdog.files.wordpress.com/2008/07/funny-dog-pictures-dog-waits-in-line-for-food.jpg[/IMG]

We hope some one will help us.
LOL. But I was gonna come back and reply that this problem was solved when I did a normal shutdown.

---

### Post by cptruong on 2008-08-01
I have similar problem.
Busybox v1.1.3 (Debian...Built in shell (ash)
type help for available commands

(initramfs)
my specs :
core 2 E4400.
Gigabyte 945P-DS3
2GB ram.
7300GT.

---

### Post by ago on 2008-08-01
Make sure you are not on a RAID 0-1 (multiple hard disks). Make sure you are not using the Alternate or DVD ISO. Make sure your HD is not encrypted. Sometimes external disks create issues.

Check that the windows partition is not corrupted by running chkdsk /r in windows

Check that any file is available in windows in particular you must have one of these 2 files (but not both): c:\ubuntu\install\boot\grub\menu.lst OR c:\ubuntu\disks\boot\grub\menu.lst

Note that sometimes for booting (first time after windows) special boot parameters are required such as all_generic_ide or irqpoll or acpi=off.

If you still have issues press ESC at boot and go for either rescue mode or verbose mode (you might try the other options as well). 

See if there is any error message.

Then type the following commands and post the input here:

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions
grep err /casper.log
grep mount /casper.log

---

### Post by Orlsend on 2008-08-01
Does HD encryption matters? I think my Dad's is PGP encrypeted... Well we still have to try the "ESC" option in booting...

---

### Post by jualin on 2008-08-01
Has anyone tried [this suggestion?]("http://ubuntuforums.org/showthread.php?t=777927&page=3"). That worked with everyone that I know was having the Wubi busybox problems, maybe it will not work for all of you guys but at least is better than nothing. Good Luck!

---

### Post by ago on 2008-08-01
> **Orlsend said:**
> Does HD encryption matters? I think my Dad's is PGP encrypeted... Well we still have to try the "ESC" option in booting...

Encrypted HD are not supported unfortunately

---

### Post by pat351 on 2008-08-01
i actually do have multiple hard disks. What exactly do I do to fix the problem? Am i not going to be able to use wubi because of it?

---

### Post by ago on 2008-08-01
> **pat351 said:**
> i actually do have multiple hard disks. What exactly do I do to fix the problem? Am i not going to be able to use wubi because of it?

Depends, if your hard disks are set up in a SOFTWARE RAID 0 or 1 (this is when 2 hard disks appear as a single hard disk to the computer) then you will have to wait for 8.10 (alphas will be available in days), otherwise yes, wubi should work.

---

### Post by cptruong on 2008-08-01
i don't use raid, i have 1 HDD.

---

### Post by pat351 on 2008-08-02
oh i see. my hard drives are read as the same. that really sucks. if i got ubuntu, would i have the same problem?

---

