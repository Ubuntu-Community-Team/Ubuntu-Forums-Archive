---
title: "keyboard not found at installation"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by johnm on 2005-09-23
I have been trying to install Linux on my laptop, but I can't get further than the first screen after the installtion loads ("Choose language"). The keyboard (meaning the keyboard built into the laptop) hangs and I can't make any selections. If I attach an external USB keyboard it works fine, but then I lose the point of having the laptop of course.

The distribution I tried was Ubuntu Hoary Hedgehog (also tried Breezy with no luck). Then I tried Debian and the same thing happened again. However, one website mentioned a workaround where you type gibberish when the kernel loads, and this magically caused the Debian installer to recognize my keyboard. After installing and rebooting, the keyboard was yet again not recognized, so it obviously wasn't a good enough solution. Also, none of this worked with Ubuntu.

Is it the Linux kernel not recognizing my keyboard, and if so, is there any way at all to fix this?? It's a really annoying problem, because when I install Ubuntu with an external keyboard, everything else works fine - it's just this one tiny detail that's missing!

My laptop is a Packard Bell iGo 6581, about 3 years old. The keyboard seems to be of the model NEC Note Keyboard.

---

### Post by mlomker on 2005-09-23
> My laptop is a Packard Bell iGo 6581, about 3 years old. The keyboard seems to be of the model NEC Note Keyboard.

I did a few searches and there doesn't seem to be anyone running linux on the machine.  I did discover that there is a Windows driver for the keyboard, which is a very bad sign.  I'm left to assume that PB used a non-standard interface for the keyboard for some reason.

---

### Post by johnm on 2005-09-24
[QUOTE=mlomker]I did a few searches and there doesn't seem to be anyone running linux on the machine.  I did discover that there is a Windows driver for the keyboard, which is a very bad sign.  I'm left to assume that PB used a non-standard interface for the keyboard for some reason.[/QUOTE]

Other distributions such as Suse and Mandriva did not have this problem though, the keyboard worked fine there.

---

### Post by mlomker on 2005-09-24
> Other distributions such as Suse and Mandriva did not have this problem though, the keyboard worked fine there.

There must be kernel differences between Ubuntu and those other distros, then.  I guess the trick would be to load one of those versions, find out what the driver difference is, and then build a custom kernel with the proper module(s) built in.

Does Knoppix work (Debian-based bootcd)?  If so, then booting up on it and saving the output of **lsmod** would be a good starting point.  I've used that approach a couple times to come up with a module list before building my own kernel.

---

### Post by johnm on 2005-09-25
[QUOTE=mlomker]There must be kernel differences between Ubuntu and those other distros, then.  I guess the trick would be to load one of those versions, find out what the driver difference is, and then build a custom kernel with the proper module(s) built in.[/QUOTE]

Hmm... I'm still a newbie when it comes to Linux. How do I build my own kernel from a distro such as Suse, and then use this with Ubuntu? Is there a how-to anywhere that can help me solve this?

[QUOTE=mlomker]Does Knoppix work (Debian-based bootcd)?  If so, then booting up on it and saving the output of **lsmod** would be a good starting point.  I've used that approach a couple times to come up with a module list before building my own kernel.[/QUOTE]

Knoppix boots fine, but the keyboard doesn't work here either :(

---

### Post by mlomker on 2005-09-25
>  I'm still a newbie when it comes to Linux. How do I build my own kernel from a distro such as Suse, and then use this with Ubuntu? Is there a how-to anywhere that can help me solve this?

I'm not sure that'd help because your story sounds familiar (see below).

> 
Knoppix boots fine, but the keyboard doesn't work here either :(

Which leaves me to question--those Suse distros that you were running...were they based on a 2.4 kernel or 2.6 kernel.  I see a couple threads per day from people that cannot get their keyboards to work with the newer, 2.6 kernels.  

You've done the basic things like check that your system BIOS is the latest and checked NEC's website for any drivers?  If my suspicion is right then you'll have to run older distros based on 2.4 kernels or an external keyboard.

---

### Post by fordfan753 on 2005-09-25
[QUOTE=mlomker]I'm not sure that'd help because your story sounds familiar (see below).



Which leaves me to question--those Suse distros that you were running...were they based on a 2.4 kernel or 2.6 kernel.  I see a couple threads per day from people that cannot get their keyboards to work with the newer, 2.6 kernels.  

You've done the basic things like check that your system BIOS is the latest and checked NEC's website for any drivers?  If my suspicion is right then you'll have to run older distros based on 2.4 kernels or an external keyboard.[/QUOTE]

Debian Sarge anyone?
Actually, it should be possible to install Ubuntu with an external keyboard, and then install a 2.4 kernel, then reconfigure the xserver, and get it to work ok.

---

### Post by mlomker on 2005-09-25
> Actually, it should be possible to install Ubuntu with an external keyboard, and then install a 2.4 kernel, then reconfigure the xserver, and get it to work ok.

No, it isn't and many people have tried.  Ubuntu runs udev instead of devfs and that relies on the 2.6 hal.

The amount of hacking required would make the resulting machine 'not Ubuntu anymore.'

---

### Post by fordfan753 on 2005-09-25
Ah ok, I can see many potential problems as well...

---

