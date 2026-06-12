---
title: "Screen alignment with offical Nvidia driver"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Tatusmi on 2007-07-10
I have searched around on the forums and have been unable to find a solution to my problem.

I am running Ubuntu 7.04 with the latest, official Nvidia drivers (as supplied/enabled w/ Ubuntu) and a Samsung Syncmaster 193P+ LCD monitor (with no hardware buttons to align screen). 

My issue is that there is that the screen is off-center by about 1/4" to the right. I have had this problem before with SuSE and was able to solve using xvidtune. When I try to use xvidtune in Ubuntu to fix my alignment it says I have requested an invalid modeline.

Is there any way for me to center the screen? It is unbelievably annoying to have everything cut off by 1/4" on the right!

Thanks!

---

### Post by coffeecat on 2007-07-10
This is a common problem. I run three machines through a KVM switch and If I switch from one with an nvidia card running the proprietary 'nvidia' driver to the machine with an Intel graphics chipset (or vice versa) the image is invariably offset by a small amount. I even get this going from one distro using the 'nvidia' driver to another set up with the open-source 'nv' driver.

I've fiddled with modelines in the past and gave that up as a bad job. So what I do is simply to press the 'auto' button on the monitor. However....

> **Tatusmi said:**
> Samsung Syncmaster 193P+ LCD monitor (with no hardware buttons to align screen).

I've not come across a monitor with no control buttons. If there's not an 'auto' button on the thing, can you access some sort of autotune function somewhere within the on-screen menus? Most, if not all, flat-screen monitors and TV/monitors have this somewhere. Even my 32" flat-screen TV does, which came in handy when I tried that as a monitor for one of my machines.

---

### Post by Tatusmi on 2007-07-10
> **coffeecat said:**
> I've not come across a monitor with no control buttons. If there's not an 'auto' button on the thing, can you access some sort of autotune function somewhere within the on-screen menus? Most, if not all, flat-screen monitors and TV/monitors have this somewhere. Even my 32" flat-screen TV does, which came in handy when I tried that as a monitor for one of my machines.Unfortunately, this monitor only has one button, the on/off switch. There are no on-screen menus. It is all software to align it.

I am also running this through a KVM switch... my other box is a Windows XP machine with an ATI graphics card. The monitor is perfectly aligned in XP (after I used software to align it properly)... it was also originally off to the right by 1/4".

---

### Post by coffeecat on 2007-07-11
I see what you mean. I suppose the aligning software is Windows only. :roll: Another gotcha to watch out for when buying a monitor then. I'm sorry I can't be of any help - unless:

Would it be possible to run this software in Wine?

---

### Post by Tatusmi on 2007-07-11
Sorry, I should have been more clear... although I believe there is actual vendor software available to align the monitor, the "software" I have been using is the ATI Control Center included with the driver. I was hoping that there would be similar functionality with the Nvidia driver under Linux (I don't understand why there isn't).

On previous installs of SuSE I have been able to fix the problem using xvidtune... but xvidtune gives me an error now saying something to the effect of "the modeline you have requested is invalid".

---

### Post by Tatusmi on 2007-07-12
I have been fiddling around with modelines in /etc/X11/xorg.conf yet none of them seem to make any difference. It's as if that config file isn't being read.

Does anyone have any other suggestions?

---

