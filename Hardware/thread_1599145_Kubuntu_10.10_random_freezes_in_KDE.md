---
title: "Kubuntu 10.10 random freezes in KDE"
date: 2010-10-17
forum: Hardware
---

### Post by dimoftheyard on 2010-10-17
Kubuntu 10.04 worked fine on my Dell Vostro 1720, but since I upgraded to Kubuntu 10.10 I get random freezes in KDE. They don't occure very often, but when they happen there is nothing I can do but turn off the computer with the power button.
After I noticed very high cpu usage from kwin and those hang-ups I turned off desktop effects. Now kwin seems to behave normally, but I just had another total freeze. Unfortunately I cannot tell when this happens. I don't even think there is any program that was running every time, except for the normal background jobs and kopete.

While I stayed on tty (with no X server running) or in another window manager I did not notice any problems, but of course that is no prove that KDE is causing them.

I found no hints on Google, and I fear my information is too vague, but I'm clueless as to why this is happening.
I would very much appreciate any hints, because I hate to run off my laptop that way.

---

### Post by dimoftheyard on 2010-10-17
One more thing that might be related: The cpu usage of Xorg occasionally jumps up to over 25% and goes down shortly after. Unfortunaly I did not check the cpu usage directly before a freeze so far.

---

### Post by smithmatthews on 2010-10-19
I'm seeing the same issue, and still investigating.


Here's what I've noticed thus far:
* Desktop freezes, windows become unmovable or selectable.
* Keyboard won't respond at all, even if unplugged and plugged back in.
* Mouse pointer will usually respond at first, but eventually hangs.
* I can still SSH in to the box and reboot.
* I've seen it happen most often when clicking things in the System Tray.  Clicking the notifications will lock it consistently enough to be reproduced.
* Bazaar Explorer caused a hang once, maybe coincidence.


Also, from my Xorg.0.log.old file...
```
[ 85880.156] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[ 85880.175] 
Backtrace:
[ 85880.228] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[ 85880.228] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a0824]
[ 85880.229] 2: /usr/bin/X (xf86PostMotionEventP+0xc4) [0x47c194]
[ 85880.229] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f7c08ac9000+0x5399) [0x7f7c08ace399]
[ 85880.229] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f7c08ac9000+0x5a8e) [0x7f7c08acea8e]
[ 85880.229] 5: /usr/bin/X (0x400000+0x6b837) [0x46b837]
[ 85880.229] 6: /usr/bin/X (0x400000+0x11f4e3) [0x51f4e3]
[ 85880.229] 7: /lib/libpthread.so.0 (0x7f7c0e135000+0xfb40) [0x7f7c0e144b40]
[ 85880.229] 8: /lib/libc.so.6 (ioctl+0x7) [0x7f7c0d160437]
[ 85880.229] 9: /lib/libdrm.so.2 (drmIoctl+0x28) [0x7f7c0b70f0a8]
[ 85880.229] 10: /lib/libdrm.so.2 (drmCommandWrite+0x1b) [0x7f7c0b70f32b]
[ 85880.229] 11: /lib/libdrm_nouveau.so.1 (0x7f7c0b0d1000+0x2a9d) [0x7f7c0b0d3a9d]
[ 85880.229] 12: /lib/libdrm_nouveau.so.1 (nouveau_bo_map_range+0xff) [0x7f7c0b0d3c8f]
[ 85880.237] 13: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x7f7c0b2d7000+0x56fd) [0x7f7c0b2dc6fd]
[ 85880.237] 14: /usr/lib/xorg/modules/libexa.so (0x7f7c0a229000+0x45a7) [0x7f7c0a22d5a7]
[ 85880.237] 15: /usr/lib/xorg/modules/libexa.so (0x7f7c0a229000+0x8764) [0x7f7c0a231764]
[ 85880.237] 16: /usr/lib/xorg/modules/libexa.so (0x7f7c0a229000+0x132fa) [0x7f7c0a23c2fa]
[ 85880.237] 17: /usr/bin/X (0x400000+0xda52d) [0x4da52d]
[ 85880.237] 18: /usr/bin/X (0x400000+0x2a6b2) [0x42a6b2]
[ 85880.237] 19: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[ 85880.237] 20: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[ 85880.237] 21: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f7c0d0a0d8e]
[ 85880.237] 22: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
```

