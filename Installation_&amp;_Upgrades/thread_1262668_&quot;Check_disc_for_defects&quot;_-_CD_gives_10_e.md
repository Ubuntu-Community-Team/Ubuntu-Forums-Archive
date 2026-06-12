---
title: "&quot;Check disc for defects&quot; - CD gives 10 errors on one laptop but no errors on another!"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by jhodgski on 2009-09-10
[FONT=Comic Sans MS][SIZE=2]Hiya,

I've tried burning Ubuntu many times, but the "Check disc for defects" utility always reports 9, 10 or 11 errors. So I bought a high-spec CD from ebay, and again it reported 10 errors. ([/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2][COLOR=#000000][FONT=arial]And selecting the "Try Ubuntu without any change to your computer" results in a list of error messages followed by a "ubuntu@ubuntu:~$" prompt.[/FONT][/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2])

Decided to try the CD in a friend's laptop - this time, no errors! (And [/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2][COLOR=#000000][FONT=arial]the "Try Ubuntu without any change to your computer" seems to work fine.)

Does anyone know what the problem could be? Should I try an older version of Ubuntu? If so, which one?

Many thanks,
James

PS - If it helps... both laptops in question were running Windows XP. The problematic one is a Toshiba and seems to have a corrupt harddrive (which is why I'm using Ubuntu to try and get my work files off it...)
[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by ottosykora on 2009-09-10
well, one of our office laptops is able to read only disks which it did burn itself, other reads only certain brands of disks and so on. I think all that is quite common.

---

### Post by phillw on 2009-09-10
I'd suggest that you get a cd/dvd drive cleaner and clean the cd drive on the poorly computer.

The only other one that bites people on the bum is that you really must burn the cd at the slowest speed possible (like 4X) - not doing this causes all sorts of 'funnies'

Phill.

---

### Post by jhodgski on 2009-09-11
Thanks for the replies.

I cleaned the CD drive, but I still get a load of errors reported - sometimes 9, sometimes 10, 11 or 12 errors (same CD).

The CDs I've tried were burnt at 4x max.

OK, the problem is probably with my CD drive. So I decided to copy the files from the CD (which work fine on a different computer) onto a USB memory stick and then (from the boot menu) to boot from that on the poorly computer. But the computer doesn't seem to notice the USB memory stick and just tries to start Windows again...

Any ideas how I can get the computer to notice the Ubuntu USB memory stick?

---

### Post by raymondh on 2009-09-11
> **jhodgski said:**
> Thanks for the replies.

I cleaned the CD drive, but I still get a load of errors reported - sometimes 9, sometimes 10, 11 or 12 errors (same CD).

The CDs I've tried were burnt at 4x max.

OK, the problem is probably with my CD drive. So I decided to copy the files from the CD (which work fine on a different computer) onto a USB memory stick and then (from the boot menu) to boot from that on the poorly computer. But the computer doesn't seem to notice the USB memory stick and just tries to start Windows again...

Any ideas how I can get the computer to notice the Ubuntu USB memory stick?

Are you able to alter BIOS to  boot from USB?

---

### Post by StuartN on 2009-09-11
> **jhodgski said:**
> So I decided to copy the files from the CD (which work fine on a different computer) onto a USB memory stick

You need to make a bootable Ubuntu USB stick like this [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) - you can't simply copy the CD files.

The difference between CD drives is normal. Some are highly fault-tolerant and others can't read any CDs except the ones they write. A CD/DVD lens cleaner (a CD disk with a little brush embedded in it) sometimes works. A new CD drive is very cheap.

Booting from USB is hardware dependent. You need to enter your system BIOS (e.g. by pressing F2 or Esc or a similar key during bootup, before GRUB) and choosing the boot order. Put USB first if it is an option - some hardware requires a USB drive to be plugged in for the option to be displayed. Some older hardware does not have a boot from USB option at all.

---

### Post by jhodgski on 2009-09-12
I made a bootable Ubuntu USB stick as described. I tried both methods (using System-->Administration-->Create a USB startup disk and by using UNetbootin to create it from an iso).

The USB Ubuntu stick I made worked from a different laptop, but not from the poorly computer. (It boots fine, but when I select "Try Ubuntu without any change to your computer" I eventually get reams and reams of error messages). So the Ubuntu problem with the poorly computer clearly isn't CD-related. Could it be a basic Ubuntu-software compatability problem?

I'm going to try it making a Ubuntu 8 USB (probably using UNetBootin) and see if that works...

In the meantime, any other suggestions would be welcomed!

---

### Post by jhodgski on 2009-09-12
Ubuntu 8.04 USB didn't work either - "errors found in 13 files"...

If no-one has any more ideas, can anyone recommend an alternative to Ubuntu?

---

### Post by raymondh on 2009-09-12
Try an Ubuntu [alternate install]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").  It is text based. If you would, try a CD method instead of a USB.  Also, download from a torrent and, prior to installing, do a [MD5]("https://help.ubuntu.com/community/HowToMD5SUM")

For alternatives, there is [crunchbanglinux]("http://crunchbanglinux.org/") and [others]("http://distrowatch.com/").

Good luck.

---

### Post by jhodgski on 2009-09-30
Turns out the problem was due to a bad memory stick in the PC...

Thanks to those who offered there help.

---

