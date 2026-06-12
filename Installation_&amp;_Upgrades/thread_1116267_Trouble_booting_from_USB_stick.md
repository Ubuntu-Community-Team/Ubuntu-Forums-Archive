---
title: "Trouble booting from USB stick"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by Andrew Golightly on 2009-04-04
Hi all,

I have a 1 Gb USB stick.. that I excitedly installed Ubuntu on to show others how easily I can demonstrate Ubuntu. Unfortunately it didn't work. I tried my flatmates USB stick, and it worked perfectly. SO it seems it has something to do with my USB drive.

I read [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and it said nothing was guaranteed..

I'm basically keen to get a USB drive that I can demonstrate on as many machines as possible.

The drive I have that didn't work is a Kingston DataTraveler ([http://www.kingston.com/flash/datatraveler.asp](http://www.kingston.com/flash/datatraveler.asp))

Thoughts? The intention is to spread the word of Ubuntu ever more :KS

thanks

---

### Post by utnubuuser on 2009-04-04
Hi -- What is the size of your roomie's USBstick?  I was under the impression that a minimum of 2gigs was required, though I might be wrong.

---

### Post by Andrew Golightly on 2009-04-05
Good question... I think :)

I seem to remember that her USB stick was greater than 1Gb anyway... but I think more importantly, it was Hi-speed.. I think that makes a difference too. I don't understand too much about that part, but I'm aware some USB drives are USB 1, and some are 2.

In terms of loading on the image, that part worked fine on my 1Gb USB stick. I only bought that USB stick last year... so I'm a little confused.

---

### Post by McMagic on 2009-04-27
I had a similar problem with and old-er 1gig Corsair Flash voyager in the case of making a bootable USB drive containing "Sugar on a Stick". The ISO was written to the disc fine, but when it came boot time, it just hung there. Convinced it was a problem with the I/O speed of the elder drive, I tried it with my new 4g Kingston DataTraveler. No more worries.

---

### Post by hatalar205 on 2009-04-27
1 gb is enough.
Try this program.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Titoolsen on 2009-04-27
I have created a bootable USB pen. I have changed the order of rebooting in the BIOS but can't seem to get the PC to boot from the USB pen. Can anyone advise or point me to an FAQ?

---

### Post by hatalar205 on 2009-04-27
> **Titoolsen said:**
> I have created a bootable USB pen. I have changed the order of rebooting in the BIOS but can't seem to get the PC to boot from the USB pen. Can anyone advise or point me to an FAQ?

At first I had the same problem. And then I formatted before copying the files (as it was advised in the forums) and it worked well. I did this with the program "unetbootin" on vista. I'not sure but if you do that on ubuntu something goes wrong because of some root privilages. So if you have a xp or vista;
1 - Download the program (unetbootin).
2 - Format USB Stick (Fat32 is prefered).
3 - Download the .iso file of your distribution.
4 - Run the program (it takes nearly 20 minutes to create a USB Stick).

I have tested this many times and everything has worked perfect.
The Distributions I installed in this way:
1 - Ubuntu 8.10
2 - Open Suse 11
3 - Fedora 10
4 - Linuxmint 6 KDE
5 - Xubuntu
6 - OpenGeu
7 - Mepis 7
....... and of course Ubuntu 9.04 Jaunty Jackalope

---

