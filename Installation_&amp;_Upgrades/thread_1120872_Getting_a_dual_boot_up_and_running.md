---
title: "Getting a dual boot up and running"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by mjbrisbois on 2009-04-09
I'm trying to give Ubuntu a test run, but can't seem to get it installed and running. I'm setting up a dual boot with Windows XP. I get the intitial screen choice with the GRUB loader (is this the correct term) and following selecting Ubuntu 10.2, I get the Ubuntu loading screen (like I did in Wubi), everything so far appears good. Then I get this: 

Boot from (hd0,4) ext 3 267d1852-c169-412c-95ac-6330a0062973
Starting up...
[   0.004000] Aperture beyond 4 GB. Ignoring
Loading, please wait...
Gave up waiting for root device. Common Problems:
   --Boot args (cat /proc/endline)
     --Check rootdelay=(did the system wait long enough?)
     --Check root=(did the system wait for the right device?)
   --Missing modules (cat/proc/modules; ls/dev)
Alert /dev/disck/by uuid/{same number as above following "ext 3"} does not exist. Dropping to a shell!!

Busy Box v.1.10.2 (Ubuntu 1:1.10.2--1ubunu6) built in shell (ash)

and then the command line. Do I still need to run with a live CD in the drive? Other help? I'm quite new to all this...

---

### Post by lightpriest on 2009-04-09
The boot loader tries to load the kernel with a root parameter that is incorrect.

If you're familiar with the boot line editing of GRUB (type 'e' on the boot selection screen) than edit ('e' again) the kernel command line and change the root parameter to say: '/dev/sda5'. (I'm guessing this from the first line of GRUB's output (hd0,4)).
After you've finished editing type 'b' to boot.

If you're not or if it fails, load with the live CD, open a terminal and run blkid. It will list all the UUID values for the different partitions/mounts. Edit the /boot/grub/menu.lst file of your installed Ubuntu (not the one that loaded from the live CD, the one you installed on /dev/sda5).
Look for the line that starts with "kernel" and change its root parameter to have the UUID of /dev/sda5.

Now try rebooting, come back with results :)

---

### Post by mjbrisbois on 2009-04-09
Just to make sure, you mean to kernel   /boot/{...}/generic root=UUID {code numbers here] to be {...}generic root=/dev/sda5, correct? I'm inexperienced with coding, so want to make sure I understand before I change things.

---

### Post by lightpriest on 2009-04-09
Yeah, that's what I mean. Basically UUID and /dev/sdX are the same if they correspond, but UUID is safer to use (partition changes, new HDs, etc.)

As I can't really tell you which of /dev/sdX to type there, you have to know it youself. Again, I guessed it from the first line of the output you wrote here.
If you want to be 110% sure, you could load from a Live CD, access the partition through the Places menu (this would mount it automatically) and then use System ->  Administration -> Partition Editor to see which /dev/sdX is mounted. There are other ways but I find this one's easiest if you want GUI :) (Use partition editor for viewing only if you're unsure about it)

Another thing, nothing harmful should happend if you mistype /dev/sdX in the root parameter (except the system won't boot) - but to be on the safe side get it right the first time :)

One more thing, I'm not really sure of it but if the kernel couldn't find the UUID then / (root) won't mount too. The mount for / (the root path) is written in /etc/fstab and it probably also uses the UUID. It's ok to change it to /dev/sdX if they are the same.

After this works you can change it back to the correct UUID, you can see it with the `blkid` command.

---

### Post by mjbrisbois on 2009-04-09
Thanks. I'll give it a try later; after dinner, that is.

---

### Post by mjbrisbois on 2009-04-10
Unfortunately it didn't work. I'm thinking about removing the Ubuntu and reinstalling it, but can't work out how to go about removing it. I'm running XP on it, if that helps.

---

### Post by mjbrisbois on 2009-04-11
Okay, I'm now going with a single boot o fUbuntu up, but keep getting the identical error. Runs off live CD fine. Integrity of disc checks fine.

---

### Post by mjbrisbois on 2009-04-11
Here's what a sudo blkid gave me:

/dev/sda1:UUIC "27686888-5262-4911-b1cc-8ce662444c10" Sec_Type="ext2" Type="ext3"
/dev/sda5:UUID="e1233681-13e7-445a-9bfe-74039a3cd424" Type="swap"
/dev/loop0: Type-"squashf"

The UUID that appears in my kernel is the /dev/sda1

Please if you can, provide example codes as I'm very green.

---

### Post by mjbrisbois on 2009-04-11
And what about using the Alternate Install CD. It has a "rescue a broken system" option I believe.

---

### Post by lightpriest on 2009-04-14
Load from a Live CD.
Use the "Places" menu to get to the /dev/sda1 partition (you can recognize it by size).
And print here the contents of /boot/grub/grub.conf

---

