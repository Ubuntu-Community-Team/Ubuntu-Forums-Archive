---
title: "Problem with ATI Radeon HD Mobility 5145"
date: 2013-10-20
forum: Hardware
---

### Post by MEkXhkM on 2013-10-20
I have an Asus K52JB and my video card is ATI Radeon Mobility 5145. Just for some information i read here : [http://ubuntuforums.org/showthread.php?t=1678044](http://ubuntuforums.org/showthread.php?t=1678044) that the card is based on the 4500 series.

So if i just don't install nothing, in "System Details">"Details" it tells me that my graphics are "Gallium 0.4 on AMD RV710".

I've tried to install fglrx drivers and AMD site drivers too but always gives me some problem. 

On ubuntu 13.04 and 13.10 if i install these drivers, when i reboot the resolution is very bad and my unity and side bar doesnt show ( tried to reset unity, didn't work). 

So i moved on to ubuntu 12.04, since it is a LTS and is older, maybe it could work. It didn't. When i reboot, my unity and side bar shows, but my resolution is very low and on options there's no option to an higher resolution.

With the default "Gallium 0.4 on AMD RV710" i tried glxgears. It gives me 60fps. I don't know if it is good or no.

[COLOR=#000000]Thanks in advance,[/COLOR]

[COLOR=#000000]Edgar.[/COLOR]

---

### Post by MEkXhkM on 2013-10-20
Please, any help is welcome.

When i do **"lspci | grep VGA"** it shows me** "VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v]"**

---

### Post by Yellow Pasque on 2013-10-20
You can't install fglrx on anything newer than 12.04.1, nor do you need to.

> With the default "Gallium 0.4 on AMD RV710" i tried glxgears. It gives me 60fps. I don't know if it is good or no.
glxgears is not a benchmark. 60fps = 60Hz monitor (because video is synced to avoid tearing).

---

### Post by MEkXhkM on 2013-10-21
> **Temüjin said:**
> You can't install fglrx on anything newer than 12.04.1, nor do you need to.


glxgears is not a benchmark. 60fps = 60Hz monitor (because video is synced to avoid tearing).

So i don't need to install anything? I mean, my graphics are good, i don't have lag or anything. Tried a few games, so good so far. I am just intrigued for showing "gallium" instead of my graphic card.

---

### Post by Yellow Pasque on 2013-10-21
> So i don't need to install anything?
There's nothing to install. The legacy proprietary driver doesn't support modern versions of Ubuntu.

> I am just intrigued for showing "gallium" instead of my graphic card. 
Don't worry about it. I see the exact same thing on my RadeonHD 4550. Gallium3D is the name of the open-source 3D driver infrastructure. RV710 is the ATI codename of your card's chip.

---

### Post by MEkXhkM on 2013-10-21
Ok, thank you for your help ! ;)

---

### Post by MEkXhkM on 2013-11-05
Maybe i found the solution.

In this website: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) they say : "[COLOR=#000000][FONT=sans-serif]ATI/AMD initially dropped Catalyst support for these cards in the regular Catalyst 12-6. These cards are now supported with the later released Catalyst 13-1 legacy, but you MUST use a kernel <= 3.4 and Xserver <= 1.12. For example, you can use Catalyst 13-1 legacy if you're running Ubuntu 12.04 or Debian Squeeze/6.0. Open source support is good and 3D is still improving."

So if i downgrade kernel to 3.4 and Xserver to 1.12 and install catalyst 13.1 i'll be able to get my graphic cards properly.

It is possible to do downgrade? I'm on ubuntu 13.10. The only thing that is stopping me to totally migrate to ubuntu is this graphic issue.

Or should i just downgrade to ubuntu 12.04 as they say?[/FONT][/COLOR]

---

### Post by QIII on 2013-11-05
Hello!

I would *highly recommend **against** using that method!*

What you will end up with is effectively a broken installation, you may have trouble upgrading in the future, you may end up with package dependency issues and it is just a lot of work to go through when the open source Radeon driver has improved so much in the last year or two.

If you really want to use the ATI driver, then use a version of Ubuntu no later than 12.04.1  -- which is supported until 2017 -- with the legacy driver.

---

### Post by MEkXhkM on 2013-11-05
> **QIII said:**
> Hello!

I would *highly recommend **against** using that method!*

What you will end up with is effectively a broken installation, you may have trouble upgrading in the future, you may end up with package dependency issues and it is just a lot of work to go through when the open source Radeon driver has improved so much in the last year or two.

If you really want to use the ATI driver, then use a version of Ubuntu no later than 12.04.1  -- which is supported until 2017 -- with the legacy driver.

Thank you for your advice ;) Yeah, the open source driver is quite good, but is not good enough to run, for example, L4d2.

I'm taking your advice and installing 12.04.1 or earlier. I know that ubuntu 12.04 has kernel 3.2 but what about Xserver? It can't be more than 1.12. I've google it, but found nothing.

---

### Post by QIII on 2013-11-05
You're good with 12.04.1.  Just don't try 12.04.2.  That's where X Server and the kernel will refuse to cooperate with you.

---

### Post by MEkXhkM on 2013-11-05
Thanks ! Downloading 12.04.0 just to be safe.

---

### Post by MEkXhkM on 2013-11-05
It worked :popcorn: ! Installed legacy by here [https://launchpad.net/~makson96/+archive/fglrx/+index?batch=75&direction=backwards&memo=75](https://launchpad.net/~makson96/+archive/fglrx/+index?batch=75&direction=backwards&memo=75).

---

