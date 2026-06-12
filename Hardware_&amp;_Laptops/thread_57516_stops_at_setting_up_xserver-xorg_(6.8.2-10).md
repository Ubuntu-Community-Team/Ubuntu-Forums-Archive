---
title: "stops at setting up xserver-xorg (6.8.2-10)"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by willfish on 2005-08-16
Greetings

New to Ubuntu

I have a "Clevo 660 notebook".......1999 vintage......PII 

It has:- 

[I]SystemSoft MobilePRO BIOS Version 1.01 (2482-00)
Notebook Computer Model 668 Version 1.00.1.06 PIIM5+
Build in time (09/08/98 14:10:40)
266Mhz Pentium II CPU
External Cache: 512K installed
SystemSoft Plug-n-play BIOS Ver 1.17.01
Base memory 640KB
Extended memory 127MB
Total Memory 128MB
[/I]
I am trying to load ubuntu-5.04-install-i386.iso and it gets to "setting up xserver-xorg (6.8.2-10) ..." and stops.

I can not do anything key board Cont'l Alt Del doesn't work so I have to power off

I power it back up and Ubuntu loads kernal 2.6.10-5-386 in command line form no GUI.  

It ask if I want to udate pkgs I have done and eventually 

"Ubuntu 5.04 "Hoary Hedghog" XXXX tty1"
XXXX login:
appears.

I log in and time & date stamp & programs with Ubuntu are free statement
the "username@XXXX:
appears

There appears no GUI am I doing something wrong

Am I expecting too much of the PII to run Ubuntu 5.04

Should I be running an earlier version?

I look forward to your assistance.

If this has been addressed elsewhere please append a  hyperlink and I'll look at that instead.

Many thanks in advance

willfish

---

### Post by tim_c on 2008-01-02
Slight delay in replying, sorry.

Other folks, there be wrinkles in this posting of more general interest.

I am pretty sure from you description I have just succeeded in successfully getting Debian 4 installed and with what I have discovered I guess that most Linux or BSD could be used. Good idea to use a light X desktop though... it _will_ run a full Ghome, if a bit glacial, met worse though.

Gutsy should be fine. 2.4 core would though make more sense. DSL or DSL-N work well, just boot with fb1024x768

Avoid live CD like the plague.

The key was discovering that DSL had no problem provided a simple configure was made. 

Tip: tools like that are good for rapid trying things out, then look at the settings it's found.
I used DSL-N mainly.

Cardbus PCMCIA slots are enabled without problem by most dist, network and so on. Same for USB.

All this is easy stuff in hindsight, yet no full instructions seem to be on the net for this stuff which is very similar to the problems many others find with laptops.

Biggest trouble is S3 virage on a laptop.

Rough idea

add video=fbdev and optionally vga=791 to the grub kernal line (has to be done in a long lived way when you want it permanent, add to I think auxillary postscript in grub using an editor.
The effect of this is creating fb0 devices which have to be done in real mode as boot starts, the buffers have to be set up first, can't be done by an OS from fancy processor modes.

The card is correctly identified by X as S3 virage

What is not clear about the X config is there are multiple layers of drivers and where it says select driver it is hogwash, nothing you put there changes the actual card driver used. What you are selecting is perhaps a shim between the actual driver and X. Select fbdev and say use frame buffers.

Do not try and probe for a monitor, lockup if you do.
Set 640x480, 800x600 and 1024x768 when prompted.

Other thing is say No to autodetect, then use advanced setting and just hit return on the default scan rates offered.

I think I set colour depth to 16

Display is normal, same as w98 or XP *(yes XP is ok if not practical)
Even by today's standards it's not bad, just 1024x768 to give the age away.

Mouse for me with external used is aux port. Both NEC glidepad and external work concurrently on defaults.

Few other wrinkles I won't go into here.

Tip if the CD drive is reluctant to read CDR reliably, get the tiny floppy boot selector, adds a better CD driver. Boot into that, launch boot from CD there.
Here it is, definitely a good tool to have around if you dabble in computers
[http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html)

I popped in a spare 6G drive (Hitachi, standard 12.7mm height), trivial changing drives on this machine. Drive is in a cassette carrier, four screws, done, pop carrier with new drive in the hole, turn on.

Some other wrinkles.
At the time of posting this do not touch rawwritewin on XP, perhaps others, it locks the floppy drive in RAW mode, I think by leaving a file handle open on exit so that XP or anything else is denied access unless you kill the handle. Good old rawrite from the command line works as ever.

A brilliant Linux or Windows rescue package is BG rescue, two floppies or tiny CD.
[http://freshmeat.net/projects/bgrescue/](http://freshmeat.net/projects/bgrescue/)
And [http://home.datacomm.ch/~bgiannone/rescue/current/](http://home.datacomm.ch/~bgiannone/rescue/current/)

---

