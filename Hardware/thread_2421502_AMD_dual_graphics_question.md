---
title: "AMD dual graphics question"
date: 2019-06-22
forum: Hardware
---

### Post by Val87 on 2019-06-22
Hey All,
Its been a long time! :)

I have an asus laptop that has 2 graphics, the integrated chip of Vega 8 running of Ryzen 5 3550H processor and a dedicated GPU of RX 560X.

Right now on windows, there is a hybrid setup with Radeon Settings deciding when to run the deciated GPU depending on the load and gaming. 

Now, that gaming is more available via Steam, before trying Ubuntu on that machine, i would like to ask people who are smarter than me, will this run on the latest Ubuntu LTS?  Will the "night light" work? (currently bugged on windows 1903). 

Am I going to run to a bunch of problems with installing or will the both graphics chips work out of the box? 
My concern is that either only one will work or both won't work. The hybrid setup that I have on Windows is fairly good, but Microsoft has been pissing me off lately. 

And also: [https://www.youtube.com/watch?v=Co6FePZoNgE](https://www.youtube.com/watch?v=Co6FePZoNgE) this has inspired me a little :D

---

### Post by satnrzn on 2019-06-22
I used laptops with a long time ago. And always - only AMD. But nevertheless, I do not remember any problems with graphics. True, the last thing I used was Kubunt 14.04. With beta. Well, and iron, respectively, of those times ...
Driver - proprietary only. Naturally, only one chip worked (processor video, not discrete). Yes, and I preferred laptops with the ability to completely disable the discrete video card in the BIOS. Less problems.
At that time, I read that it was possible to run games separately, on a discrete one. But, only on a free video driver. ))) I do not think that in AMD something has changed much since the days of the Catalyst. ))
Here is my personal opinion - if the discrete is so important for games. That is better dualbut with Windows.

---

### Post by Val87 on 2019-06-22
Oh boy, thanks for the reply! It will take me a while to figure out what was just said! :D I know amd has this for Drivers: 

