---
title: "Shift key stuck for approximately one minute"
date: 2010-04-22
forum: Hardware
---

### Post by beow on 2010-04-22
Have this strange problem with my Thinkpad T61 running 9.10. Every now and then (more often lately, about one time each other day on average) the system acts as if the shift key was pressed continously:

* Letters are typed with reversed caps (Caps lock gives small letters)
* Mouse is anchored when clicked

After some time, a minute or so the behavior is gone and everything is back to normal again. Can't see anything in the normal logs like syslog, kernel log. Had this problem a long time ago (a year back or so), it disappeared but is coming back now. Anybody have a clue?

---

### Post by ddalcu on 2010-05-16
I have the same problem with keyboard in Ubuntu 10.04... No solution yet. Please help!

---

### Post by wlad0 on 2010-05-20
Same problem in Ubuntu 10.04.

---

### Post by wlad0 on 2010-05-29
Disabling compiz seems that everything is working. I try reset compiz settings but no effect

---

### Post by fogNL on 2010-05-29
Same problem here, has been happening over multiple installs.  Its been driving me crazy.  When it starts to happen, i start banging on my keyboard constantly, and it seems to fix it, no idea why.

I thought it was just my keyboard at first, but, I also run NoMachine nxserver for remote access, and when I'm at work I remote in, and the same thing can happen.  Almost like the system gets confused as to which mode it should be in.

---

### Post by beow on 2010-06-02
I'm not alone at least... :) Would be good if you provided which HW you're running, just to exclude if it is HW related.

The two latest times this happened (yesterday and today) a single tap on the shift key cured the symptom. Can't say that it is a work-around yet though...

Hope the devs gets notified about this, anyone filed a bug report?

---

### Post by beow on 2010-06-02
> **beow said:**
> 
Hope the devs gets notified about this, anyone filed a bug report?

Just found out that there is one since yesterday...