[FreeDesktop Bugzilla – Bug 26980]("https://bugs.freedesktop.org/show_bug.cgi?id=26980") - seems to be on track with what I'm seeing.


-Matt

---

### Post by dimoftheyard on 2010-10-19
After some more reboots I 'fixed' my problem by reinstalling Kubuntu 10.10. Everything seems to work now, although it's hard to test that. Xorg still uses a lot of cpu sometimes, but that might be normal.

@Matt: My freezes were somewhat different, I think. I could not access the computer with ssh, but I too noticed that the mouse could move a little longer. Music seemed to work even longer, it once stopped a second after my mouse stopped moving. 
I did not find a backtrace in the Xorg logs, but I'm not using nouveau, so at least that part of the problem can't be the same anyway.
Good luck with finding a solution!

And thank you to all who read my post.

---

### Post by smithmatthews on 2010-10-22
Good to see you've fixed it.

I swapped video drivers out from the Nouveau driver to the nVidia proprietary driver and my issues have gone away.  Prior, I was hard-locking several times a day.  Now, it's going on 3 days with no locks.

---

### Post by dimoftheyard on 2010-10-25
As a matter of facts my 'fix' didn't work, the system froze again. Now I reinstalled Kubuntu 10.04 and everything seems to be good again.
I did use the proprietary nvidia driver all the time, so my problem seems to be of different origin.

---

### Post by schnook9 on 2010-10-26
Try disabling the Desktop Effect "Blur".  I have had this very high (60-80%) CPU on-going since upgrading to 10.10, and played around with all kinds of settings.  The only thing that worked was going thru my effects one by one with the System Activity monitor up on the screen at the same time.  You uncheck one, hit apply, look at CPU. if it does not go down, re-check the effect and then uncheck another, rinse, repeat etc.

For me it was Blur.

HTH

---

### Post by sfmedion on 2010-10-31
It's my first time that i'm usung KDE and i'm very disappointed. I don't know if it's 10.10 or something else, but my gnome system never froze. :(

---

### Post by sabatmonk on 2010-11-03
i have thet the same problem and i would like to know how to solve this...
i'm using kde on my laptop after 2 years of ubuntu on pc.

---

### Post by dieduiwel on 2010-11-04
I have been getting the same thing. Been trying to get Kubuntu 10.10 (64bit) working on my HP ProLiant ML110 with an additional ATI Radeon 7000 for a few days now after trying to replace a troublesome Debian, installed to replace a not so stable Ubuntu 10.04 (unlikely a hardware issue as the machine works perfectly well with a Live USB Linux 9.04). It seems that maximising windows and firing up Amarok hastened the freeze. I also get the black screen, some times with, some times without the mouse pointer and music still playing, but completely frozen... ctrl/alt/Fx not responding... a hard reset the only way out apparently. I messed around with graphics drivers, tried using Gnome instead (even worse) but the same thing keeps happening.

So now I installed a 32 bit version of Ubuntu 10.10 and the install was definitely much smoother than the 64bit Kubuntu 10.10. I had one freeze so far, admittedly while importing 10K songs, doing the software updates and hitting Firefox hard. The system monitor did not register anything significant...but at least I was able to drop into a command shell (ctrl/shift/f1) and rebooting. Went back in, turned of all desktop effects ... and finally... it seems to be stable. I suspect it has more to do with the 32bitness and less so with KDE vs Gnome. I might install KDE next and see how it behaves.

Hope this helps others.

---

### Post by dieduiwel on 2010-11-04
Bad news... even though performance is much better and more stable.. I have now had about 3 seemingly random crashes. Screen goes black...sound continues... Ctrl+Alt+F1 halts the sound until I enter my username and password in the dark...then the sound returns... but nothing else. I am now getting dangerously close to binning Linux for another 5 years and going back to Windwows.

Will try installing KDE and see how that goes... 

If any body has any ideas...do share please.

---

### Post by omniuni on 2010-11-05
Hi,

I have read that downgrading the radeon driver may fix this, but I haven't yet tried it myself.

---

### Post by tadaskr on 2010-11-05
ok, yesterday my kubuntu random freezes and now i can't log in from desktop enviroment. I try uninstall desktop enviroment but that don't fix that.. can anybody help me? it not first time that in kubuntu i can't login. But that time I reinstall kubuntu. So should I reinstall kubuntu or there is any fix that? now I'm using windows 7, because I don't have choise

---

