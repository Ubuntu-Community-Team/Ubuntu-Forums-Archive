---
title: "More Synaptic Touchpads"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by xtacocorex on 2005-11-03
I think I've done pretty much everything I've read on the forums to get the scrolling to work on my Synaptic touchpad on my Dell Smartstep 250N.

Scrolling on the touchpad worked under Hoary, but after a harddrive failure, I decided to try Breezy.

A look at  says the following code (the >: is my prompt)
```

>: cat /var/log/Xorg.0.log | grep "synaptic" 
(EE) No Input driver matching `synaptics'

```

I have the drivers installed
```

>: locate synaptics | grep "X11R6"
/usr/X11R6/lib/modules/input/synaptics_drv.o

```

When I go the following:
```

>: synclient -l
Can't access shared memory area. SHMConfig disabled?

```

I also installed tpconfig, but I don't think that is affecting anything. I'm attaching my xorg.conf file for any assistance with that.

I do use a usb mouse when I'm at home, but I don't take it with me when I go on campus for school. Don't know if that's helpful or not.

Are there any update drivers out there that someone could send me?

Let me know if any other log output is needed.

Thanks for any and all help.

---

### Post by comfrey on 2005-11-05
Option "SHMConfig" "on"

in the pointer device section of you xorg.conf

then synclient should work.

---

### Post by xtacocorex on 2005-11-05
I have that set and I still get the error.

```

>: cat /etc/X11/xorg.conf | grep "SHM"
        Option          "SHMConfig"             "on"

```

I figure I'll just have to downgrade back to Hoary or wait 6 months for Dapper.

---

### Post by scubajeff on 2005-11-05
checkout this thread:

[http://ubuntuforums.org/showthread.php?t=78904]("http://ubuntuforums.org/showthread.php?t=78904")

---

### Post by xtacocorex on 2005-11-05
Scubajeff,

I found that thread after I had posted mine and went through and made the changes that I saw in there. Still didn't work. 

Do you know the thread that has the instructions to get Breezy to use the newer driver instead of the backdated one?

---

### Post by ispiked on 2005-11-15
xtacocorex, could you attach your xorg log file (probably in /var/log/Xorg.0.log)?

---

### Post by scubajeff on 2005-11-15
xtacocorex,

actually i'm using the latest synaptics driver 0.14.3, and i'm using breezy too. like ispiked said, please post your log file here so that we can start the debugging.

---

### Post by xtacocorex on 2005-11-15
I compiled 0.14.3 from source and it still didn't work, so here is the Xorg.0.log file.

---

### Post by beijingjj on 2005-11-16
I'm having variations on this same problem.

With my out of the box installation the touchpad scrolling worked fine.  "synclient -l" worked fine too.  However, any changes I made to the synaptics options in my xorg.conf had no effect at all.

Now I have installed the vanilla kernel from kernel.org.  I haven't changed anything in my xorg.conf.  Now when I issue "synclient -l" I also get 

```
Can't access shared memory area. SHMConfig disabled?
```

Does the out-of-the-box install not use the synaptics driver in the kernel and thus the difference?  I've had this same problem in other distros and have been dying to know what the reason is.  It's frustrating.

---

### Post by ispiked on 2005-11-16
xtacocorex, my suspicions were right. You're using a static build of xorg that does not allow module loading. I was having the same problem until someone in #xorg on freenode told me I was using a (static) debug build of xorg (package from synaptic) that did not allow module loading. Once I uninstalled that and went back to the normal xorg package all it well. :D

---

### Post by xtacocorex on 2005-11-17
I can see where that would cause problems.

Are the non-debug builds in the repos and if so are they names different?

---

### Post by ispiked on 2005-11-17
[QUOTE=xtacocorex]Are the non-debug builds in the repos and if so are they names different?[/QUOTE]Definitely. The only reason I had a debug build (xserver-xorg-dbg) was because I downloaded it when I was trying to get a useful stack from a Firefox crash. If you have xserver-xorg(-core) then you should be fine.

---

### Post by xtacocorex on 2005-11-17
I removed xserver-xorg-dbg and left xserver-xorg-core this morning before I went to campus for school, but during the restart of the xserver, it didn't work.

What method did you use to remove it and then reinstall everything?

---

### Post by ispiked on 2005-11-18
Yeah, the same thing happened to me. I really can't say what I did to fix it. I think I backed up my current xorg.conf, then ran the command mentioned in xorg.conf to restore it to the default (sudo dpkg-reconfigure -phigh xserver-xorg), then restarted X, then change it back to my old xorg.conf and it seemed to work.

---

### Post by beijingjj on 2005-11-20
[QUOTE=ispiked]xtacocorex, my suspicions were right. You're using a static build of xorg that does not allow module loading. I was having the same problem until someone in #xorg on freenode told me I was using a (static) debug build of xorg (package from synaptic) that did not allow module loading. Once I uninstalled that and went back to the normal xorg package all it well. :D[/QUOTE]

ispiked, 

Is going to the normal version of xorg as simple as preserving a copy of xorg.conf, uninstalling it from synaptics, and installing the normal version from source?

Thanks.

---

### Post by xtacocorex on 2005-11-20
Well, I got it to work.

I have this problem of getting bored while doing homework, which is usually programming, so I check out the forums here. I found one on speeding up the boot process, so I decided to try that. 

Definately got X to not start on boot automatically and when I that fixed, dialog boxes with input boxes had messed up fonts.

So I reinstalled linux twice that night, Fedora Core 4 first and then reinstalled Kubuntu on over that since I remembered why I didn't want Fedora. I screwed some stuff up in the process, my fault for choosing expert install, so I reinstalled Breezy this morning. 

xserver-xorg-dbg wasn't installed by default and I got sidescrolling.

Thanks for all the help.

---

### Post by beijingjj on 2005-11-21
[QUOTE=ispiked]xtacocorex, my suspicions were right. You're using a static build of xorg that does not allow module loading. I was having the same problem until someone in #xorg on freenode told me I was using a (static) debug build of xorg (package from synaptic) that did not allow module loading. Once I uninstalled that and went back to the normal xorg package all it well. :D[/QUOTE]

I thought about this but couldn't bring myself to remove the xorg deb package and install from source as I felt pretty sure this would hose my system.  Fortunately, it turned out not to be the problem.

Looking at my Xorg.0.log file I found out that my "evdev" module was not loading which is required for the synaptics_drv driver.  I added it to /etc/modules so that it would load before X starts.  Voila!  It works!

Now the only question I have is why is evdev not insmod-ing automatically with my new kernel?

---

