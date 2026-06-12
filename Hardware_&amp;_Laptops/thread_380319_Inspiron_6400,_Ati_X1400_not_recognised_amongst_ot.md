---
title: "Inspiron 6400, Ati X1400 not recognised amongst other things"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by maggot_brain on 2007-03-09
Hello everyone,

I just got (yesterday) a brand new Dell Inspiron 6400 with the ATI Mobility X1400 graphics card and I'm having serious problems getting the X1400 recognised.  I've tried 6.10 in both X86 and X86-64 versions.

specs:

UK Model
Core 2 Duo 1.66 GHz
1 GB Ram
120 GB SATA HDD
15.4" widescreen display (1280x800)

X.org only recognises the graphics card as a vesa vga card.  The refresh rate and resolution is totally screwed up.  The ATI Radeon framebuffer also does not work and the text console looks blocky and horrible.  I think it may be due to the kernel not recognising the gfx card properly.  When I use the 'lspci' command on either X86 or X86-64 Edgy the gfx shows up as ATI vga controller unknown model.  So I thought I'd download the Feisty Herd 5 image (X86) and see what happens there.  If I boot from it then lspci **does **show the machine as having a X1400 card on it.

Has anyone else run into these issues on an Inspiron 6400?  I'm thinking with Feisty having an updated kernel it should detect and configure the X1400 correctly.  Is anyone running Feisty on there 6400?  Also the BIOS is the very latest version A13 and the machine came with Windows Vista (ugh!!!!).  I'm thinking the problem may be due to the latest BIOS revision.  Are there any BIOS options I can change to get the framebuffer and X working properly?

I realise that this is a bit of a rambling post with not much information.  Let me know if there's anything else I need to post logs or spec wise.  I've been running Debian Etch on an old iBook G3 without a hitch so I though a new Dell should have been easy to get up and running.  Looks like I was wrong on that one.

The sound card and wireless work out of the box it's just the gfx card that I'm having problems with.

thanks,

Ananda

---

### Post by falcons7 on 2007-03-09
i have a friend with the same laptop as you.... backup your xorg.conf and try this link... it worked for him :D


[http://www.ubuntuforums.org/showthread.php?t=194993](http://www.ubuntuforums.org/showthread.php?t=194993)

---

### Post by Pugwash on 2007-03-10
Hi, I'm on the same laptop and have the same graphics. try this - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-fa96a980ed5a785b2b6454ee0183dc9eb115a2f0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-fa96a980ed5a785b2b6454ee0183dc9eb115a2f0)

---

### Post by maggot_brain on 2007-03-10
Thanks for the advice, I should have mentioned that I got fglrx working already.  I don't mean to sound like an arrogant sod but I pretty much know what I'm doing with Linux configuration when it comes to the standard stuff.  The real problem is getting the framebuffer working properly so the console doesn't look horrible.  Also the splash screen doesn't work properly because of tihis.  Are there any kernel options (ie grub options) to force the ATI Radeon framebuffer and get it working?

thanks

Ananda

---

