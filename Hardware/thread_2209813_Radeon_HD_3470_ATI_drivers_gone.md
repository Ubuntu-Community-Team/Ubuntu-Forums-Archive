---
title: "Radeon HD 3470: ATI drivers gone"
date: 2014-03-07
forum: Hardware
---

### Post by hojjat on 2014-03-07
I upgraded my Ubuntu 12.04 and somehow all ATI drivers are gone. It has caused Unity to load in 2D mode, and for compiz to not load at all (I am on metacity now :(). Here is the relevant information about my driver.

> 
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620 PRO [Radeon HD 3470]
$ sudo  /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system


I have tried googling but I can't seem to find a way to enable ATI drivers on my machine again; or get compiz to work (which is the ultimate goal). Any advice is highly appreciated.

---

### Post by QIII on 2014-03-07
Hello!

By "upgrade", do you mean that you are now using 12.04.2 or greater?

If so, your graphics card will not work because ATI has dropped Linux driver support for that card for more recent versions of Linux, which includes Ubuntu 12.04.2 or later.  All HD 2000 to HD 4000 cards are now supported only by a legacy driver that will not work with the X Server used by Ubuntu 12.04.2 and beyond.  As a result, even if you had previously installed the driver from the Ubuntu repo, it will not be reinstalled on upgrade to 12.04.2 or later.

This is ATI's decision and there is nothing the Linux community can do about it.

You have two choices:  Use the open source driver (as you are now) or reinstall 12.04.1 or prior and use the legacy ATI driver.  I would recommend very strongly against using any of the hack methods of downgrading certain parts of 12.04.2 or beyond to get the card to work.

Best wishes.

---

### Post by hojjat on 2014-03-07
Thanks for the quick response. By upgrade, I mean running *apt-get upgrade*. I was, and still am, using 12.04 LTS.

How do I use open source drivers then? And will that make compiz work again (in the slow way that it did before)?

---

### Post by QIII on 2014-03-07
There have been several "point releases" of 12.04 LTS. If you have done a dist-upgrade recently, it is likely that you have a newer kernel that is unsupported by ATI.  For 12.04.2 and beyond, ATI does not support your card.  Have you installed a newer Hardware Enablement Stack?

To get better support with the open source driver, you might want to try

```

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
```

---

### Post by Bashing-om on 2014-03-07
hojjat; Hi !

The point is that as you have an old no-longer-supported video card . Then in order to utilize a fglrx driver you must be running version 12.04.[color=red]1[/color]; Which is still a LTS version, and will have continued support until 2017.
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.[color=red]2[/color], the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


There are options
[INDENT][INDENT]but they are slim
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2014-03-07
You may be able to roll back to previous kernel/X.
What kernel are you running?
```
uname -a
```

---

### Post by hojjat on 2014-03-07
Right now using 3.2.0-60-generic

---

### Post by hojjat on 2014-03-07
Okay, I guess I messed up with too many configs. Now when I restart my computer, the login screen is shown in 800x600 (everything is HUGE!) and after I login, the only resolution option I see is 800 x 600. Any idea how I can fix that?

---

### Post by hojjat on 2014-03-07
After unchecking the "Mirror dispalys" option, now I see one of the mintors at the usual resolution, but the other one is still stuck at 800x600. I'm still unable to solve that problem.

---

### Post by hojjat on 2014-03-07
I finally managed to find the correct ModeLine from Xorg.0.log and then add it and assign it to the correct viewport using xrandr program.

---

### Post by Bashing-om on 2014-03-07
hojjat; Hey,

You do good work !

Thanks for providing your solution or the community !

All look'n good
[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by TBeholder on 2014-04-12
> **Bashing-om said:**
> The point is that as you have an old no-longer-supported video card . Then in order to utilize a fglrx driver you must be running version 12.04.[color=red]1[/color]; Which is still a LTS version, and will have continued support until 2017.
It's possible to run legacy FGLRX on 13.10 - but this requires some jumping through hoops. See "[AMD Legacy drivers on 13.10](http://ubuntuforums.org/showthread.php?t=2181190)" thread.

---

