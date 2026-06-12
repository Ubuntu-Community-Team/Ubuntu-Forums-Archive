---
title: "screen brightness problems on 10.04"
date: 2010-06-06
forum: Hardware
---

### Post by mgiblets on 2010-06-06
I cannot adjust the screen brightness on my laptop a **benq joybook s35 **, my graphics card is **intel mobile 4. **Other posts seem to be related to the nvida graphics card and other laptops, although I've noticed this seems to be a recurring them among **v. 10.04 **users

---

### Post by jarviser on 2010-06-07
Are you saying there is no brightness control? in which case try adding Brightness Applet to the top panel using Right-click and Add to Panel.
Or try System, Preferences, Power Management and adjust it there.

Or are you saying you have a brightness control but it does not work?

---

### Post by mgiblets on 2010-06-07
I have the applet, and I can access the power management window. But when I move the slider, it doesn't do anything.

---

### Post by roydrager on 2010-07-20
I have the same problem on an Asus UL50AG-A2 laptop.  I tried with Ubuntu 10.04 32 bit, Kubuntu 10.04 32 bit, and Mint 9.   The slider in power manager or the applet has no effect.  

If you use the laptop function keys, there is a delay of up to several minutes before the screen brightness icon comes up.  It also has no effect.  But in Kubuntu, it suddenly made the screen totally black after a few minutes.

---

### Post by dtr1001 on 2010-07-20
same here with samsung n150 - applet exists but doesnt do anything

---

### Post by cherep on 2010-07-22
the same problem with Lenovo Z360, 10.04 64 bit

---

### Post by roydrager on 2010-08-06
Developer Kamal Mostafa has pushed out a fix for this problem for computers with the Intel i915 display chipset:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611")

To see if this is your chipset, 

```
lshw|more
```

and scroll down until you see Display.  It will say Intel i915 there.

Kamal's fix is pending inclusion in the main Ubuntu kernel updates, but you can get it here and install it yourself.  It seems to be running fine for me:

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri/+packages]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri/+packages")

The two files you need are most likely:

linux-headers-2.6.32-24-generic_2.6.32-24.39~kamal~i915bri1_amd64.deb (or i386.deb)
linux-image-2.6.32-24-generic_2.6.32-24.39~kamal~i915bri1_amd64.deb (or i386.deb)

Scroll down and do a Save As on those two files, then go to your save directory in console and run:

```
sudo dpkg i *kamal*.deb
```

Then reboot.

---

### Post by utilitytrack on 2010-08-06
to **mgiblets**, **cherep**, **dtr1001** and others

Look in here: [http://ubuntuforums.org/showthread.php?p=9677094#post9677094]("http://ubuntuforums.org/showthread.php?p=9677094#post9677094")

PS
Don't forget that only root can do this.

---

### Post by SuperMau on 2010-08-12
I had that problem with my Asus Laptop UX50V with bios 204. I upgraded to the  new BIOS 208 (Fixed bug that ALS has no function under dGPU mode on  Win7) and problem gone, screen brightness can be set with function keys.

---

### Post by tito_torrisi on 2010-08-31
The fix from Kamal [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611) solves this problem on many Notebooks (mine is a Lenovo Z360). 
Use his Launchpad ppa to install the fixed kernel.

Why does it take so long to push it into the main kernel? It's known since months, can't someone take some action here?

---

### Post by cherep on 2010-09-03
> **tito_torrisi said:**
> The fix from Kamal [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611) solves this problem on many Notebooks (mine is a Lenovo Z360). 
Use his Launchpad ppa to install the fixed kernel.

Why does it take so long to push it into the main kernel? It's known since months, can't someone take some action here?

**tito_torrisi**, I have Z360 as well. It helps me. But have you tried to suspend? The cooler becomes crazy just after 1 minute the laptop has gone back from a suspend regime. Processors do nothing, just about 5% of usage. Do you have any suggestions?

---

### Post by tito_torrisi on 2010-09-04
> **cherep said:**
> **tito_torrisi**, I have Z360 as well. It helps me. But have you tried to suspend? The cooler becomes crazy just after 1 minute the laptop has gone back from a suspend regime. Processors do nothing, just about 5% of usage. Do you have any suggestions?

Yes, suspend "works" with that kernel, but my fan also goes crazy, so I have to reboot after suspend. We should post that to the bug report on launchpad, kamal may correct that, at least he made a patch for suspend to work in the first place.
Another question, we can select the nvidia card in bios, and only when I do that, Ubuntu offers me to install the nvidia propriety drivers. But they don't work for me, and nouveau doesn't work too. I don't understand that graphics chip thing. Do you?

---

### Post by cherep on 2010-09-06
> **tito_torrisi said:**
> Yes, suspend "works" with that kernel, but my fan also goes crazy, so I have to reboot after suspend. We should post that to the bug report on launchpad, kamal may correct that, at least he made a patch for suspend to work in the first place.
Another question, we can select the nvidia card in bios, and only when I do that, Ubuntu offers me to install the nvidia propriety drivers. But they don't work for me, and nouveau doesn't work too. I don't understand that graphics chip thing. Do you?

First of all, I hope you are running ubuntu 64bit. I have never tried to install nvidia drivers. For my purposes it is totally fine to work with ubuntu pre-installed drivers. However, I would love to work with ubuntu which is installed correctly.

I have only the options "Optimus Graphic" vs. "UMA Graphic Only" to change in bios. Did you mean that? I'm running win7 as well (but I want to get rid of it). My observations tell that under "Optimus Graphic" win7 is running nvidia drivers, but ubuntu can't even go to the terminal mode "Crtl+Alt+F1". Under "UMA Graphic Only" win7 is using the intel graphic card, and ubuntu works fine (in terminal mode as well). Does it mean that I can change the card to use choosing appropriate option in bios? How can one check which driver he is using now in Ubuntu?

Another question: how to post the bug report on launchpad? I haven't tried this :)

---

### Post by cherep on 2010-09-11
by the way, does anyone know if Ubuntu supports Optimus Graphic Technology?

---

### Post by cherep on 2010-09-15
I guess the problem for all laptops with the Optimus Technology is that NVidia doesn't support it for Linux :( That's why it might be impossible to install any drivers for Nvidia Graphic cards.

[http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=3)

---

### Post by tito_torrisi on 2010-09-27
Fixed kernel available, check the launchpad bug report again!!

---

### Post by kamalmostafa on 2010-10-28
Hi folks-

Giving proper credit where its due...

My backlight brightness fix PPA at [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight) is composed primarily of the very fine work of Matthew Garrett (thanks Matthew!).  I'm responsible for the Ubuntu 10.04 backport and other bits to glue it together.

I am tracking the progress of the backlight brightness issue and the PPA in the Launchpad bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611) .

