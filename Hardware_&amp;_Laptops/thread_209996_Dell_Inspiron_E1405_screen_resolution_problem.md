---
title: "Dell Inspiron E1405 screen resolution problem"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by fledylids on 2006-07-06
I'm using a Dell Inspiron E1405, with an Intel video card (Intel Media Accelerator 950 Graphics) running on an i810 driver. However, since installing Ubuntu, I have not been able to use any sort of widescreen resolutions. My screen resolution is 1024x768, and when I go to System-->Preferences-->Screen Resolution, the only option I have is 1024x768.

Additionally, I have tried using 915resolution to fix the problem, but doing so doesn't seem to work. I want to get a 1280x800 resolution, and (maybe, but I could be pushing my monitor/graphics card) possibly 1440x900. I'll post my 915resolution file and my xorg.conf here:

```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
#
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
MODE=3c
XRESO=1280
YRESO=800
MODE=3a
XRESO=1440
YRESO=900

```

xorg.conf is attached

Any help with this is appreciated greatly!

---

### Post by xrchris on 2006-07-06
So is the correct native resolution 1440x900?

---

### Post by dracolich on 2006-07-06
All works fine here with 915res and i810 on my 1405.

If you have the shiney screen you want 1440x900, if you have the mat screen you want the 1280x800 res.

---

### Post by fledylids on 2006-07-06
[QUOTE=xrchris]So is the correct native resolution 1440x900?[/QUOTE]

According to Dell's website, the native resolution should be 1280x800. Had I gotten the better graphics stuff, it would be 1440x900.

---

### Post by sayanchak on 2006-07-06
The native resolution is a property of the screen tha you choose, not the graphics card. The Intel 950 is very much capable of supporting 1440x900 if you do have the "glossy" truebright or whatever high resolution screen. However 915resolution should detect the native resolution automatically.

---

### Post by xrchris on 2006-07-06
OK assuming you are using Dapper 6.06.

Have you followed the instructions on the following link EXACTLY, only making changes to input your required resolution (1280x800 for matt screen or 1440x900 for the glossy screen)?

 [https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654](https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654)

Further advice for this can also be sought at [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

### Post by fledylids on 2006-07-06
[QUOTE=xrchris]OK assuming you are using Dapper 6.06.

Have you followed the instructions on the following link EXACTLY, only making changes to input your required resolution (1280x800 for matt screen or 1440x900 for the glossy screen)?

 [https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654](https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654)

Further advice for this can also be sought at [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)[/QUOTE]

Thanks so much! Using that ubuntu.com guide, I got 1280x800 to work. I don't think I'll bother with 1440x900, I don't think my laptop can support it.

I was using the README.debian for the 915resolution program; those were the instructions I followed.

Anyway, all is good now! ^^

---

### Post by zhelezov on 2006-07-07
hi, guys

i also have problems with inspiron e1405 but sadly they are starting at install time. dapper won't manage to set up the xserver, so i'm stuck. should i edit xorg.conf manually and would that be enough. i've already tried to set it up with the vesa driver and lower resolution, just to be able to proceed with the install, but it won't work.

did you encounter such a situation?

thanx
-vlad

edit: would i be more lucky if i install from 'alternate install cd' and try to fix the screen problems afterwards?!

---

### Post by saratoga on 2006-07-14
^^^ After a lot of playing with it, I realized the e1405 works correctly if you start the installer in safe mode or whatever its called.  That dumps you to the desktop in 1024*768, which looks bad, but works.

---

### Post by saratoga on 2006-07-14
Stupid question about the directions above.  

For the 915resolution script:

```
#! /bin/sh

/usr/bin/915resolution 38 1280 800
```

If I edited entry 5c to 1440*900 using 915resolution should I change it to:

```
#! /bin/sh

/usr/bin/915resolution 5c 1440 900
```

?  And shouldn't that command give a bitdepth?

Also, I can't get the update-rc.d to work:

```

update-rc.d 915resolution start 99 defaults
udate-rc.d: error expected runlevel [0-9S] (did you forget "."?)

```

Otherwise the method seems to work.  If I don't mind manually running 915resolution everytime i boot, I can get proper resolution.  But thats a little annoying :-|

---

### Post by dcohen on 2006-07-29
> **saratoga said:**
> Stupid question about the directions above.  

For the 915resolution script:

```
#! /bin/sh

/usr/bin/915resolution 38 1280 800
```

If I edited entry 5c to 1440*900 using 915resolution should I change it to:

```
#! /bin/sh

/usr/bin/915resolution 5c 1440 900
```

?  And shouldn't that command give a bitdepth?

Also, I can't get the update-rc.d to work:

```

update-rc.d 915resolution start 99 defaults
udate-rc.d: error expected runlevel [0-9S] (did you forget "."?)

```

Otherwise the method seems to work.  If I don't mind manually running 915resolution everytime i boot, I can get proper resolution.  But thats a little annoying :-|


anyone solved this?  I am having the same problem/the same questions except i have the 1440x900 screen.

---

### Post by glenda on 2006-08-03
> **fledylids said:**
> Thanks so much! Using that ubuntu.com guide, I got 1280x800 to work. I don't think I'll bother with 1440x900, I don't think my laptop can support it.


You should better figure out if your Dell realy applied with 1280x800. Mine has 1440x900, and I've spend some time to figure out why I couldn't set up hi resolution. The problem was in low video memory by default and some absent agp modules in kernel, that helps viodeadapter to borrow memory

---

### Post by muskyminxx on 2006-08-05
I am having the problem as well.  My screen looks like a 4:3 screen that has been stretched.  I have tried to do everything in the 915resolution instructions, but run into the same problem when I get to the
update-rc.d 915resolution start 99 defaults
step.  I do not know how to manually start 915resolution, so I have no idea if it is working at all.  Could anyone go into some detail if they have worked through this?

thanks

---

### Post by fsgpr on 2006-08-06
I had the same problem and spent many hours trying to solve it, here is what I learned and how I did it:

Script Files placed in /etc/init.d are all supposed to be run at startup (maybe if only registered somewhere else, not quite sure)

'sudo updatedb' updates a location database of all files on your computer
'locate 915resolution' will tell you where the 915Resolution file is

What finally fixed the problem was:
1st I deleted all 915resolution script files from /etc/init.d (I had several as I tried following many different instructions I found, thinking maybe different file names were conflicting)

I added the following line to /etc/init.d/procps.sh:
/usr/sbin/915resolution 5c 1280 800

I put it right after the line ### END INIT INFO.

Hope this helps someone, obviously I am still a Linux noob so I have no idea if this might cause any other consequences....

---

### Post by muskyminxx on 2006-08-07
It doesn't seem to break anything yet.  I followed your instructions and everything worked just right.  Thank you so much.

---

### Post by garethc on 2006-10-30
](*,)

---

