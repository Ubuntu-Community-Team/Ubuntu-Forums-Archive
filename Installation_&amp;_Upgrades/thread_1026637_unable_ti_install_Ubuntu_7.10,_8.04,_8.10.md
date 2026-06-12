---
title: "unable ti install Ubuntu 7.10, 8.04, 8.10"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by blazzz on 2008-12-31
hi!
I would be grateful if someone could help me...

The same problem happens with all 3 of Ubuntu versions:

Booting from cd - I get the start screen with Ubuntu logo and installation menu. After choosing install or check cd all i get is the black screen with flashing cursor in the upper left corner of my screen. 
Then I found on this forum a tip to try to replace "quiet splash--" with "noapic nolapic" or "irqpool" or some other option to fix bios problems, but it did not help. All i got was some 30 or 40 lines of booting text, like memory test or allocation, and at the end same old flashing cursor.

Installation in Windows with ver. 8.04 & 8.10 - Windows installation screen would start the creating of image, and would get all the way to 99%, and then the error massage would appear: Could not access CD, please make sure other applications are not using it and try again. 

Don`t know what else to say... 
My PC configuration is:
-intel pentium dual core e5200 2.5ghz
-dfi mbo s.775 lan party ut
-vga pci-e bfg 9600 gt
-ddr2 pc-6400, 800mhz 2gb x 2
-maxtor 6g160p0
-logitech mouse;)

thx for help

total noob

---

### Post by dstew on 2008-12-31
Do you know for sure that the CD is good? Did you make the CD yourself, or get it throught the mail? Try booting it in another computer to see if it works.

---

### Post by blazzz on 2008-12-31
i got the iso image on DVD of one IT magazine, and made a iso CD of ver. 8.04 and 8.10. I got ver. 7.10 from my friend, but he is pretty sure that it is working. 
I`ve made copies using nero 6 and option burn image... 
anyways i can`t check my disks on other computer at this time, and I also think that the problem is in my computer, but i just don`t know where or what... maybe my logitech mouse???

---

### Post by dstew on 2008-12-31
Did you burn the disks yourself? What speed did you burn?

---

### Post by blazzz on 2008-12-31
Yes, i burned 8.04 & 8.10 CD`s all by myself;) the speed was 3600 kbs. 
But my friends 7.10 is working on his PC...

---

### Post by dstew on 2009-01-02
I am familiar with burn speeds like 4x or 16x, so I am not sure how fast 3600kbs is. Anyway, if you burn an image too fast, it will often have errors in it. Usually I burn an image as slow as possible, no more than 4x in my machine.

It is different burning music CD's or movie DVD's. Those file formats can tolerate lots of single-bit errors that you would never notice listening or watching the media. But OS image files may fail if even a single bit is wrong. That's why you need to burn at the slowest speed.

---

### Post by blazzz on 2009-01-02
will try, tnx...
i`ll report back

---

### Post by Sef on 2009-01-02
At the Live CD main menu, go down to 'Check Disk for Errors' (instead of installing or running the Live CD.)

---

### Post by blazzz on 2009-01-03
i have tried that, but nothing, black screen and flashing cursor...

---

### Post by Pumalite on 2009-01-03
Try vga=788; vga=789; vga=791; vga=0x317 in your boot line.

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

