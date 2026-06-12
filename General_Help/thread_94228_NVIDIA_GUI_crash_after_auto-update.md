---
title: "NVIDIA GUI crash after auto-update"
date: 2005-11-23
forum: General Help
---

### Post by tidemann on 2005-11-23
Today I noticed in the top-right corner that there was several important upgrades. These includes the kernel source, tree, headers, and the NVIDIA legacy driver. I then downloaded and successfully installed the patches. Everything seemed to work flawlessly. Then i rebooted. The GDM wouldn't load, and I got an NVIDIA error message at startup which caused the GUI to crash. I am forced to use lynx to post this, which is a pain in itself. Does anyone know how I can fix this, and maybe restore my old settings? I am pretty new to Linux but backed-up using a one-line-command when I installed some other software a week ago... maybe I could pull it out somehow? I have a lot of important stuff on this machine and I would hate to reinstall. It's also alarming that my system crashed when I used the autoupdate... I have tried to remove and reinstall the nvidia-glx-legacy driver with apt-get from the commandline without success. PLEASE HELP!

---

### Post by Neobuntu on 2005-11-23
Me too! I'd like to help get this resolved quickly. That's what ubuntu is best at.

Never should an update render (X) un loadable.

My situation:

I have a Nvidia legacy card that was running TORCS (great racing) and other direct access 3D (DRI) games just fine (for a $12 card.) 

I had installed Nvidia using ubuntu online easy commands but the thing is, one forgets all these steps even though it's world easier than it used to be.

I have been impressed that one does not need to recomplie a kernel (or anything else) for Nvidia and NDISwrapper (option to use an XP 802.11G WiFi driver in ubuntu.) Compiling isn't that hard but takes a lot of time.

Also, I'm impresses to utilize a pre-compiled K7 optimised kernel that matches all these other needed drivers.

So as the first poster, I was impressed to see my select choices being updated. That is, the K7 Kernel and Nvidia(legacy.) 

What I did: Currently I'm back at the 9th redition of this K7 Kernel and it's driver module that were working simply by delecting it in my GRUB startup menu before timeout. I had set this timeout to 1 second because I had the one and only Kernel I needed working and with matching drivers. Thus, I had to know how to go back into and edit /boot/grub/menu.lst to change the time out (8 seconds) to see the new and old kernel choices. I think many newbies will miss the GRUB menu and not know what to do.

I must assume the was a problem with my working version 9 (of the K7 kernel that just updated yesterday I think) and that the now broken version 10 was ironically suposed to fix. I welcome a speedy and working version 11 if nessary.

I hope that help others "punt" and go back to version 9 until this is fixed.

My question is how to fix? I tried running sudo "dpkg-reconfigure xserver-xorg"  and going with the defaults but I had to remove setting over 1024x768 in order to get X to start. So X is fixed but DRI and the Wifi (NDISwrapper) is broken. Obvously these need to be set up for the new Kernel (I think.) Now we are far away from an easy ubuntu. 

Is there an easy fix we can post? Do we have to wait for an update fix? How do I know what these automatic (K7) kernal updates are supoosed to fix?

If new set up is indeed required with my hardware set, I sure would like a warning and some included direction on update.

I thank you in advance for quick responses.

---

### Post by Neobuntu on 2005-11-23
OK, now I'm loading not only the ... 

linux-restricted-modules-2.6.12-10-k7 
(done in auto update)

but also ...

linux-restricted-modules-2.6.12-10-k7-nvidia-legacy
(not done with auto update)

So with X not loading one could perhaps...

sudo apt-get install linux-restricted-modules-2.6.12-10-k7-nvidia-legacy

I will let you know if it worked. I expect it will fix X, Nvida 3D and Wireless.

**Edit** It works! Of course I had to "refiddle" with X and the NDISwrapper to making sure to restart (just reboot) and then had a slow hardrive check at a frustrating time but hey, all is well. DO NOT MESS WITH THEM.

I feel sorry for the newbies though. Hopfully this will help.

So did a dependacy (the restricted and for the Nvidia "legacy") just get left out? How can we fix this? It all worked on the last Kernel update.

I understand the freaking plantets have to align but ubuntu has mitigated this better than any other I've seen (and no compiling thank you). 

It's my hope that this glitch get put in the past today, because no user should have figure out...

My SOLUTION

