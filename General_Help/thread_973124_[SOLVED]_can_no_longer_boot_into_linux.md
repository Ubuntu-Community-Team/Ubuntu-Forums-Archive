---
title: "[SOLVED] can no longer boot into linux"
date: 2008-11-06
forum: General Help
---

### Post by Priddeh on 2008-11-06
hey guys, today I installed Win XP Pro on a unused partition of my HDD. Problem is it has seemed to of gotten rid of GRUB loader (i think that's what its called) and now it will only boot into XP. Any ideas how I can add it back onto the boot menu? Files I need for Uni are on there so any help would be great.

Thanks

Edit: Also if there's a way to get onto the partition where my Linux files are from XP that would great if someone can tell me how to.

---

### Post by bscbrit on 2008-11-06
Follow the step to recover grub bootloader:
1. Boot with Ubuntu Live CD
2. Open gnome-terminal
Give the commands:
3. sudo grub
then it shows grub> like this
grub>find /boot/grub/stage1
it&#8217;ll give a output like this (hd0,7)  7 is here for example, it will be number of your partition.
grub>root (hd0,7)
grub>setup (hd0)
grub>quit

reboot back to your hard drive

---

### Post by Priddeh on 2008-11-06
Okay, will try that as soon as I've downloaded Ubuntu again. Thanks for the quick reply :).

---

### Post by bscbrit on 2008-11-07
Priddeh, have you managed to solve your problem?

---

### Post by Priddeh on 2008-11-07
Sadly not. When I try to boot from live CD I get "I/0 error - Error reading boot CD" it might just be a bad disc so I'll try re-burning it.

Edit: I've re-burnt it, still getting the error - disk works fine on other computers.

---

### Post by Priddeh on 2008-11-07
I found that on one of my systems, when I enter the CD's I get another error "Invalid CD detected" and doesn't open. I'll start downloading it again in case it got corrupted.

---

### Post by bscbrit on 2008-11-07
Confirm, please, that you are using a LiveCD, and not the Alternate CD? And that you are burning the image as an ISO an not data?

---

### Post by Priddeh on 2008-11-07
After re-downloading Ubuntu and burnt it to a disc it now works (first one I downloaded must of been corrupted).

Just followed your steps and its worked :D thanks a lot!

Just one more quick question, is there away now I add Windows XP to the GRUB menu?

---

### Post by bscbrit on 2008-11-08
Usually, because of the way that Windows ignores every other OS, it is installed at the start of the first hard drive (which Microsoft calls 'C:').

My /boot/grub/menu.lst is shown below. At the end you can see the reference to Other Operating Systems and below that the lines which produce the menu entry to allow the computer to be to booted into Windows.  The hard drive reference points to (hd0,0) which is the first partition of the first hard drive.  There is a comment showing that, on my computer, it is /dev/sda1.  Assuming that your Windows installation is standard, then if you copy the code onto the end of the menu.lst file it should work.  

When the Grub menu displays you should see a new menu entry.  If you do not usually see the menu, press the Esc key when you see the countdown during the early boot process immediately after the BIOS has completed its checks.

Always take care when editing this menu because if it becomes corrupted it can prevent the computer from booting - although this can be repaired using a LiveDisk.  Make a backup (copy it to something like menu.lst.original) before you start editing the file.

Look at 'man grub' or Google for 'linux grub' for more information.  Or search the forum archives for dual boot and you will find lots of good advice.


```


{Lots of comment before we get to this part....}

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3c66eb0c-2324-4db9-aabc-02ff8db8e87a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3c66eb0c-2324-4db9-aabc-02ff8db8e87a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by Priddeh on 2008-11-08
Thanks a lot, I've added XP on the menu and it boots fine :).

Thanks for all your help! :D

---

### Post by bscbrit on 2008-11-08
Great news.  See you around the forums - and thank you for the "thank you"!

---

