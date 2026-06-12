---
title: "Undo Grub loader"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by pheonixdragon on 2009-03-22
Hi,

My apology if someone may have asked this before. I am new here and haven't had the opportunity to browse through the whole website to find the answer.

I installed Ubuntu on existing Vista laptop. How do I restore to the original state before I installed Ubuntu?

I tried deleting the partition where Ubuntu was installed then I couldn't boot Vista.

---

### Post by mhgsys on 2009-03-22
Basically this actually is a windows question.

anyway:
read this and you'll get back your vista
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

note: You'll be done by the /FixMbr and /FixBoot commando

---

### Post by pheonixdragon on 2009-03-22
> **mhgsys said:**
> Basically this actually is a windows question.

anyway:
read this and you'll get back your vista
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

note: You'll be done by the /FixMbr and /FixBoot commando

Thanks.

I found another solution with Knoppix

fdisk /mbr 

will overwrite grub bootloader with Microsoft bootloader. 

Warning: This will remove Ubuntu or any Linux and has to be reinstalled.:KS

---

### Post by hexanol on 2009-03-22
> Warning: This will remove Ubuntu or any Linux and has to be reinstalled

Well, I guess the command you gave won't actually modify any partition, so all your "Ubuntu stuff" would still be there and you would just have to reinstall grub and you would be up again!

---

### Post by pheonixdragon on 2009-03-22
> **hexanol said:**
> Well, I guess the command you gave won't actually modify any partition, so all your "Ubuntu stuff" would still be there and you would just have to reinstall grub and you would be up again!

How do you reinstall grub without reinstalling a complete Ubuntu?

---

### Post by hexanol on 2009-03-22
There's more than a way to do it, but how I do it normally is from a grub floppy/usb stick (you have to create the floppy/usb stick before, but that's simple, takes only two commands). Then, you boot from the floppy/usb stick and you will have a grub prompt, and you enter simple command like "root (hdX,Y)" and "setup (hdX)".

Here's a link on how to create a grub boot floppy. The procedure is the same for a usb stick but you replace /dev/fd0 for /dev/sdb or whatever it is on your system. [http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy](http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy)

:)

---