sudo apt-get install linux-restricted-modules-2.6.12-10-k7-nvidia-legacy

From a kernel with working internet and when X doesn't start after a (really nice easy) auto update.

---

### Post by Neobuntu on 2005-11-23
Looks like I'm having problems with my cheap (unsuported) WiFi card. It's great that ubuntu set up the WiFi to work automatically but this one is happier with the XP driver via NDISWrapper.

I can only guess the new kernel is trying to use a native driver instead of the ndis I installed.

Now, I have to remember how I did that and if there are conflicting wifi driver modules.

Anyone know what to do?

---

### Post by tidemann on 2005-11-24
[QUOTE=Neobuntu]OK, now I'm loading not only the ... 

linux-restricted-modules-2.6.12-10-k7 
(done in auto update)

but also ...

linux-restricted-modules-2.6.12-10-k7-nvidia-legacy
(not done with auto update)

So with X not loading one could perhaps...

sudo apt-get install linux-restricted-modules-2.6.12-10-k7-nvidia-legacy

I will let you know if it worked. I expect it will fix X, Nvida 3D and Wireless.

**Edit** It works! Of course I had to "refiddle" with X and the NDISwrapper to making sure to restart (just reboot) and then had a slow hardrive check at a frustrating time but hey, all is well. DO NOT MESS WITH THEM.

I feel sorry for the newbies though. Hopfully this will help.

So did a dependacy (the restricted and for the Nvidia "legacy") just get left out? How can we fix this? It all worked on the last Kernel update.

I understand the freaking plantets have to align but ubuntu has mitigated this better than any other I've seen (and no compiling thank you). 

It's my hope that this glitch get put in the past today, because no user should have figure out...

My SOLUTION

sudo apt-get install linux-restricted-modules-2.6.12-10-k7-nvidia-legacy

From a kernel with working internet and when X doesn't start after a (really nice easy) auto update.[/QUOTE]


Thank you so much!! It now loaded into X :) Although my screen resolution is messed up. It is now using 1024x768, when it should be 1200x800 (laptop) but it's not an option in "Screen Resolutions". These are the only available options:

1024x768
800x600
640x480
832x624

What do I need to fix?

---

### Post by Sebby on 2005-11-24
[QUOTE=tidemann]What do I need to fix?[/QUOTE]
The way I do it is:

```
sudo gedit /etc/X11/xorg.conf
```

Add a modeline under the monitor section. Mine looks like this:

```
	Modeline 	"1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
```

There may be an easier way... :p

---

### Post by tidemann on 2005-11-24
[QUOTE=Sebby]The way I do it is:

```
sudo gedit /etc/X11/xorg.conf
```

Add a modeline under the monitor section. Mine looks like this:

```
	Modeline 	"1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
```

There may be an easier way... :p[/QUOTE]

did that and rebooted but still no 1280x800 resolution available.... anything I might by missing?

---

### Post by Neobuntu on 2005-11-25
Hey Y'all! Happy Thanksgiving!

I thank you for the thank you. At a time when we see Ubuntu is best but everyone still looks at you like your a Three headed Linux geek, it's nice to know my post helped.

#1 I simply renamed my old backup xorg.conf file because ubuntu leaves nice dated ones to restore in case of situation like this. This put my X back to maximal monitor settings before I (mistakenly) reconfigured xserver-xorg.

#2 I'm my case, I also removed the "sudo rmmod acx_pci" Ubuntu auto (native) WiFi driver so as not to conflict with my ndis wrapped XP (updated online) driver. I other words, I use a different driver so I had to turn off the stock (and native) one. Now Internet access doesn't hang. I'll be rebooting to check for permenancy.

I'm thankful for sharing and Ubuntu.

---

### Post by tidemann on 2005-11-26
I figured it out at last... now my system is restored to the proper graphical settings :)

---

### Post by Neobuntu on 2005-11-26
As a follow up I do infact need to use "sudo rmmod acx_pci" after booting up to stop the ubuntu acx_pci native driver because it doesn't registar 100% signal strength like the NDISwrapped XP driver does. The XP driver doesn't fail after a few minutes.

Note: This closed type hardware is dirty monopolist pool and our politcal leaders and law makers are to stupid to see the anti-competitive nose in front of thier face. But I mean that in a nice way. :) The thing to do is get a Linux approved WiFi card. One where the manufacture isn't a nazi hiding how the thing works.

---

