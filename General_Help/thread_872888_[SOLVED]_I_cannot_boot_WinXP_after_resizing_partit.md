---
title: "[SOLVED] I cannot boot WinXP after resizing partition with gparted"
date: 2008-07-28
forum: General Help
---

### Post by rEbyTer on 2008-07-28
I have an EeePC and I have installed WinXP on SD, ArchLinux on SSD and Ubuntu on external HDD.

The instalation of winxp to sd was pretty 'bloated' so I need to install first to SSD and then **dd** the whole SSD to SD. The SSD has 4GB and SD has 8GB, so when I **dd** the SSD to SD I have only 4GB on SD, so i've resized it with gparted and now i'm not able to boot.

What can I do ? Thanks in advice

---

### Post by kerry_s on 2008-07-28
i don't think you can just move windows like that.
your post is a little confusing, so questions:
did it boot before you resized?
if it did, did you defrag before you resized?
what does it do now, if anything?

i'm still on my first cup of coffee so i'm still slow. :)

---

### Post by eriqjaffe on 2008-07-28
> **kerry_s said:**
> i don't think you can just move windows like that.Correct, you'll need to edit the c:\boot.ini file to point to the correct drive.  Mind you, it's a hidden system file, so you'll need to unhide and unprotect it first.  You should be able to do all that from the XP recovery console (which you can get to from the XP install CD).

---

### Post by rEbyTer on 2008-07-28
* before resizing everything was OK.

> i don't think you can just move windows like that.
Yes indeed, but with a little hacking is possible. (Take a look [here](http://www.3eportal.com/index.php?option=com_content&task=view&id=16&Itemid=1))

> did it boot before you resized?
No!

> if it did, did you defrag before you resized?
No!

> what does it do now, if anything?
I can see the BIOS messages and when i choose to boot from SD i get a **_** that is blinking and it does nothing

* when I boot Ubuntu from my external HDD I can see what it is on SD

> Correct, you'll need to edit the c:\boot.ini file to point to the correct drive. Mind you, it's a hidden system file, so you'll need to unhide and unprotect it first. You should be able to do all that from the XP recovery console (which you can get to from the XP install CD).

I will try with XP install CD, but I have to unmount the HDD from rack, install the cd drive... etc :) **however I have also tried booting from SD with external HDD ubuntu grub.**
```
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
chainloader	+1
```
Where hd1,0 is my SD. **That didn,t work.**
Thank you again for helping me.

---

### Post by kerry_s on 2008-07-28
sounds like a botched install from the get go, i would try again, but this time make sure your partions already setup so you don't have to resize it, maybe install straight to sd instead of ssd then dd'ing it.

---

### Post by rEbyTer on 2008-07-28
In that tutorial I install on SSD, then I update the Internal CardReader drivers to a Hitachi Microdrive filter, so the card reader would be recognized as a non-removable device.Then I have to dd to SD. But It's ugly to have 4GB on a 8GB SD.

> # Go to Device manager. Under disk drives, you should see SiliconMotion and USB2.0 Card Reader. Right click on the card reader and click update driver. Direct the driver updater window to the Hitachi driver you just edited. It won&#8217;t detect the driver automatically, you have to specifty that your supplying the disk for the hardware and force it to use the driver.
# Reboot using the Partedmagic CD or USB Flashdrive, Download it here
# Create a FAT32 partition on the SD card, same size as the one on the SSD in your 3epc
# Use 'fdisk -l' to find out the partition names of your SSD and SD.
# Type this command into a prompt: 'dd  if=/dev/sda1 of=/dev/sdb1'  When it finishes (it will take some time) type this command: 'dd if=/dev/sda of=/dev/sdb bs=512 count=1' (Note: If fdisk reported your SSD and SD as different than sda and sdb respectively, you must change that in the dd commands, if unsure ask in the support forums)
# When it finishes the task is complete, reboot and select to boot from the card reader
# Re-image the SSD of your 3epc with your restore DVD or USB. 

What does the *dd if=/dev/sda of=/dev/sdb bs=512 count=1* command ?

---

### Post by rEbyTer on 2008-07-28
SOLVED.

I have used fixmbr from Recovery Console and everything works fine now. Thank all of you for helping me.

---

