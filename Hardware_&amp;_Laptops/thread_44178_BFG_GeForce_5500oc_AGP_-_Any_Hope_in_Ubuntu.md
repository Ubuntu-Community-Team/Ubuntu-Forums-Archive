---
title: "BFG GeForce 5500oc AGP - Any Hope in Ubuntu?"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by polo_step on 2005-06-24
I got this thing on sale for my other box a month back and it just tore up XP so badly it wouldn't even boot any more.  Did everything - EVERYTHING - tech support said and it wouldn't run even on a brand new virgin XP install without bluescreening after a few minutes.  A tech support manager said it's a common XP overwrite bug that shows up on some boxes with nVidia cards, and Microsoft is working on it.

Any hope of this thing working any better in Ubuntu?  It's just sitting here on the desk doing nothing, a total waste of money otherwise.  I've heard that nVidia cards actually work under Linux, but I don't want to wipe out this system like I did with the last one if it won't.

Thanks for any help.

---

### Post by intangible on 2005-06-24
I seriously doubt it could mess up your Ubuntu install at all.  The worst that might probably happen is that it won't work properly, but you can always go back to your normal video.

Here's a quick and easy guide to getting nvidia cards working properly on Ubuntu: [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

Oh wait... I mean... it won't work at all, how about just sending it to me so I can "dispose" of it properly :D

---

### Post by polo_step on 2005-06-24
I think there's a bit more rigmarole I have to go through first before that.  I know I have to disable this cheap onboard video in the BIOS and I may have to go through something to purge all other existing AGP drivers -- at least I had to go through this in XP on the other box.

It was the most complicated video card installation I'd ever done in Windows.  Perhaps it's dead simple in Linux, I dunno.  I hoped maybe someone here had tried it.  

Someone else had a very similar card (same one but with 256M instead of 128M) and couldn't get it going in Ubuntu according to another thread here a few days ago.  I don't think that ever resolved.

---

### Post by polo_step on 2005-06-25
UPDATE:  As noted in the other threads, I now seem to have the card working, maybe even properly.

It's official:  I've put the "Powered by BFGTech" logo sticker on the front of the box.

It CAN'T break now can it?  ;-)

---

### Post by intangible on 2005-06-26
It shouldn't :D

Open a terminal and type **glxgears** if it's over 1000, your accel is working.  You can also type **glxinfo** into a terminal and make sure it says "nvidia" somewhere to insure it's working.

---

### Post by polo_step on 2005-06-26
[QUOTE=intangible]
Open a terminal and type **glxgears** if it's over 1000, your accel is working.[/quote]
Well, then, it looks good:
anonymous@beatdown:~$ glxgears
6377 frames in 5.0 seconds = 1275.400 FPS
6872 frames in 5.0 seconds = 1374.400 FPS
5653 frames in 5.0 seconds = 1130.600 FPS
6809 frames in 5.0 seconds = 1361.800 FPS
6961 frames in 5.0 seconds = 1392.200 FPS
6866 frames in 5.0 seconds = 1373.200 FPS
6956 frames in 5.0 seconds = 1391.200 FPS
6899 frames in 5.0 seconds = 1379.800 FPS
5837 frames in 5.0 seconds = 1167.400 FPS
6917 frames in 5.0 seconds = 1383.400 FPS
6841 frames in 5.0 seconds = 1368.200 FPS
6840 frames in 5.0 seconds = 1368.000 FPS
6879 frames in 5.0 seconds = 1375.800 FPS
6768 frames in 5.0 seconds = 1353.600 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

...and that's with a ton of other stuff going on, if that matters.  Does glxgears function as a card burn-in as well?

> You can also type **glxinfo** into a terminal and make sure it says "nvidia" somewhere to insure it's working.
That looks OK:

anonymous@beatdown:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
[etc.]

---

### Post by polo_step on 2005-06-26
[QUOTE=polo_step]...and that's with a ton of other stuff going on, if that matters.[/QUOTE]
[Later...] Apparently it does, though just slightly.

With everything else shut down, it does a consistent 1393.xxx FPS.

---

### Post by diablo75 on 2007-07-21
I have a 5500 OC AGP (256 MB) that I'm having problems with.  I don't know if this is strictly a problem with the card or what, but here's the problem:

If I'm running Beryl, or say, I'm not running beryl, but playing OpenArena, the card will seem to work perfectly fine for a few minutes.  But suddenly, lock up.  Half the time it locks up it stays locked for about 20 seconds, and then kicks back out and keeps on running.  Other times, the system becomes completely frozen.

Anybody else experience this problem?

---

