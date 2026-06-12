---
title: "Insiprion 600m and fglrx"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Game_Ender on 2006-06-04
Has anyone gotten fglrx with 3d acceleration working on the Dell Inspiron 600m?  I am having issues currently explained [here]("http://www.ubuntuforums.org/showthread.php?t=186876").

---

### Post by akniss on 2006-06-04
I've tried several HOWTOs and other 'fixes' but I still cannot get fglrx working.  Or 3d acceleration with any other driver for that matter.  Luckily I never use anything that requires it, or I'd be really upset.

---

### Post by zahidism on 2006-06-04
i *think* it's working on my 600m (mobility radeon 9000 which is an IGP btw)  when i do glxinfo | grep rendering it says yes.  however, i must note when i try glxgears it maxes my CPU to full...so i dont know.  i dont run compiz or any games so i suppose it's no big.  oh and on an aside note.  my dell 600m had heating issues running ubuntu so i installed gkrellm with the i8k plugin from synaptic and now i believe it's as silent as when i run windows.  cheers.

---

### Post by Game_Ender on 2006-06-04
What does "fglrxinfo" return?  It it mentions ATI you installed fglrx properly.  When I use fglrxinfo I always get Mesa.  If you do have 3d Acceleration working what howto did you follow or how did you install it?

I too have a Radeon Mobility 9000.  It is also not unusall for 3D graphics to heavily tax the CPU on my 600m so a pegged CPU usuage is not unusual.

Thanks for i8k tip.  The standard CPU frequency scalling only takes my CPU down to 50% of its max speed, hopefully that will put it down where windows puts it.

EDIT: Just realized i8k only does fans.

---

### Post by zahidism on 2006-06-04
> zahid@zahid-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)


hmm, so I used  [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") it was actually really helpful.  try search mobility radeon in this thread, or maybe you can tell me your problem and ill try to help you except the fact that i'm a complete noob.  on another note, my cpu scaling is fine.  maybe try the centrino speedstep utility? search synaptic for it.

---

### Post by Paerez on 2006-07-17
I have fglrx 3d working on my inspiron 600m radeon 9000 mobility w/ 32m ram. I installed ati's proprietary 8.26 driver following:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)
Nothing fancy in my xorg.conf.

---

### Post by misha680 on 2006-07-23
Mine works too. Followed same instructions as Paerez. Don't forget to replace your libGL.1.2.so with the one I attached. I recommend doing the following so updates will never overwrite it unelss you do it yourself:

```
bunzip2 libGL.so.1.2.fglrx.bz2
sudo cp libGL.so.1.2.fglrx /usr/lib
cd /usr/lib
sudo rm libGL.so.1
sudo ln -s libGL.so.1.2.fglrx libGL.so.1
```

This way, you will keep both libGL.so's in your /usr/lib, but just change the symlink. 

Oh, and one confusion I saw in the posts was whether or not to put fglrx in DISABLED_MODULES  in /etc/default/linux-restricted-modules-common. Yes, you need to do this (well for 8.26.18, for   8.25.18 it doesn't matter because that is the version in restricted modules).

Misha

Misha

---

### Post by misha680 on 2006-07-26
Btw, if you want compiz to work on your 600m with fglrx drivers, you need to use the following link to install an older version of Xgl than the one that's in the compiz repos. Otherwise it won't work:

[http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb](http://ubuntu.compiz.net/pool/main/x/xserver-xgl/xserver-xgl_7.0.0-0ubuntu28_i386.deb)

Took me quite some time to get this answer, so I wanted to save y'all the trouble since you are fellow inspiron 600m owners. Compiz runs amazingly fast on my computer, although I upgraded my RAM to 1.5 gb so maybe that helps.

Misha

p.s. also, if you want suspend to work on Ubuntu 6.06 with fglrx, I had to change the following settings in /etc/default/acpi-support:

ACPI_SLEEP = true
SAVE_VBE_STATE = false
POST_VIDEO = false
USE_DPMS = false

It works even with the ATI power management enabled.

---

### Post by dppowell on 2006-09-29
Thanks for posting those ACPI settings, Misha.  They just did the trick for my 600m, too.

---