We appreciate everyone's patience while this new experimental brightness control method works its way through the process of getting integrated upstream and into Ubuntu proper.  This new method hasn't been integrated into the official kernels yet, since it is still being evaluated upstream.

 -Kamal Mostafa <kamal@canonical.com>

---

### Post by Valshar on 2010-10-29
EDIT:

Okay I finally got just intel_backlight showing, but brightness still goes all the way up or down when I use the hotkeys and breaks the session a little (clicking applications/places/systems shows that the button is selected as usual but the menu doesn't drop, among other things). I have to log out and in again to fix it. I don't mind much the optimus card not being supported, but I'd love to be able to control the brightness... this is a Samsung Q330.

Anything else I can try? =/

---

### Post by Valshar on 2010-10-31
bump to see if someone can help me with the new info

---

### Post by GaBe- on 2010-11-05
> **Valshar said:**
> EDIT:

Okay I finally got just intel_backlight showing, but brightness still goes all the way up or down when I use the hotkeys and breaks the session a little (clicking applications/places/systems shows that the button is selected as usual but the menu doesn't drop, among other things). I have to log out and in again to fix it. I don't mind much the optimus card not being supported, but I'd love to be able to control the brightness... this is a Samsung Q330.

Anything else I can try? =/

Same problem in here. Is there any way to disable those fn+up/down keys, because I accidentally push them all the time and that's really annoying.

---

### Post by Valshar on 2010-11-18
So I just realized that if I go to System > Power Management and if I use the "Set display brightness to:" button the brightness changes in real time, yet the Fn button still has the same problem. I'd imagine this is an easy fix from here? Just linking the Fn brightness key to wherever the power management option is... or something?

If someone could take a look at this would be awesome.

---

### Post by Dustin Bess on 2010-11-20
> **roydrager said:**
> Developer Kamal Mostafa has pushed out a fix for this problem for computers with the Intel i915 display chipset:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611")

To see if this is your chipset, 

```
lshw|more
```

and scroll down until you see Display.  It will say Intel i915 there.

Kamal's fix is pending inclusion in the main Ubuntu kernel updates, but you can get it here and install it yourself.  It seems to be running fine for me:

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri/+packages]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri/+packages")

The two files you need are most likely:

linux-headers-2.6.32-24-generic_2.6.32-24.39~kamal~i915bri1_amd64.deb (or i386.deb)
linux-image-2.6.32-24-generic_2.6.32-24.39~kamal~i915bri1_amd64.deb (or i386.deb)

Scroll down and do a Save As on those two files, then go to your save directory in console and run:

```
sudo dpkg i *kamal*.deb
```

Then reboot.
uhhm im having trouble with this i typed that code in and founf this under display

*-display:1 UNCLAIMED
so.....now what?

---

### Post by Valshar on 2010-11-27
Last update killed what I could do before, no brightness bar shows up on Power Management anymore... can't change brightness at all.

---

### Post by mesa lara on 2011-09-06
> **cherep said:**
> the same problem with Lenovo Z360, 10.04 64 bit
Hi Cherep,

I have Lenovo Z360, 32-bit, and had 11.04. I used to have brightness control problem and i often have to forced shutdown by pressing the power button. But today I update and upgrade the system and both problem are solved. I really happy with it. Thanks a lot to Ubuntu & launchpad team. This is great.

---

