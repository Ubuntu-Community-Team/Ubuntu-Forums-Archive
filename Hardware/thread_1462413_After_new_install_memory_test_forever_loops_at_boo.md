---
title: "After new install memory test forever loops at boot and grub does not appear"
date: 2010-04-25
forum: Hardware
---

### Post by j-dub305 on 2010-04-25
Hi all!

I have here a HP 6735s Business Desktop with Ubuntu 9.10 and for whatever reason after a brand new installation it will not boot the grub and goes DIRECTLY to Memtest86.  Pressing escape makes it reboot, only to return to Memtest86!!!  So basically, I have a computer that I can only access Memtest86 and not the OS!  The Live CD runs fine.  I am actually writing this while on the Live CD as of this moment.  But I can't get into the installed system no matter what I do.  All I get is Memtest86 and no Ubuntu.  Any ideas??  It would all be greatly appreciated!  Thanks!

---

### Post by oldyoda on 2010-04-26
> **j-dub305 said:**
> Hi all!

I have here a HP 6735s Business Desktop with Ubuntu 9.10 and for whatever reason after a brand new installation it will not boot the grub and goes DIRECTLY to Memtest86.  Pressing escape makes it reboot, only to return to Memtest86!!!  So basically, I have a computer that I can only access Memtest86 and not the OS!  The Live CD runs fine.  I am actually writing this while on the Live CD as of this moment.  But I can't get into the installed system no matter what I do.  All I get is Memtest86 and no Ubuntu.  Any ideas??  It would all be greatly appreciated!  Thanks!

I am having the same problem but i was deleting stuff when it hapened and it first whent to a black screen similar to command prompt and the shutdown control from there didnt work. I dont have a live CD or anything so there is nothing i can do at all! please help! the Memtest86+ v2.11 is really anoying.

---

### Post by P4man on 2010-04-26
did you accidentally delete your kernels perhaps?
Can you verify if the kernels are still present in

/media/yourharddisk/boot/

they should look like: vmlinuz-2.6.xx-xx-generic

If they are, I would try reinstalling grub from the livecd. Plenty of howto's for that, Here is one of many:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by oldyoda on 2010-04-26
> **P4man said:**
> did you accidentally delete your kernels perhaps?
Can you verify if the kernels are still present in

/media/yourharddisk/boot/

they should look like: vmlinuz-2.6.xx-xx-generic

If they are, I would try reinstalling grub from the livecd. Plenty of howto's for that, Here is one of many:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

I dont have a live CD and i cant get into the memory to cheack for such files i can only turn on the computer and then it goes directly to memtest86.

---

### Post by sleep furious idea on 2010-07-12
I am having the same problem as well.

Had a two partition set up (XP/Ubuntu) working swell until last night.  9.10 froze a couple times.  

Upon rebooting GRUB will only allow memory tests.  Apparently it passed. 

It cannot locate any OS.  This sucks.

Live CD works but I would like to burn some files on other CDs before throwing laptop off the balcony.

I reinstalled GRUB and the same problem persists.

   P4man said, "did you accidentally delete your kernels perhaps?"

   /media/yourharddisk/boot/

   they should look like: vmlinuz-2.6.xx-xx-generic

Perhaps but I can't check with the live CD...

---

### Post by sleep furious idea on 2010-07-12
> **sleep furious idea said:**
> I am having the same problem as well.

Had a two partition set up (XP/Ubuntu) working swell until last night.  9.10 froze a couple times.  

Upon rebooting GRUB will only allow memory tests.  Apparently it passed. 

It cannot locate any OS.  This sucks.

Live CD works but I would like to burn some files on other CDs before throwing laptop off the balcony.

I reinstalled GRUB and the same problem persists.

   P4man said, "did you accidentally delete your kernels perhaps?"

   /media/yourharddisk/boot/

   they should look like: vmlinuz-2.6.xx-xx-generic



Get this message in /media/

"The folder contents could not be displayed."

You do not have the permissions necessary to view the contents of "18D.........."

---

