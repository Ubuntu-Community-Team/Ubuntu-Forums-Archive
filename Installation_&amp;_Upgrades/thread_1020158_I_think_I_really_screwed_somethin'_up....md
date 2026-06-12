---
title: "I think I really screwed somethin' up..."
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by whitecs on 2008-12-23
Hello all,

My friend recently showed me his machine that he loaded up with Ubuntu, and I thought that my older PC could use a bit of a change. So, I thought I would get rid of XP and start out fresh with Ubuntu. I burned the disc image and did the whole try-it-out thing, and it worked perfectly. I was reading up on partitioning my hard disc, and followed the steps and was ready to have my PC single boot Ubuntu. When I load the disc into the PC and attempt to install Ubuntu, the installation process begins, but it freezes up about a minute in, leaving my Caps Lock and Scroll Lock lights blinking on my keyboard. I went into my system BIOS and reset it using alt-tab E F B thinking that might do the trick, but it didn't. I also switched the hard disc and floppy drive off from the boot sequence. I've pretty much run out of ideas... you guys got any? Thanks in advance.

---

### Post by melojo on 2008-12-23
Can you still boot into the live cd?
Did you test the disc for errors?

---

### Post by taurus on 2008-12-23
Are you planning to dualboot (Ubuntu and windows) or do you plan to install Ubuntu as an only OS on your machine?

What's the spec of your machine?

You can always try the alternate CD if you want to install it on your machine.  Remember to burn it at a slow speed.

---

### Post by abn91c on 2008-12-23
other than the keyboard and mouse,and  internet connection,  remove all peripherals like printers, external storage, etc.  before you try installing again

---

### Post by whitecs on 2008-12-23
The machine I'm trying to install it on is an old Dell Dimension 4300, 1.6 GHz processor, 756 MB DDR memory, 80 GB hard drive. I was planning on single booting with Ubuntu. I could get the live CD to load, with the main menu appearing. I tested my memory and everything checked out, along with the disc. The error message I get is "Strike F1 to retry reboot, F2 for setup." I was a little confused, so I tried to load my Windows recovery disc just to see if that would load and it gave me the same error. Thanks again.

---

### Post by albinootje on 2008-12-23
> **whitecs said:**
> The error message I get is "Strike F1 to retry reboot, F2 for setup." I was a little confused, so I tried to load my Windows recovery disc just to see if that would load and it gave me the same error. Thanks again.

Some BIOSes on certain computers are very primitive about the boot-order (and changing that) is my experience.

Did you change the boot-order in the BIOS in order to boot ?
It is possible that you have to go into the BIOS to make it boot from either cdrom and/or hard disk again.

Or did you perhaps leave some usb-stick in the usb-slot ?

---

### Post by abn91c on 2008-12-23
on dell pc's you dont have to go into bios, reboot, wait  2 to 3 seconds after the Dell logo appears hit F12, then select boot from cdrom. 
Go into the bios and reset it to setup defaults, that is why you got the "press f1 error"

---

### Post by joshmuffin on 2008-12-23
First of all welcome to Ubuntu I hope you enjoy your experience.

My first suggestion would be (its a bit of a hassle) but you could try installing from a USB. If your going to try this:
When the install starts press cancel and run a live session. Then go system > administration > Live USB creator. You'll need to get a Ubuntu image. (live USB creator is only included on 8.10 intrepid Ibex Live CD, Not 8.04 Hardy Heroin)

The other suggestion is when the install starts press cancel and run a live session. Then you can start the install again.

Hope I was able to help, Joshmuffin

---

### Post by whitecs on 2008-12-24
Thanks Josh, I installed via USB, and it worked great.

---