### Post by AlvaroRD on 2010-11-05
I have a similar problem with Ubuntu 10.10 and KDE running on a imac 24" 2009.

KDE starts properly and suddenly when i try to switch the desktop it freezes. I've seen XORG consuming 60% to 70% of CPU.

I solved the issue modifying settings at: NVIDIA XServer Settings -> PowerMizer -> Preferred Mode = Prefer Maximum Performance.

Can sombody try it:

```
uname -a
Linux iLinux 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux
``````
nvidia-xconfig -v

nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to enable NVIDIA X driver functionality.

  Copyright (C) 2005 - 2010 NVIDIA Corporation.
```
Regards.

---

### Post by IljaRepin on 2010-11-18
Hi,

I am experiencing the same problem. I am running Kubuntu 10.10 Maverick with KDE 4.5.1 on Dell Latitude E6400, and I have an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller. I have basic Kwin desktop effects enabled, and am using the Desktop cube.

The screen freezes at random times. Actually, it did it once while writing this post. The mouse pointer moves but the window system is completely non-responsive. The only way out is a manual power-off. (I did not try bringing up a terminal.)

I cannot say what might trigger the freeze. Sometimes it happens while I'm rotating desktops or using other effects, but it can also happen while I'm clicking the taskbar or just basic Firefox buttons. I don't see any unusually high CPU activity (although I'm not sure what would be unusual). When I'm moving the mouse around, the Xorg process is using about 20 % of the CPU, according to the System Monitor. The glxgears gives me 58 FPS, while running Firefox, Kmail and Skype.

I will try disabling some desktop effects next, and if that helps, will report back.

If anyone can shed light to this, I would be greatly pleased. I have used KDE for some time now, and was first a little afraid of KDE 4, with all the plasma stuff and everything. Now I decided to put it on my laptop, and am falling in love a bit. If there just weren't these annoying hangups.

- Repin

---

### Post by dscoggins on 2010-11-19
> **schnook9 said:**
> Try disabling the Desktop Effect ... uncheck one, hit apply, look at CPU. if it does not go down, re-check the effect and then uncheck another, rinse, repeat etc.

For me it was Blur.

I have had random system freezes since kubuntu 10.04. Switching to 10.10 has helped some. My symptoms? Always screen activity freezes, sometimes the whole system locks up and sometimes just the display freezes and is accessible via ssh. Once, it froze right after I started burning a CD with K3b, I waited until the burner light stopped flashing before doing a hard reset and was amazed to find the the burn process was successful!

Followed @schnook's advice and found that certain Desktop Effects do indeed take a noticeably greater amount of X resources then others. And, I too found that Blur was a big offender. To give a perspective, with Blur activated the xorgs process idled at 8 to 10%, with it unactivated, xorgs, at idle, drop to 1 to 3%.

Here is what I am running
[LIST]
[*]ASUS  M4A785-M motherboard
[*]AMD Athlon II X2 240 2.9MHz CPU
[*]4 GB DDR3 8XX MHz RAM
[*]ATI RV710 (Radeon HD 4350)
[*]2 Samsung 1.5 TB SATA drives w/ RAID 1 
[*]Kubuntu 10.10 AMD64 / KDE 4.5.1
[*]Linux 2.6.35-22-generic
[/LIST]

I have some pretty heavy video and graphic tasked scheduled for this weekend so I'll post back next week with my results.

-Dan

---

### Post by richthanki on 2010-11-21
I'm so glad to have found this thread.

I have this problem too, on a Toshiba Portege R500 running 64-bit Kubuntu 10.10. For me it occurs whenever I'm playing audio, sometimes immediately, sometimes after a while. I've tried so much - attempting to resart Kwin, dropping into the tty sessions. 3 or 4 fresh installs.

Nothing works. And it's hugely frustrating knowing that the system is working perfectly in the background. I'm considering switching away from this, either to 10.04 or to Linux Mint KDE.

---

### Post by paperpuli on 2010-11-22
I also have the same problem with Kubuntu 10.10 on a Toshiba Satellite L510.

This is so frustrating, since Linux claims that it is much more stable than Windows and sometimes it isn't.

---

### Post by KernelSpace on 2010-11-22
This is a truely well know problem experianced by me an others. It seems to be a kernel/xorg bug
 
See the 1000+ posts here for more details
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

