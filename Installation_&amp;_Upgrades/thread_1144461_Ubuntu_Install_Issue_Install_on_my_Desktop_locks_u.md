---
title: "Ubuntu Install Issue: Install on my Desktop locks up!"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by NDWolfwood5268 on 2009-04-30
OK, this is my 2nd Ubuntu install, my laptop (that I'm on) has been awesome and steady for months now. So I want to induct the bigger, badder desktop PC into the bunch. 

Here's an abbreviated set of PC specs:

DDR3 Corsair Dual Channel RAM
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145182](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145182)

Intel BOXDX38BT LGA 775 Intel X38 ATX Intel Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121090](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121090)

Intel Core 2 Quad Q6600 Kentsfield 2.4GHz 2 x 4MB L2 Cache LGA 775 Quad-Core Processor
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115017](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115017)

Here's my issue:

I try installing Ubuntu 8.10 and the thing let's me choose options (install, run without affecting computer... etc.) but once I choose, it starts the loading bar back and forth, but eventually stops. I can hear the disc drive stop reading at this point as well. 

For Jaunty 9.04, I get past the initial options, and the thing gets to said DOS screen with nothing but a single blinking entry cursor, and I can't type anything. The lights on my keyboard and mouse go off singaling that they're disabled I think...

If I do alternate boot options, and adjust settings... well, I get this issue pretty much: [http://ubuntuforums.org/archive/index.php/t-225589.html](http://ubuntuforums.org/archive/index.php/t-225589.html).

Hence I think this is a system hardware issue... I have an Intel quad core processor, for the record. 

What I've tried:

1) Boot from CD
 -Multiple image downloads, multiple CD's burnt, including different kinds of CD's and different speeds. I've tried 9.04 and 8.10.
2) Install from the Hard drive itself (hangs up at a command about IRQ 16... I'd have to run it again to get the line). 
 - Ref: [http://ubuntuforums.org/showthread.php?t=28948&page=6](http://ubuntuforums.org/showthread.php?t=28948&page=6)

Note: I've installed Ubuntu on this laptop I am using a few months ago, and it was incredibly easy. I got my coworker on Ubuntu last week, he had no issues... Why is this happening with my superior desktop PC?.. I'd love to get this thing up and running so I can start developing and stuff, so please post with help! There MUST be a way right?..

---

### Post by upchucky on 2009-04-30
there are 2 things that could be happening, one is called busybox
the other is a hang when it is trying to load the graphic display

busybox indicates a possible bootloader problem, grub is confused as to where the os is or what to boot, or is not getting called at all, 

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

the display issue is a trial and error setting of the resolutions.
search here for info this is a very common problem and it is very likely that someone has same card and display as you and has posted the settings.

did the live cd boot into a graphical display before you actually did an install? if yes then the display will work you just need to find the right settings.

---

### Post by NDWolfwood5268 on 2009-04-30
Ok, first, thanks for the reply. Now on to your responses:

1) Now, this may be me being ignorant, but I tried a number of CDs and versions. Grub is stored on disc, isn't it? so the odds that I have had multiple bad Grub copies is very poor (my coworker lent me the EXACT CD he used to try it).

2) Resolutions and guessing... fun fun... yes the graphical display DOES show up at first (assuming you mean the logo and the initial 'how to boot' options of install, check defects, etc.), note my 8.10 experience, I get a graphical loading bar even... Guess I'll have to explore this. Is it dependent on my graphics card?

Again, thanks.

---

### Post by upchucky on 2009-04-30
yes it is dependent on your graphics card and screen capabilities.

grub is modified for each and every pc, as they all are different, that is why someone created supergrub, it takes most of the work out of setting up grub.

plus everyone learns a great deal when they understand how an os is actually booted.

---

### Post by NDWolfwood5268 on 2009-04-30
Ok, well, I'll play with Grub a bit then... I think that's probably it based on my research, but to test the resolution idea, I'm downloading the text-only alternate install disc to try that out.

Thanks for the help, I'll post if it worked or not.

---

### Post by NDWolfwood5268 on 2009-04-30
Upchucky, super grub sounds like it repairs a grub booter AFTER an install... My issue is DURING install. Am I wrong? My Ubuntu CD freezes up during install, and I only managed to install it on my laptop. My desktop can't get past the boot load.

---

### Post by NDWolfwood5268 on 2009-04-30
I may have found the answer... le tme see if it installs

---

### Post by NDWolfwood5268 on 2009-04-30
... Ok, I managed to fix my issue thanks to my said co-worker. It's an issue on Intel's side for not supporting IDE fully or something... I don't know the technical details, but should anyone have a similar issue, check yer drives!

Short answer:
I had 2 SATA and 1 IDE drives (IDE a leftover relic of my last PC upgrade that I never removed). It couldn't figure out what the hell it was. I removed it, it booted fine... Short IM correspondance below to highlight.

(09:11:10 PM) wolfwood5268: "bios bug, no explicit IRQ entries, using default mptable. (tell your hw vendor)"
(09:11:19 PM) wolfwood5268: do you have ANY idea what the f*** that means?
(09:11:32 PM) coworker: yeah ur using intel though right./
(09:11:36 PM) wolfwood5268: yeah
(09:11:52 PM) coworker: when AMD was poor back in the day, they left out the support for the use of IRQ 14
(09:12:12 PM) wolfwood5268: I get locked up at irq 16 during install from my hard drive
(09:12:13 PM) coworker: why the f*** they did that, i have no gd idea, but caused problems for me
(09:12:20 PM) coworker: ohhh u can do this
(09:12:24 PM) wolfwood5268: lol
(09:12:25 PM) wolfwood5268: how?
(09:12:38 PM) wolfwood5268: BTW, I have no idea what an IRQ is
(09:13:08 PM) coworker: move your HD using that IRQ, the Interrupt Request Number is the CPU talking with the MBoard
(09:13:16 PM) coworker: to access the device
(09:13:22 PM) coworker: move the device, problem solved
(09:13:33 PM) wolfwood5268: ... ?
(09:13:37 PM) wolfwood5268: My HDD is in the wrong port?
(09:13:50 PM) coworker: ya it has to be something like that
(09:14:23 PM) wolfwood5268: ...
(09:14:29 PM) wolfwood5268: here's teh line it gets hung up on
(09:14:31 PM) coworker: melieve me, moving my PCI card for AMD processor worked, and ive been shocked for life. the painfulness of finding out the world is round and jagged is still with me.
(09:15:20 PM) wolfwood5268: "pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
(09:15:21 PM) wolfwood5268: "
(09:15:40 PM) wolfwood5268: there's an address of some sort before the line to mark it, didn't think it'd matter
(09:16:23 PM) coworker: PATA, thats the 66/100 tech

So yeah... I was kinda mad after discovering this little issue... But whatever...

---

