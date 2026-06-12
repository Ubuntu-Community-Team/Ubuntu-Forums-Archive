---
title: "GRUB error 17 - please help me!!"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Newbie0001 on 2009-08-05
i installed Ubuntu 9.04 the other day side by side with Windows XP. It made its own partition for itself, but that was only 2.33GB, so i resized it and then it said it needed to restart, so i rebooted, then it loaded and made the changes i had asked, then it rebooted again, and then a black screen came up saying:

GRUB loading stage 1.5


GRUB loading, please wait...
GRUB error 17


it hasn't changed from that screen for about a week! can someone please give me some advice on how to fix this problem??

---

### Post by philcamlin on 2009-08-05
I have had this error 17 many times from having bad power downs and crashes for other reasons. In most of my cases the problem is usually from a bad magic number in the root partition. This can be easily fixed by doing this:
 
to fix error 17 in grub at boot time don't forget to try:

a. boot from any live CD (ubuntu install disk works for me)
b. open accessories->Terminal
c. in terminal type "sudo e2fsck -b 32768 /dev/hdaX

replace the hdaX in line above with the disk that you have your root mounted from
for example

sudo e2fsck -b 32768 /dev/hda2

in my case I have windows installed in /dev/hda1 and my root partition for ubuntu in at /dev/hda2
also if -b 32768 fails you can try other numbers including -b 8193 or -b 98304 or -b 163840....

---

### Post by merlinus on 2009-08-05
Another possibility is that the UUID for linux / changed due to resizing its partition.

```
sudo fdisk -l
sudo blkid
```should give you the correct one, which you will have to compare with the one in /boot/grub/menu.lst.

You can access this file by running from the live cd, then Places/Computer/media/disk/boot/grub/menu.lst, rightclick and open with text editor.

If changes are needed

```
gksudo gedit /media/disk/boot/grub/menu.lst
```

---

### Post by merlinus on 2009-08-05
Then remove cd and restart.

---

### Post by Newbie0001 on 2009-08-05
oh, i forgot to mention, it wont read any disk... even the Ubuntu loading disk

---

### Post by philcamlin on 2009-08-05
press f12 at the bios and select boot from cd

---

### Post by Newbie0001 on 2009-08-05
it didnt work

---

### Post by Newbie0001 on 2009-08-05
any more suggestions?

---

### Post by computerkid2000 on 2009-08-05
> **Newbie0001 said:**
> any more suggestions?
well nothing else to say but you are evidently screwed! back up all data and reinstall all OSes!

---

### Post by Newbie0001 on 2009-08-05
i dont think i can back up data :(

---

### Post by Newbie0001 on 2009-08-05
fixed it!

what had happened was that in BIOS setup, the boot priorities had messed up and a virtual floppy disk drive apparently had to be in the first boot device, then the CD drive, then the HDD. i moved them all to that position, then put the Ubuntu disk into the CD drive, rebooted, and it booted off the disk! i then reinstalled Ubuntu on the comp. and it fixed the GRUB issue, and it working good now. thanks a lot for the advice guys!

---

### Post by alexhore on 2009-08-05
When you say it dint work did it read the disk when pressing f12 if not check disk on another pc or try another bootable disk to see if its the disk.
 
If nothing is booting from the diskdrive on f12 your dvd/cd drive is dead or might have a loose connection?

---

