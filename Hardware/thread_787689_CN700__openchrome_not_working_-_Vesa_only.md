---
title: "CN700 / openchrome not working - Vesa only"
date: 2008-05-09
forum: Hardware
---

### Post by brainstuff on 2008-05-09
Hi people
Wondering if anyone can help...I'm trying to get 8.04 to use any driver other than Vesa for my VIA CN700 chipset running on a Jetway J7F2 mini itx mobo. 

The BIOS allows me to pump out through the S-Video (this PC is largely for my kids - gcompris, tuxpaint etc). So the install has gone okay largely, with all the hardware detecting properly - except for the VGA - I can only get it to display < 800x600 using Vesa/Mesa. It actually looks best in 720 x 576 (off the top of my head) - as it's an analog TV.

I've tried apt-get to install, remove, install, remove the VIA, Openchrome and Unichrome packages, tried adding Device "openchrome" etc to xorg.conf, but the only way I can bring up the window where you can select video driver from a list is by deliberately breaking my xorg.conf. It then defaults back to Vesa anyway. 

"dpkg-reconfigure xserver-xorg" only seems to deal with the keyboard, and if I stick the "-phigh" switch in there, it just gives me a message saying "overwriting possible custom xorg.conf" and saves a backup - but nothing else, it just goes back to the prompt.

I'm not at the machine right now, but does anyone have any ideas as to: 
a) what grep / lspci - type commands I need to give you lot to help 
b) how to fix it :)

By the way, I signed the Decent Via Drivers for Linux petition:
[http://www.petitiononline.com/vialinux/petition.html](http://www.petitiononline.com/vialinux/petition.html)

Yeah!

---

### Post by DynamicMouse on 2008-05-10
I am using the same jetway board as a pvr so I obviously need the tv out to be at its best.  I did have openchrome working in 7.10 but since going to 8.04 the display doesn't work correctly.  When using mplayer for example I get "can't open -vo ..." style errors, also where has the option under Administration gone where you can choose the driver to use, or am I missing something here!

So far I am actually very disappointed with linux on this board especially as it works fine on my other machines.

---

### Post by brainstuff on 2008-05-11
Hi
The application you're looking for is 
```
sudo display-config-gtk
```

For some reason it doesn't have an associated menu item that I can find any more.

I've got openchrome running on this box now, but to be honest it's no improvement over the Vesa driver - if anything, refresh rates seem a little slower, and the auto-detected 720x480 doesn't fit my TV (the top and bottom menu bars are cut off). I need to spend some time tweaking my xorg.conf I think....But the pull of GTA IV is just too darn strong :)

---

### Post by thak on 2008-05-24
So did the driver just stop working in Hardy?

I've got a laptop that I can run Mandrake 2008 just fine on, but Ubuntu (HH) doesn't work for crap.  The video is completely hosed.

Is there any hope for openchrome?  Or, based on your experience, should I just give up on Ubuntu (which I _much_ prefer) and switch to another distro that seems to support that chipset?

---

### Post by DynamicMouse on 2008-05-26
Strangley enough, after the last lot of updates I performed using the update application, the problems I had with mplayer seem to have gone away.

The only issue I have now is I can't turn all of the visual effects on like the morphing windows when you drag them and some of the screensavers don't work smoothly.

I am not sure if that was with vesa or via but either way it achieves what I wanted, I did read on another forum that even if you do get openchrome working it doesn't give you much over the vesa stuff.

---

### Post by mfallavol on 2008-08-07
So DynamicMouse, did you end up with the Openchrome or Vesa drivers?  I'm trying to use the composite out on a VIA EPIA-EN motherboard.

---

### Post by DynamicMouse on 2008-08-11
I ended up using the vesa drivers, they display fine through both the composite and s-video output on a jetway j7f2 board which should be very similar to your epia one.

I do have one display gripe and that is that I cannot put the screen effects on full.  So for example I don't get the nice screen swipe transition when cycling between desktops and when I drag windows they don't morph around the edges.

p.s. Just while I think about it, I did have a problem when I first tried to use the composite out on my jetway.  The solution was that I had simply selected the wrong setting in the bios.  Remember to make sure that both the output is set to composite and that the output is set to either RGB or YCrCb whichever your screen needs, mine was an old tv so used the YCr.

---