[https://www.amd.com/en/support/kb/faq/gpu-635](https://www.amd.com/en/support/kb/faq/gpu-635) not sure what it is. But i remember that i struggled before with installations of tar.gz

Also this: [https://www.amd.com/en/support/kb/release-notes/rn-prorad-lin-18-20](https://www.amd.com/en/support/kb/release-notes/rn-prorad-lin-18-20)

---

### Post by CatKiller on 2019-06-22
I've never tried it, but the infrastructure for switchable graphics is called Prime. Both your graphics devices use exactly the same driver, so it should be painless. Everything you need should already be provided.

---

### Post by CatKiller on 2019-06-22
> **satnrzn said:**
> I do not think that in AMD something has changed much since the days of the CatalystIt has absolutely completely changed. Catalyst and fglrx were discarded, and AMD threw their weight entirely behind the open driver (amdgpu). The proprietary driver they have now is exactly the same as the open source driver, except for some compiler stuff. If you're doing GPGPU computation, or if you absolutely definitely need to use the same shaders on Linux as Windows, then you might need the proprietary AMD driver. Otherwise, stick with the open source one.

---

### Post by Val87 on 2019-06-22
&#1054;&#1090;&#1083;&#1080;&#1095;&#1085;&#1086; &#1089;&#1084;&#1086;&#1075;&#1091;, &#1091;&#1078; &#1087;&#1086;&#1074;&#1077;&#1088;&#1100;!
Wasn't sarcastic, was basically saying that I am waaay to behind on all things Linux and have a lot of catching up to do, plus i wasn't that advanced to begin with, basics, as mentioned before even tar.gz installations gave me headaches. :)

---

### Post by CatKiller on 2019-06-22
> **satnrzn said:**
> I do not need. Already years with five Nvidia. And laptops - for a long time do not use.

The "if you..." part wasn't directed at you, specifically, but readers in general choosing between amdgpu (open) and amdgpu-pro (proprietary).

The point was that there *was* a massive shift in the way AMD handled their Linux drivers in the 2014-2015 timeframe.

---

### Post by Val87 on 2019-06-22
> **CatKiller said:**
> It has absolutely completely changed. Catalyst and fglrx were discarded, and AMD threw their weight entirely behind the open driver (amdgpu). The proprietary driver they have now is exactly the same as the open source driver, except for some compiler stuff. If you're doing GPGPU computation, or if you absolutely definitely need to use the same shaders on Linux as Windows, then you might need the proprietary AMD driver. Otherwise, stick with the open source one.

So i can basically install it with a sudo command and it will support both GPU's and manage them based on the load?

---

### Post by CatKiller on 2019-06-22
> **Val87 said:**
> So i can basically install it with a sudo command and it will support both GPU's and manage them based on the load?

You don't need to install anything if you're using recent versions of the kernel and Mesa.

> **CatKiller said:**
> I've never tried it

You direct which way you want the assignments to go with **xrandr**, and choose which applications use which card with the **DRI_PRIME=1** environment variable.

The [Arch wiki]("https://wiki.archlinux.org/index.php/PRIME") has more details.

---

### Post by Val87 on 2019-06-22
> **CatKiller said:**
> You don't need to install anything if you're using recent versions of the kernel and Mesa.



You direct which way you want the assignments to go with **xrandr**, and choose which applications use which card with the **DRI_PRIME=1** environment variable.

The [Arch wiki]("https://wiki.archlinux.org/index.php/PRIME") has more details.

So if I go this rout (see image attached)

Will Ubuntu then decide itself witch adapter is running when based on the load or wil i need to switch manually? As that process seems to be fairly eeasy to follow.
Also, what about keyboard backlight and Radeon Sync? And RGB mouse and headsets, mouse being the asus mouse and headset from Corsair? Will all of this somehow work but with no config?

Sorry for all the questions, i want to get homework done before I do anything, as i made that mistake before and suffered! :D

---

### Post by CatKiller on 2019-06-22
> **Val87 said:**
> Will Ubuntu then decide itself witch adapter is running when based on the load or wil i need to switch manually? As that process seems to be fairly eeasy to follow.

> **CatKiller said:**
> I've never tried it

You'll need to specify for yourself which applications you want to be using which graphics device.

> Also, what about keyboard backlight and Radeon Sync? And RGB mouse and headsets, mouse being the asus mouse and headset from Corsair? Will all of this somehow work but with no config?

No.

The hardware manufacturers can't decide on an RGB specification for their devices, so their solution on Windows is to have you run a bajillion bits of software to control each device. They could do the same on Linux, and it would work, but they haven't bothered to make their widgets available on Linux.

On the reverse-engineering side, no one else has settled on a specification that is compatible with every manufacturer's baubles and that behaves in a sensible way. Some people have done some work that makes the baubles they personally have work.

In all likelihood you won't be able to control any of your RGB things from Linux.

---

### Post by Val87 on 2019-06-22
> **CatKiller said:**
> You'll need to specify for yourself which applications you want to be using which graphics device.



No.

The hardware manufacturers can't decide on an RGB specification for their devices, so their solution on Windows is to have you run a bajillion bits of software to control each device. They could do the same on Linux, and it would work, but they haven't bothered to make their widgets available on Linux.

On the reverse-engineering side, no one else has settled on a specification that is compatible with every manufacturer's baubles and that behaves in a sensible way. Some people have done some work that makes the baubles they personally have work.

In all likelihood you won't be able to control any of your RGB things from Linux.

Damn it! And I got so exited after watching this: [https://www.youtube.com/watch?v=Co6FePZoNgE](https://www.youtube.com/watch?v=Co6FePZoNgE) 
They are talking about two other distros there: Pop!_OS & Manjaro one of them being an Ubuntu clone. Apparently they are ahead of ubuntu on hardware config, would they be viable and less "messy"?

---

### Post by Val87 on 2019-06-22
Thanks for the answer, and your effort! And what about Steam? Look here at this videos, it is in English, but there they show what they do for the minutes from the 5th so as not to listen to all the prelude, everything seems to be pulling nicely? Or am I just a noob? There they went Skyrim without native support for Linux and even on good graphics?

---

### Post by wildmanne39 on 2019-06-22
Hello, you are posting in an English only forum, please translate all your posts into English for the good of the whole community, I looked and did not find a Sub-forum in your Language that you can post in on this forum, if you can find one you are more then welcome to post in your Native Language in that sub-forum.

Thanks!

---

### Post by QIII on 2019-06-23
For those of you who may be confused by this thread:  some posts, written in another language, have been removed due to their rude and off-color nature.  Continuity has suffered, but we want the OP to have a chance at some support.

---

### Post by Yellow Pasque on 2019-06-23
Give output of:
```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

If all is well, you can run programs on the discrete GPU using DRI_PRIME as ^above.
```
DRI_PRIME=1 nameofprogram
```

---