### Post by richthanki on 2010-11-23
I don't think that is the bug we're reporting on this thread. In my case the mouse works (but you don't know what you're clicking on as the screen is frozen - you can still change music volume and tracks if you luckily happen to click on a button), you can drop down to tty 1 to 6 (from where you can shut down), and this never happened on Ubuntu, happens only on Kubuntu - so it looks as if KDE (or its interactions with X and/or the Kernel) might well be part of the problem.

Furthermore, this bug is not totally random - my system is fine as long as you're playing no audio. When the screen does freeze, there's not even a hiccup to the sound which carries on merrily.

---

### Post by IljaRepin on 2010-11-25
Hi again,

My system has been working ok since I disabled the "blur" desktop effect. Unfortunately, I can't say that was the whole story, because I experienced one more hangup the same day I disabled blur. That happened - if I remember correctly - when I was "presenting all windows" which I have set as my upper left hand screen corner action.

By the way, also the "present windows" effect looks a bit funny to me: it first spreads all the windows on the desktop, but then the windows disappear leaving only the title and icon visible. Clicking in the space around the title and the icon focuses the corresponding window. Is this the correct behaviour?

Anyway, I haven't experienced the freeze in five days now, so I'm pretty happy. However, as long as we don't really know what causes it in the first place, there will remain a nagging fear that it might happen again.

Relating to richthanki's post: My freezes had no connection with audio. I don't think they ever happened while playing audio, but this is probably just a coincidence because I wasn't playing anything very often anyway. On the other hand, I could bring up tty's, but not reboot from there, as the screen was filling with error messages of which I remember only the repeating text: "GPU hung". I could not input anything between those messages.

-Repin

---

### Post by jacoor on 2010-11-25
Hi
I had this crazy issue every 15 minutes, drived me totally mad, since I have some work to do for tomorrow.

I haven't had this error for more than an hour now, so seems it is solved (doing the same stuff i did before). Try to disable proprietary driver if you are using ATI cards.  OS driver included in Ubuntu is not great at the moment, but at least for me now it's enough.

Hope it helps somebody.

BTW, my graphic card is ATI mobility Radeon HD 5470. Everything was working fine with prioprietary driver few days ago, just before some xorg update...

---

### Post by jacoor on 2010-11-25
ok, after few more hours of stable work (at last!) I can confirm that disabling proprietary driver works.

Good luck in resolving this bug... I'd really like proprietary driver...

---

### Post by IljaRepin on 2010-11-29
Hi,