[https://bugs.launchpad.net/ubuntu/+bug/588473](https://bugs.launchpad.net/ubuntu/+bug/588473)

---

### Post by fogNL on 2010-06-02
> **beow said:**
> I'm not alone at least... :) Would be good if you provided which HW you're running, just to exclude if it is HW related.

The two latest times this happened (yesterday and today) a single tap on the shift key cured the symptom. Can't say that it is a work-around yet though...

Hope the devs gets notified about this, anyone filed a bug report?

My hardware is in my sig, and my keyboard is just a standard Lenovo keyboard with no fanciness to it at all.

I think that there's more than just the Shift key getting stuck, because, it happened again for me a minute ago, and when i started typing, menus would be popping open, etc, as if i was pressing the alt or meta keys.  This is a mess.

---

### Post by wlad0 on 2010-06-02
hey guys, not only shift is the problem for me. The same happens with Ctrl, Alt or SysKey. My keyboard is Logitech UltraFlat Keyboard

```
vlado@vlado-desktop:~$ lsusb 
Bus 002 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 001 Device 002: ID 03f0:c402 Hewlett-Packard PhotoSmart D5100 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

In Ubuntu 9.04 and 9.10 keyboard work perfectly. After upgrade to 10.04 problems began. Same after clean install Ubuntu 10.04 :(

---

### Post by ler0y on 2010-06-02
> **wlad0 said:**
> hey guys, not only shift is the problem for me. The same happens with Ctrl, Alt or SysKey. My keyboard is Logitech UltraFlat Keyboard


Same here with two different keyboards.. one is my Lenovo laptop and one from a Microsoft keyboard. This has been over NoMachine.. I have not used it sitting at the console enough to notice the issue. Ctrl and Shift are my two worse offenders.

---

### Post by ler0y on 2010-06-04
Anyone have an update on this? I have re-installed Nomachine with no resolve. Between nomachine sticky keys and slow performance my Lucid upgrade then the later fresh install has proven to be an epic failure.. I may have to go back to 9.x. :(

---

### Post by ler0y on 2010-06-07
> **ler0y said:**
> Anyone have an update on this? I have re-installed Nomachine with no resolve. Between nomachine sticky keys and slow performance my Lucid upgrade then the later fresh install has proven to be an epic failure.. I may have to go back to 9.x. :(

Looks like the stuck keys is an issue with the current version of NoMachine. I installed 9.10 back on the box.. the thing runs fast again so the speed issue was a Lucid problem, but the keys are still getting stuck. Both systems had the newest version of nomachine installed. :(

---

### Post by beow on 2010-06-14
Have had this for a couple of times now the last week and I'm beginning to think that just tapping once on the left Shift key cures the condition. It has worked every time the latest 5-6 times this state occurs, maybe still to early to call it a workaround, but you might test it.

---

### Post by travisj on 2010-06-18
I have this problem too (it also happens with ctrl and alt). For me, it is not related to nomachine -- I've never had nomachine installed.

I can "unstick" any key by switching to tty1 (ctrl-alt-f1), switching back (ctrl-alt-f7), then pressing the particular key that was stuck. This works 95% of the time, the other 5% of the time I have to repeat the procedure one more time. Of course, this is annoying because a key gets stuck about once an hour for me.

Just tapping on the stuck key does not fix the problem for me.

---

### Post by wlad0 on 2010-06-18
I thought that this is a problem with Compiz. But after long time  testing it looks like Xorg problem :( Same thing happens without Compiz

---

### Post by thetrojan01 on 2010-08-27
excuse me for opening an old topic, but I've found that this problem appears when a video device (such as a tv tunner card) is plugged in the computer.
It may have something to do with X, or HAL...

Does anyone else experience this problem too?

---

### Post by mulpac on 2010-08-28
> **thetrojan01 said:**
> I've found that this problem appears when a video device (such as a tv tunner card) is plugged in the computer.


That might be related to the problem I am experiencing. For me, shift and ctrl gets stuck sometimes. Usually, it does not help to push shift or ctrl just one time, but hitting them a few times (well, sometimes quite many times) helps. Also switching to the console (ctrl-alt-Fx) and back helps. Additionally, xev shows that Control_L and Shift_L are pressed at a ten second interval (Control_L pressed and released, ten seconds later Shift_L is pressed and released, ten seconds later Control_L is pressed and released and so on). They are pressed for a very short time, but every now and then i accidentally get a versal when I am typing or activate some <ctrl><letter> shortcut. If I log out and log in xev shows no activity at first, but after some time this shift and ctrl pressing starts again. When keys get stuck, xev shows this activity, so it seems to be related. I believe it happens when I press ctrl or shift on the keyboard at the same time as those strange ten second presses occur, but I am not completely sure about this. I tried disconnecting mouse, keyboard and everything connected to usb, except the tv tuner, and xev still showed the key pressing.
I did not have this problem on Gutsy or Jaunty with the same hardware (well, at least not on Jaunty, maybe Gutsy was before I upgraded the hardware) (Athlon X2 4850e, Nvidia graphics with proprietary driver). It started when I had upgraded to Lucid. Not running Compiz.
Is there some way to trace what is generating those annoying key presses?

---

### Post by thetrojan01 on 2010-08-29
I think I didn't have that problem either with a previous version of Ubuntu, but later on, I had that problem with Arch Linux and a newer version of Ubuntu Desktop / Ubuntu Server. I think it's X11 or hal related...

---

### Post by cgarvey on 2010-09-08
Same problem here. "SHIFT_L" gets stuck. I've an Apple aluminium keyboard (the USB variant, not the Bluetooth one). The last few times I've tried the trick posted above (switch to console and back, then tap shift key) has worked, but that's not an exhaustive test.

Based on comments above, some additional obserations:
+ I do have a WinTV PCI tuner card. This happens, though, whether or not I'm using TvTime (so the tuner card is present, but not active when this has happened).
+ Unplugging/replugging the USB keyboard doesn't fix it.
+ When I switch to text console the keyboard works fine, but goes back to SHIFT_L being stuck in Gnome (unless the first key I press is shift, as per the above trick).
+ It doesn't happen in Windows Vista on the same machine.
+ It has happened while using gVim, KomodoEdit, Thunderbird, NetBeans, and a variety of other software. I haven't noticed it whilst typing in a (Gnome) Terminal window, though.
+ The time it takes to reset itself (i.e. I sit there and do nothing) is about 30 seconds (and I can tell it's fixed by a new KeyboardEvent if I run xev).
+ The problems start with a KeyboardEvent with a different "Serial" than that of the keyboard.

Other than that, I must state the obvious that this is extremely annoying.

---

### Post by wlad0 on 2010-09-15
I have TV tuner on my system too.
```
01:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
```

---

### Post by aximilation on 2010-11-03
I've been running into this issue rather sporadically as well, although for me it is always the home key that is stuck. I just switched to tty1 and it seemed to fix it, but man, that's annoying, especially as this is the computer I do all my work at, and it seriously detracts from my productivity when this happens. For me it seems to randomly resolve at times within 30 seconds-1 minute, other times it sticks until reboot or enough button pressing "magically" clears it.

---

### Post by mulpac on 2010-11-04
It seems like I have found what was causing my problems now. It was actually xine that pressed shift and ctrl as an effective, but rather primitive, way to inhibit the screen saver. Unfortunately, those keys interfered when typing on the keyboard and sometimes caused stuck keys. Setting 
gui.screensaver_timeout:0
in the xine config file seems to have solved the problem.

---

### Post by jim.hitch on 2011-03-13
> **mulpac said:**
> It seems like I have found what was causing my problems now. It was actually xine that pressed shift and ctrl as an effective, but rather primitive, way to inhibit the screen saver. Unfortunately, those keys interfered when typing on the keyboard and sometimes caused stuck keys. Setting 
gui.screensaver_timeout:0
in the xine config file seems to have solved the problem.

Thanks for posting this. It seems to be working a treat. For a moment I thought I was living in a Windows virus world again!

---

### Post by cantab on 2011-06-29
I know this is a huge bump, but does tvtime use the same screensaver-disabling method as xine? If so, how do I disable it on tvtime?

---

### Post by beow on 2011-10-16
Have the same problem now when I run Win7 on the same Thinkpad 61. So in my case it seems to be something unrelated to Ubuntu.

---

