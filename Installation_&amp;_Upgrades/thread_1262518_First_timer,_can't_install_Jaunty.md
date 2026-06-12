---
title: "First timer, can't install Jaunty"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by maxbox51 on 2009-09-10
Hi, I'm trying to install Ubuntu 9.04 on my Pentium II 350 MHz, slot 1 with 900+ MB memory.  I don't see any references to the problem I'm having (after a quick scan), so...here it is.  First and foremost, Windows XP is installed on this system, and still boots fine; so the hardware is working.  Secondly, I've been using Unix/Solaris/Linux since the early 1980s, but this is my first attempt at installing Linux on anything.  I don't want to dual boot, I just want a Linux machine.

I downloaded a disk image, made a CD, and got it to boot to the initial menu.  I can check the memory, and I can set options (but I have no idea what to set to what :).  Unfortunately, the only other action that works is booting from the first disk (it boots to Windows).  For checking the disc, installing, or trying Ubuntu from the CD, all that happens is the screen clears, a blinking cursor appears at the top, and...nothing happens for as long as I've been willing to wait, maybe 10 minutes at the longest.

What am I doing wrong?

PS -- I'm going out of town tomorrow, so I'll get back to replies on the weekend.

---

### Post by chinoy on 2009-09-10
Please post more info about your setup.
Make / Bios / Display card etc.

You may want to do a search and see what flavour of Linux has been used on your laptop in the past.

You may have to play with and tweak your bios settings.
I suspect your video is not VGA compatible or has native VGA suport.

Please post more info about your setup.

---

### Post by bhaverkamp on 2009-09-10
I would recommend trying the live CD. It boot into linux right off the CD and gives you a clue as to what works and what doesn't.

---

### Post by maxbox51 on 2009-09-12
> **bhaverkamp said:**
> I would recommend trying the live CD. It boot into linux right off the CD and gives you a clue as to what works and what doesn't.
I thought that's what I was doing?

---

### Post by presence1960 on 2009-09-12
> **maxbox51 said:**
> I thought that's what I was doing?
You are! look [here]("https://help.ubuntu.com/community/BootOptions") first. I would try F4 safe graphics mode first, if that doesn't work I would look into F6 options since you have an older pc.

---

### Post by maxbox51 on 2009-09-12
> **chinoy said:**
> Please post more info about your setup.
Make / Bios / Display card etc.

You may want to do a search and see what flavour of Linux has been used on your laptop in the past.

You may have to play with and tweak your bios settings.
I suspect your video is not VGA compatible or has native VGA suport.

Please post more info about your setup.

This isn't a laptop, it's a tower;  It was custom-built by a friend of mine who has moved away.  Here are the specs I can give you:  slot I motherboard, P2XBL/D; has the Intel 440BX AGPset chipset.  The graphics board is a Matrox Marvel G200; it's a PCI board, not the AGP version.  It also has a Sony CD-R drive, a 3.5" floppy drive, a Creative Soundblaster sound card, a Western Digital hard disk, and a Philips Brilliance 190P monitor.

Which bios settings might I need to tweak?

---

### Post by maxbox51 on 2009-09-12
Thank you, that's very helpful.  I'll take a good long look at the boot info you referenced before I try again.

---

### Post by Bartender on 2009-09-12
I tried using an old Matrox PCI card a few months back.  It didn't work in Jaunty.  Don't know if it's the same card as you have.

---

### Post by presence1960 on 2009-09-12
> **maxbox51 said:**
> Thank you, that's very helpful.  I'll take a good long look at the boot info you referenced before I try again.

If none of that works you can try te alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by RJARRRPCGP on 2009-09-12
> **maxbox51 said:**
>   For checking the disc, installing, or trying Ubuntu from the CD, all that happens is the screen clears, a blinking cursor appears at the top, and...nothing happens for as long as I've been willing to wait, maybe 10 minutes at the longest.


Possibly a corrupted CD or HDD.

---

### Post by maxbox51 on 2009-09-13
It looks like I needed the "edd=on" option, possibly in addition to mucking about with the acpi options.  That is, when I set my BIOS to not use acpi and told ubuntu not to look for it, nothing happened; however when I did it again with the "edd=on" option, the Live CD has gone past the blank screen stage.  I may try again, but with "edd=on" and acpi on also; I got some sort of error message about acpi, but at least it's making some progress.

Oh, and my disk is a Maxtor, not a Western Digital.

I'm pretty happy to have gotten this far!  Although, it's been 5 minutes now and I'm still restarting the display...but at least I have something to work with.

---

