---
title: "Boot from external Hard drive"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Jeanke on 2009-07-08
Hi,

I have a problem booting Ubuntu from an external hard drive.

Let me explain the situation and how I installed Ubuntu:

I have an Acer laptop with 2 internal hard drives of 160gb.

On the 1st I have 4 OS installed: 
1. Windows Vista 64bit(unfortunately need it still for some applications...)
2. Ubuntu 8.10 64bit (main Linux distro)
3 & 4 also Linux distro's, just for messing around.
I made a dedicated GRUB partition from where i can boot to one of those OS.
The 2nd hard drive is just used as data-storage space.

I bought a WD USB drive of 500gb and wanted to install Ubuntu with the intention to be able to boot this installation on any PC (if BIOS supports usb boot ofcourse).
As I understood from some research this should be possible using recovery mode.

I created a ext3 partition (15gb) for the installation of Ubuntu and added a swap partition (2gb). The rest is filled with a FAT32 partition.
Booted from Ubuntu 8.10 32bit live cd with following boot order in BIOS:
1. Cd/dvd
2. USB -> name of external drive, BIOS recognized!
3. USB FDD
4. Internal hard drive

Started installation and installed bootloader on the external hard drive as I want to boot from it (and also don't want to mess with my MBR on internal drive).

But as already mentioned in the beginning of this post, the external drive does not boot. No message or anything...
Boot order in Bios with external drive at 1st place, and Bios recognizes hard drive...

Note: Installing Ubuntu on usb flash drive does work!

Anybody any idea?
Am I trying to do something impossible, or am I doin something wrong?

---

### Post by earthpigg on 2009-07-08
i think you may be overcomplicating things a bit. try this:

boot into ubuntu as normal, just like you do every day -> plug in your usb hard drive -> system -> administration -> USB Startup Disk Creator


work?

---

### Post by Jeanke on 2009-07-09
Thanks for the reply, unfortunately this seems not to work for a usb external drive, only for a usb flash drive.

At least when I insert a flash drive I can install it without a problem, but with only my external drive connected I don't get target to install it to.

---

### Post by Jeanke on 2010-04-18
Sorry to wake this...but maybe someone is interested in the solution I found some time ago.

Seems the "easiest" way to accomplish what I was trying to do is to disconnect all internal and external hard drives from the PC and only connect the USB hard drive.
Then install Ubuntu on the USB, after the installation the other hard drives can be connected again and you can choose to boot from the USB hard drive, works like a charm.

After all I did not use it a lot but on all PC's I tried to boot the USB  (using recovery mode -> I adjusted the GRUB menu to make this the default boot option), Ubuntu worked quite well, of course without full hardware support.

---

