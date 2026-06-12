---
title: "ubuntu-gnome Bamboo Capture doesn't work"
date: 2013-07-16
forum: Hardware
---

### Post by Vinca on 2013-07-16
Hello,

My bamboo capture doesn't work on 13.04.  Worked fine on 12.10, after some great setup help by favux.

Shows up in lsusb
does not show in xsetwacom
does not show in xinput

I've tried kubuntu, ubuntu, and ubuntu-gnome.  Same problem everywhere.

Thanks for your help! I wish I could figure this out...

---

### Post by Favux on 2013-07-16
Hi Vinca,

> Bus 002 Device 006: ID 056a:00de Wacom Co., Ltd 
I think nwillis is dealing to something specific to the Intuos5 and if so it shouldn't affect your BambooPT.  Although it is strange yours is not working on multiple different, I assume Raring (13.04), releases.  So hmm.

Why don't you make sure the wacom kernel module is auto-loading:
```
lsmod | grep wacom
```

---

### Post by Vinca on 2013-07-16
All 13.04.

Seems kernel module isn't loading, doesn't show up in lsmod. I have all the packages...

---

### Post by Favux on 2013-07-16
Alright, the you want to add **wacom** to the end of the list of drivers/modules (probably 1 to 3 of them in there already) in **/etc/modules** and reboot.
```
gksudo gedit /etc/modules
```

---

### Post by Vinca on 2013-07-16
didn't work.  but 
```
insmod wacom
``` says that it can't find module wacom

Would that be the same problem? /etc/modules was empty already except for comments at the top, I just added wacom, but did not work.

```
modprobe wacom
``` also says no such module...

---

### Post by Favux on 2013-07-16
Please show me the contents of your /etc/modules, i.e. navigate to it in Nautilus and open it with gedit.

Another thing you can do is navigate to System Files, i.e. /, and then go into /boot.  In boot you should see your current kernel's (uname -r) config file.  Example:  config-3.2.0-49-generic.  Open that in gedit and do a search/find on 'wacom'.  You should see a line like:
```
CONFIG_TABLET_USB_WACOM=m
```
That means build the wacom kernel driver as a module as opposed to a built-in.  Is it there?

And/or check in e.g. /lib/modules/3.2.0-49-generic/kernel/drivers/input/tablet (using your current kernel) for wacom.ko.

---

### Post by Vinca on 2013-07-16
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

wacom
```

my boot folder is empty.  It could be because I'm on a chromebox, but the ubuntu on here is native...

---

### Post by Favux on 2013-07-16
Ah, the fact that you are running Chrome OS is sort of an important detail.

The wacom driver/module doesn't appear to be rolled in your chrome kernel (uname -r).  Have run into that before:
[http://ubuntuforums.org/showthread.php?t=2126969](http://ubuntuforums.org/showthread.php?t=2126969)
[http://ubuntuforums.org/showthread.php?t=2092166](http://ubuntuforums.org/showthread.php?t=2092166)

So you have to roll your own Chrome kernel where the kernel config specifies building the wacom module.  Now someone posted fairly recently on a thread I was on that a friend did that for them and they had their Wacom tablet working on Chrome.  They had some xsetwacom problems though which is what they were asking about I think.  I don't remember where that was.  Maybe I can find it.  I'm thinking your best shot unless you're a kernel guru is see if they would post the kernel somewhere to download.  Although not sure how generic the Chrome kernels are because Chrome is on different hardware right?

---

### Post by Vinca on 2013-07-16
[http://ml.reddit.com/r/chrubuntu/comments/1e7gjs/i_need_help_compiling_kernel_modules_eg/](http://ml.reddit.com/r/chrubuntu/comments/1e7gjs/i_need_help_compiling_kernel_modules_eg/)

the first comment has some instructions.  Seems simple enough.  I've done some android kernel stuff... we'll see what happens. I'm just not clear at which step I add the wacom kernel module? I can't even find where the module is located in my system??

---

### Post by Favux on 2013-07-16
The script looks promising if it works it should make things a lot easier.  No idea where chrome puts modules but it likely has a location somewhere.  Doubt it does all drivers as built-ins.

---

### Post by Vinca on 2013-07-16
I'm running ubuntu, not chrome OS.  It's just on a chromebox with some weird kernel stuff going on.  Those instructions on reddit were for ubuntu.  

I just don't know where to look to see the wacom kernel module, and I don't know how to make sure it gets included when I build the kernel?

---

### Post by Favux on 2013-07-16
Oh.  Well it should be in /lib/modules/your kernel/etc like I showed.

If you have the kernel headers with the kernel then you should be able to compile input-wacom to get a wacom.ko:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=110304](http://forums.linuxmint.com/viewtopic.php?f=42&t=110304)

What does the kernel call itself when you run?
```
uname -r
```

---

### Post by Vinca on 2013-07-16
I just ./configure'd input-wacom-0.18.0 and now I don't know which wacom.ko to put into my modules directory.

Should I use the 2.6.30, 2.6.36, 2.6.38, or 3.7?

Thanks

Vinca

---

### Post by Favux on 2013-07-16
You still haven't told me your kernel version.  Besides only one of the folders should have a newly compiled wacom.ko.

---

### Post by Vinca on 2013-07-16
It was 3.4.0 like the other chrome guy.  

I realized that just now, only one of them had an output wacom.ko.  I copied it into my input/tablet folder and BAM

Perfect wacom support, 100% xsetwacom functionality (from what I can tell)

Amazing! Thanks for your help!

Vinca

---

### Post by Favux on 2013-07-17
Outstanding!  :)  Nice work.

With the 3.4 kernel I'm guessing the wacom.ko was in the 2.6.38 folder.  Correct?

---

### Post by Vinca on 2013-07-17
yep, good guess.

I'm proud of myself, I like kernel-y stuff now :)

---

