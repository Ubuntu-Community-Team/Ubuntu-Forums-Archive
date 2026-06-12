---
title: "USB super grub won't boot any operating system!"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by chufflar on 2009-11-09
I'm a bit of a newbie to super grub and ubuntu but I believe I have followed the install wiki correctly but have had problems.

I decided to install super grub as the normal grub with the ubuntu install gave me error message 22 and no evidence of ubuntu at all.

I cannot get either of my operating systems to boot windows which is installed on my laptops hard disk and ubuntu which is installed on an external usb disk.

when i try and boot through my usb drive grub starts then it enters usb shift and i get an error which says:-

filesystem type unknown, partition type 0x7
configfile (hd2,0)/boot/sgd/sgd.lst
error 17: cannot mount selected partition

when I try and boot straight to windows I get grub error 22.
  
I have tried removing grub all together with an xp install disk using fixmbr then fixboot. this didn't work.

Any help would be much appreciated.

Thanks in advance

---

### Post by darkod on 2009-11-09
How about this:
[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

You would have to add entry in grub2 for windows but it is enough if you make ubuntu work, you can add the windows entry in grub2 from inside ubuntu, easier.

---

### Post by chufflar on 2009-11-09
The only problem is I'm currently running my laptop off a ubuntu live cd so my disk drive is full. Is there any way I can do the same thing off a usb pendrive or through terminal?

---

### Post by darkod on 2009-11-09
Not sure, you better follow the commands in the article.

Write them down, yeah, we don't use paper these days. :) Open the website, write them down, then restart with the live cd and follow them.

---

### Post by chufflar on 2009-11-09
Cheers I'm following now! I'll post results!

---

### Post by chufflar on 2009-11-09
[FONT=Arial]I got to step 8.) and entered [/FONT][B][FONT=Arial]grub-mkconfig -o /boot/grub/grub.cfg at which[/FONT] point I got the error:-

bash: grub-mkconfig: command not found

any idea why this might happen?

sorry for bold I can't seem to remove it!
[/B]

---

### Post by chufflar on 2009-11-09
I completed the install from your link.

I now get grub loading 1.5....
error 22 when I load from my laptop hard drive

and when I load from my external hard drive I get

error disk failed
press any key to restart...

---

