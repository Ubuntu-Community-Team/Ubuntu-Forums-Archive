---
title: "boot from usb in a non copatiable pc"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by izar on 2009-02-20
I have an old laptop with a broken cd which can’t boot from diskonkey.
I am looking for a program which will allow me to boot any bootable usb drive.
(I looked on pen drive linux site. I found only methods for booting a specific linux distribution. Isn’t there a way to simply load some drivers and then boot the MBR of my diskonkey?)
Thanx for your help
***
[SIZE="1"]Technical information:
Compaq laptop
Pentium or Celeron processor with 300Mhz
~50 mb ram
OS: fluxbuntu (ubuntu with fluxbox)
Grub bootloader
Harddisk: 4Gb with two partitons.
1.44 diskett drive[/SIZE]

---

### Post by CapnGimp on 2009-02-20
No.

 It takes an OPERATING SYSTEM to run a computer.

  If your computer bios does NOT allow/offer boot from a USB device, the only way would be to use a bootable cd to enable the flash drive to 'boot'.
 You stated your cd drive is non-functional, so you would have to make a bootable floppy.
  get it here with a tutorial.
[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

Pick a linux version and install it on the flash drive.
 I used SLAX and added modules of stuff I needed and it works great.
 I have it on a 1GB mp3 player, lol. Makes for a great tool to carry  and fix windows machines, introduce folks to linux. Different from a cd/dvd.

 Let us know how it went and mark the thread as SOLVED.

---

### Post by cariboo on 2009-02-20
If you have a floppy drive, you can use ti to load the drivers needed to boot your USB device.

Jim

---

### Post by izar on 2009-02-21
> **CapnGimp said:**
> No.
[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)


thanks.
i've seen this page, though i understood this floppy will only let me boot pendrivelinux. (i am looking for something that will let me boot anything)
i was planing on trying this, yet the laptop's charger has a problem which will take me some time too solve so i'll try it once it is fixed.

in any case, is there a way to copy the floppy and boot it from the hard drive?

> **cariboo907 said:**
> If you have a floppy drive, you can use ti to load the drivers needed to boot your USB device.
Jim
and how exactly do i do that?

[SIZE="3"][COLOR="Red"]P.S. i appreciate your help though i must note that this task is not urgent and i would probably find a way around it in any case (though it might be the hardist and longest)[/COLOR][/SIZE]

---

### Post by cariboo on 2009-02-21
Have a look at these instructions at [Bootdisk.com]("http://www.bootdisk.com/usb.htm").

Jim

---

### Post by izar on 2009-02-22
i'll try this when i get my charger fixed.
thanks

---

### Post by izar on 2009-03-01
i tried the floppy from pendrivelinux. it is simply a grub floppy with a menu.lst for booting PDL. as far as i understand it doesn't have any usb drivers. in any case it didn't work for me.

jim, the information at bootdisk.com is for dos users, and my pc currently runs only grub and fluxbuntu. in any case i will try using a dos floppy and see if it works.

---

### Post by izar on 2009-03-12
i used the instructions from bootdisk.com and got access from dos too my usb.

now i wanted to boot from the usb so i figured i can use grub4dos to do that. yet in grub i can't reach the usb pen drive.
(typing "root (" and tab show me hd0, fd0 and rd which is the ramdrive.)

---