Just had another freeze when Presenting all windows. This time the windows were left visible (not just their titles and icons as I explained before) and I was at first happily surprised, but then I noticed that the gui had just frozen to show the windows. :(

I have no proprietary drivers installed, at least to my knowledge. The problem has become very rare and thus tolerable after I disabled Blur. Next I will try quitting the use of Present all windows option. I wish I knew more about the inner workings of the graphics system to make some guesses.

-Repin

---

### Post by Psi84 on 2010-12-04
Ive a similar problem here. Updated KUbuntu from 10.04 and no it freezes randomly after some time. 

I can move the mouse AND can connect to the machine over SSH!
The X uses a lot of CPU, about 70% of my Quadcore. 

Restarting kdm or killing X brings no result, only a reboot helps.

I use a Geforce 9500GT with nouveau driver. I really really need a fix for this because its may daily-work pc.

---

### Post by Azguz Bloodfist on 2010-12-05
I am having the same problem.

Installed Kubuntu 10.10 yesterday on my Aspire Aspire 1680 and had 2 screenfreezes today. They occur randomly after at least an hour. Screen is completely frozen, cannot move the mouse. Fan is quiet, sound's like the CPU isn't doing much.

I am using the open source ATI driver with Kernel Mode Settings enabled (KMS). I'm not sure if that is relevant, as I didn't have this problem before enabling KMS.

Also running Kopete when it crashed - could that be an issue? I will avoid using it and see how it goes

---

### Post by Psi84 on 2010-12-07
Ive changed my GPU, installed the original nvidia driver and kicked nouveao - no crash up to now

---

### Post by derchefkoch on 2011-01-13
> **schnook9 said:**
> Try disabling the Desktop Effect "Blur". 
HTH

for me this was also part of the issue. I get far less crashes now (but still some)

---

### Post by flo121at on 2011-01-15
Hi!

I had the same issues on a Thinkpad T61 with 10.10 and Nvidia G84M [Quadro NVS 140M] with the proprietary driver. Freezes occurred even with completely disabled Desktop effects (Xorg caused very high CPU usage).

[SIZE=4]**Solution**[/SIZE]

Switch the QT graphic system from native to *raster* as described in [http://forum.kde.org/viewtopic.php?f=66&t=90821](http://forum.kde.org/viewtopic.php?f=66&t=90821) 


[LIST=1]
[*] Create a script in *~/.kde4/env* which contains the line ```
 export QT_GRAPHICSSYSTEM=raster 
```
[*]Logout and re-login.
[/LIST]
[B][SIZE=4]Circumvent side effects on OpenOffice:[/SIZE]

[/B]OpenOffice crashes during startup with this setting. So you need to disable it explicitly for OO.


[LIST=1]
[*]Open* /usr/lib/openoffice/program/soffice* and the following line: ```
 export QT_GRAPHICSSYSTEM=native 
```
[/LIST]
Now KDE Performance is perfect again.

---

### Post by derchefkoch on 2011-01-19
> **Psi84 said:**
> Ive changed my GPU, installed the original nvidia driver and kicked nouveao - no crash up to now

 Using the original nvidia driver helped. (I also deactivated the blur desktop effect before) --> no crashes so far...   for those who don't know how to in Kubuntu 10.10: - Hit the "K" botton (the thing called "start botton" in windows) - go to applications - system - additional drivers

---

### Post by IljaRepin on 2011-02-10
Hi,

After my last post (30 Nov) I stopped using "Presenting all windows" as well as "Blur". There have been no freezes ever since. No clue as to what could have been the cause, but I hope this will work for some of you.

-Repin

---

### Post by jbaack on 2011-02-28
Just wanted to thank everyone for the info in this thread. I just installed 10.10 64 bit and was having the freezes a few times a day. Was on Nouveau - installed the Nvidia driver and now none. That fixed mine.


Jim

---

### Post by walter_j on 2011-03-22
I'm trying kubuntu as a alternative to ubuntu. I don't like the direction ubuntu is going with unity. Thats a whole different discussion though.

I installed kubuntu 10.10 recently, and within a few days started to have lockups, where i caould move the mouse - and thats all. Music would play (amarok) but nothing else. hard reset. I tried the proprietary video driver, but lockups with that too. I noticed dmesg was reporting some strange errors with the video drivers, so i suspect this is the problem. I used to have this problem in ubuntu 10.04, and eventually resolved it with video drivers. Ubuntu 10.10 has never had this problem, and my pc ran for weeks at a time.

I suspect the devs are too busy with unity to sort this one out. No ubuntuu one in kubuntu too, but thats another discussion eh.

I have a Nvidia card : Geforce GT 220. issues with samaba too:

---

### Post by mastablasta on 2011-03-23
yeah they don't give a F... about KDE.
This is not the only error. I for example can't play audioCDs propperly (cd is mounting god&dev knows where). Also installing Samba does not install all necessary packages. one package needs to be added manually.
 
What card are you using? I don't have lock ups (though occasionally KDE crashes and recovers) but latest updates messed up falsah player so some videos don't work propperly no more and even crash the system (sound...). I use ATi with OS drivers. What you could do is try to upgrade the KDE to 4.6 or try Linux mint. though i also had strange issues with their KDE.
 
It's too bad because both have very nice look and feel. And i kind of got to like the KDE interface.
.

---

### Post by walter_j on 2011-03-27
firmware update seems to have fixed the lockup problem. 2 days w/o lockup so far. looks promising.

Nvidia 220 with prop. driver and latest firmware update as of march 25. Also enabled desktop effects.


Updated to 4.6.1 but still getting lockups. More stable, but...

---

### Post by kio_http on 2011-04-02
Kwin has received massive under the hood improvements recently. Try updating to KDE 4.6.1

Updating Packages

1. Add the Kubuntu PPA represitory
To learn how to add repositories in kubuntu click [here]("https://help.ubuntu.com/community/Repositories/Kubuntu").
The represitory you want to add is ```
ppa:kubuntu-ppa/backports
```
2. Open a terminal. To launch you can do ALT + F2 and type "konsole"

In konsole:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

3. Restart the computer

Speeding up window management

1. In KDE system settings, go to Desktop effects.
Enable an effect call scale resize or something like that.
Set Crisp mode in the last tab of the setting page.

(If if is still slow)
2. Press ALT + F2 and type 
```
oxygen-settings
```
Disable some effects.

---

