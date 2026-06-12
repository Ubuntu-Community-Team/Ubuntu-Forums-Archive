---
title: "Black Screen after bootup"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by shogunami on 2009-04-26
Hi!

I'm new to these forums, and I'm not really sure where to post this, but I'll try here.

I upgraded Ubuntu from 8.10 to 9.04 and whenever I boot into Ubuntu now, I get a black screen where the login screen should be, keyboard or mouse doesn't respond and I'm just stuck =/
Tried a fresh reinstall, but didn't go any well at all =/

I've read around on forums and googled a lot, even on these forums, but I've found no solution so far. Does anyone know what's going on?

My specs are;
Intel E8400 @ 3.6GHz
ATi Radeon 4870x2 2GB (issue is appearently with both nvidia and ati cards =/)
4GB Ram
Asus P5Q mobo
1.25TB of HDD's.
My screen is an ASUS VW222U, if it's any help.


I'd really appreciate any help I can get.
Thanks!

---

### Post by Tristan_F on 2009-04-26
It might be a noob question but did you try the live CD juste to know if everything is working fine with it?

---

### Post by shogunami on 2009-04-26
I used USB Live CD, and it worked fine =/

---

### Post by shogunami on 2009-04-26
*shameless bump*

I'm dying here =/

---

### Post by pocon on 2009-04-26
Sounds a lot like what happened to me.
Try booting in safe mode, you'll come to a menu that gives you a few options, you'll probably need to scroll down a bit to get to the one that brings you to a root prompt.

type:

```
apt-get remove fglrx*
```

then type exit, and select resume normal boot.

Worked for me.

---

### Post by shogunami on 2009-04-26
and graphics still worked? I'll try it and get back to you :)

---

### Post by shogunami on 2009-04-26
I did the apt-get remove fglrx*, and I'm now inside Ubuntu, however, once I try to use the EngyNG drivers, it goes back to bad.

I wont be able to use compiz without drivers, right? :S

---

### Post by maclinux on 2009-04-27
The same always happened to me.  The only live cd that mounts the graphics card is 8.04.  The others like 7.1 or jaunty go straight into a black screen.  I never have or had visual effects enabled under 8.04 because is just not plain possible, which tells me the onboard video is very basic indeed.

My specs:

Pentium III - HP Vectra
512k Ram
Video Adapter Intel(R) 82815 Graphics Controller (Microsoft Corporation) (32 MB)
3D Accelerator Intel i752

I noticed this also happens with several other live cd distros.  The live CD graphics just wont mount.

I know this has becoming quite a common annoyance.

Any help will be very much appreciated.

Thanks.

---

### Post by shogunami on 2009-04-27
> **maclinux said:**
> I know this has becoming quite a common annoyance.

Any help will be very much appreciated.

Thanks.

I really do second that motion!

I've got graphics now, but poor graphics. Annoying, half the fun in Linux is customizing the UI.

---

### Post by pocon on 2009-04-27
I have an ATI X1600 video card - I added the Driver  "ati" line to this section in my xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver    "ati"
EndSection
```

I was then able to select a resolution from the display settings that was appropriate for my monitor.
It may be of some help.

---

### Post by shogunami on 2009-04-29
I managed (messed up again and I cant fix it at all) to get graphics to work -'ish, and I could actually use Ubuntu, but it's not enough for me.

I have tried many things now, many "solutions", some have worked temporarily, and then fails when I reboot, or some that works but the graphics is very limited. I feel that for once Ubuntu has failed me, and it's not a pleasant feeling. Like, how does it actually feel when Windows Vista is more stable and works better than Ubuntu? :S

I hate Vista, but I HAVE to use it to get things done.

I'll just stand by for a while, or try another distribution =/

Thanks for the many answers and suggestions.

---

### Post by pocon on 2009-04-29
I can feel your pain. 

Does it still work ok from the usb live cd? If it does you'd think it would be ok from a hard drive as well. Maybe something went wrong with the install, or maybe some of the subsequent tinkering didn't help ( I've been there ).

I guess you could always try a fresh install before you abandon ship.

I've set up a dual boot with XP, I have a cintiq graphics tablet and the drivers for linux just aren't there yet - so I have to fall back to windows to take advantage of it fully.

---

