---
title: "HP NC4200 - failure to install dapper."
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by ashp on 2006-07-25
Hi,

I just tried to install Dapper and broke my laptop terribly, meaning I had to slink to the company IT guys as they have stopped booting from external devices, so I couldn't sneakily fix it.

I did a net install, and it worked fine up until it tried to setup X, it tried to load X, breaking immediately leaving a couple of white boxes of corruption on the screen.

I tried changing back to a console, blindly, but that didn't work.  I couldn't kill X.  I tried going to alt-f2 and blindly typing killall X, but that wouldn't work either.  It hadn't set up a bootloader so I couldn't get back in to force it to continue.

Has anyone else installed on one of these laptops?  I had it in the docking station, could this have been the problem, my external display?  I'm willing to risk ridicule by IT by trying it again out of the docking station!

---

### Post by Tycho C on 2006-07-25
I have an HP Compaq nc4000.  Dont know how closely related that is.   I too dont have a CD rom drive in the machine.  I used an external drive to load Ubuntu.  So far, Ubuntu seems to be the only distro that works with the wlan out of the box. Im new to linux so I wish I could help you more, but I can tell you I havn't had a problem installing it with an external drive.

---

### Post by Myrtti on 2006-08-02
> **ashp said:**
> I did a net install, and it worked fine up until it tried to setup X, it tried to load X, breaking immediately leaving a couple of white boxes of corruption on the screen.

That's exactly the behaviour I got last week trying to do OEM install on one. I managed to get the install work by using an older Dapper install, one from February (Flight 4 apparently). It does the changes to GRUB before trying to install or configure X.

---

### Post by ashp on 2006-08-02
I think I'm going to try and get to the beginning of the install, manually install grub, let it carry on until it crashes on me, then go from there.  I'd file a bug if I wasn't on holiday right now, when I get back I'll see if anyone else did and file one if they didn't.

---

### Post by unprinted on 2006-09-19
Hmm, an earlier reply re the nc4000 is interesting, because I can't get to run 6.06 (Dapper) on mine.

With the ordinary install and both 'safe mode' video and vga=771, it gets as far as playing the startup music, but never gets further than "Window Manager" on the splash screen.

The mouse moves happily, so it's not locked up completely.

Suggestions welcome, because I know some people have it working.

---

### Post by unprinted on 2006-09-24
Ah ha. Using the alternate (text mode) install CD worked for me. As this used to be the only installer, this may be why using an earlier install CD worked for someone else above.

Once booted, the graphics display is slightly out - some buttons have horizontal lines on them. Moving the mouse point over them makes them look ok, but clearly something is slightly wrong with the graphics / driver.

---

### Post by unprinted on 2006-09-25
Changing the video driver in /etc/X11/xorg.conf to "vesa" rather than "ati" makes the 'horizontal lines in some buttons' problem go away, so it's some sort of video driver issue.

Any suggestions?

---

### Post by unprinted on 2006-10-27
Ah ha, the ati drivers with Edgy appear to work.

Thanks to those responsible.

---

