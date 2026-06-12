---
title: "HP Pavilion dv7 does not boot after upgrade to 11.04"
date: 2011-04-29
forum: Hardware
---

### Post by jap1968 on 2011-04-29
I upgraded my hp-dv7 laptop to Ubuntu 11.04

First time I booted the computer after the upgrade, everything seemed to be OK.

After that, I am unable to start again. The system starts loading but suddenly the screen gets powered off. The system is running but the screen is off (not only black screen, but fully powered off).

I suspect it can be some issue related to hybrid graphics (intel HD video + ATI graphics). Maybe the system is powering off the wrong video card? :confused:

Anybody out there experiencing similar problems?

---

### Post by lcmikerinos on 2011-05-01
Exactly the same happened to me. Ubuntu 11.04 installed in HP pavilion dv6, run ok first time and after that unable to boot, the screen goes black. Any idea??

---

### Post by Dario Zamuner on 2011-05-01
I had the same problem, but it seems to be resolved installing the proprietary driver for the ati video card.

System -> Administration -> Additional Drivers 
Activate the ATI/AMD Proprietary FGLRX graphics driver

The installation for me didn't go well, so I opened Synaptic, searched for fglrx, and reinstalled the packages already marked as installed.

After a reboot the proprietary driver appeared to be activated.

Since then Ubuntu doesn't freeze anymore at reboot :D

---

### Post by lcmikerinos on 2011-05-01
Thanks Dario, one question did you install the propietary drivers after installing 11.04 or previously in the 10.10?

---

### Post by Dario Zamuner on 2011-05-01
> **lcmikerinos said:**
> Thanks Dario, one question did you install the propietary drivers after installing 11.04 or previously in the 10.10?

I installed the drivers on 11.04. Previously I used the generics.

BTW these drivers fix the boot problem, but after some tests I have some other issues.

[SIZE=2]**Before, with generics drivers**[/SIZE]
[COLOR=Red] [SIZE=4]-[/SIZE] [/COLOR]Ubuntu 11.04 with kernel 2.6.38 freezed on boot (not always, it seemed that 1 time out of 10 it worked.)
[COLOR=SeaGreen] [SIZE=4]+ [/SIZE][/COLOR]Loading the previous version 2.6.35 worked.

[SIZE=2]**Now, with proprietary drivers**[/SIZE]
[COLOR=Red] [SIZE=4]- [/SIZE][/COLOR]I can't use Unity. Yesterday I switched to gnome because I like it better, but today I tried to switch back to Unity with the ati drivers without success: it says that my hardware doesn't support it.
[COLOR=Red] [SIZE=4]-[/SIZE] [/COLOR]In firefox4, when I'm watching a video on youtube and press the full screen button, flash crashes (switching back to generics drivers it works)
[SIZE=4][COLOR=Red] - [/COLOR][/SIZE]The Catalyst control center doesn't work. When I try to launch it, it says

```
 There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
  
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
```  [COLOR=SeaGreen][SIZE=4]+[/SIZE] [/COLOR]Ubuntu 11.04 loads correctly.

---

### Post by Dario Zamuner on 2011-05-01
... neither Mysql Workbench works with the ATI proprietary drivers. :(

One lucky time I was able to start ubuntu 11.04 with generics drivers (1 out of 10 it works) and I can confirm that everything works in that case (flash, workbench, unity).

I really hope to see some update to resolve this issue soon, otherwise I have to restart my pc ten or more times to get it work, or make a fresh install of the 10.10 version.

---

### Post by lolface123 on 2011-05-02
same problem, but how can i do that if my computer won't even boot to the log in screen?? it is just giving me a black screen...

---

### Post by rb1234 on 2011-05-02
This seems to be a misadjustment in the grub configuration files. 

(1) Try to boot your gui, e.g. remove 'quiet' and / or 'splash' from the grub menu settings at boot time.
(2) Install startupmanager.
(3) Use startupmanager to set your screen resolution.

Maybe the splash screen won't appear, but the xserver should start.

---

### Post by lolface123 on 2011-05-03
how can i boot my gui? because after turning on my laptop, all it's giving me is a blackscreen...unless i have to press something??

---

### Post by Dario Zamuner on 2011-05-03
> **lolface123 said:**
> how can i boot my gui? because after turning on my laptop, all it's giving me is a blackscreen...unless i have to press something??

Press the shift key during startup to show the GRUB menu.

---

### Post by nosushi4you on 2011-05-03
I have the same problem as well. I also have an HP laptop with switchable graphics. I have posted another thread related to this issue.

Basically, if I install the driver, the system boots normally, but Unity does not work. If I uninstall the driver, Unity works, but the system rarely loads correctly, usually resulting in a black screen.

---

### Post by absolut1983 on 2011-05-04
Same issue over here (HP Pavilion dv6-3065ea). Upgraded from 10.10 (working fine except for the clickpad and the internal mic) to 11.04, booted properly once and never again.

   I tried removing both quiet and splash from the GRUB menu, but it didn't do much. After rebooting over 30 times I decided to reinstall 10.10 and give the developers some time to sort it out.

   Fair enough, Canonical is doing nothing but improving the user experience, but breaking stuff that was previously working causes nothing but pain.

---

### Post by mörgæs on 2011-05-04
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by lolface123 on 2011-05-05
the shift key doesn't work...=(

---

### Post by lolface123 on 2011-05-05
shift key doesn't work...=S

---

### Post by lolface123 on 2011-05-05
> **Dario Zamuner said:**
> Press the shift key during startup to show the GRUB menu.
 
shift key doesn't work...=S

---

### Post by mörgæs on 2011-05-06
Posting the same statement three times does not give you three times as many answers. It only annoys people.

---

### Post by lolface123 on 2011-05-07
sorry man, i thought i didn't send my previous post...that's why i post it again. just noticed it now...chill

---

### Post by sauthess on 2011-05-07
Hi,

If you managed to lower brightness before freeze, you should see a kernel panic I think (if you have the same bug as me). It happened 9 over 10 boots for me...

There is a bug with radeon module on 2.6.37 and after (so 2.6.38).

See here : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620")

You have multiple solution (before a fix is really provided) :

- blacklist radeon module (create file /etc/modprobe.d/blacklist-radeon.conf and add "blacklist radeon", then update-initramfs -u and all is ok)
- add radeon.modeset=0 as kernel boot parameter
- install fglrx drivers (that blacklist radeon so the problem is "solved" with the same solution as before ;))

Hope this help,

Regards,

---

### Post by Dario Zamuner on 2011-05-14
Blacklisting the radeon driver seems to fix the problem

I've followed the instructions from here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775462](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775462)

and added these lines to /etc/modprobe.d/blacklist.conf

```
# blacklisting radeon driver as it will not allow 2.6.38-8-generic to boot
blacklist radeon 
#blacklist closed source fglrx driver for graphics card
blacklist fglrx

```

---

### Post by mbooma on 2011-05-21
Same probleme here with HP DV7 and ubuntu 11.04 x64

-black screen sometimes (I think ubuntu doesn't support hybrid graphic card changement)

-no right click, no multitouch with clickpad

-slow wifi connection with RT3090.


**my solution**

*I install ATI driver but can't acces to at catalyst (fix the probleme but not totaly)

*for clickpad go here [http://ubuntuforums.org/showthread.php?p=10744640](http://ubuntuforums.org/showthread.php?p=10744640)

*for ralink Rt3090 install this download and install this [https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)


hope help someone ^^

---

### Post by mbooma on 2011-05-27
any solution for hybrid witch graphique card (ATI & Intel) ??


thanks ^^

---

