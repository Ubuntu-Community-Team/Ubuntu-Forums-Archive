---
title: "Having display issues Please help"
date: 2011-09-01
forum: Hardware
---

### Post by Evonus on 2011-09-01
Hello,

I have a Lenovo W520 thinkpad.

I'm trying to run dual monitors and I've read these two threads:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

But after running this command "sudo apt-get --purge remove xserver-xorg-video-nouveau" now I no longer even have a display when I boot up normally. 

I'm running in low graphics recovery mode right now. 

Using the additional drivers menu, I did install the Nvidia accelerated graphics driver, but its telling me that the driver is installed but not currently in use.

When I try to open Nvidia Xserver settings, I get this error message : 

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I googled it and got this: [http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu](http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu)

but after running through the steps I find that it doesn't help me.

Can someone please help me!

---

### Post by realzippy on 2011-09-01
Isn't that an Optimus laptop?

---

### Post by Evonus on 2011-09-01
> **realzippy said:**
> Isn't that an Optimus laptop?

I'm honestly not sure.

How would I find that out, and what would that change?

---

### Post by realzippy on 2011-09-01
I am too lazy to tell,since there are a bunch of threads about nvidia
optimus technology related not-working-nvidia-linux-drivers....

Run this:

```
lspci |grep VGA
```

if you see 2 devices (intel and nvidia),you very likely have an optimus laptop.Then read this:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by Evonus on 2011-09-01
> **realzippy said:**
> I am too lazy to tell,since there are a bunch of threads about nvidia
optimus technology related not-working-nvidia-linux-drivers....

Run this:

```
lspci |grep VGA
```

if you see 2 devices (intel and nvidia),you very likely have an optimus laptop.Then read this:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

You were right. I went into the bios and killed that option so now I'm just running off of the nvidia card.

Thanks a lot for you help!

---

### Post by realzippy on 2011-09-01
Luck you have a switch in the BIOS.I don't...
Set thread as solved please (ThreadTools)
Have fun
zippy

---

