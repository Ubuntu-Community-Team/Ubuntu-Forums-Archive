---
title: "ubuntu 9.04 on ThinkPad T60, i can't see volume up/down notification"
date: 2009-04-26
forum: Hardware
---

### Post by m.h.shams on 2009-04-26
Hi everyone,

i just installed 9.04 on my Thinkpad T60p,

when i playing with volume buttons, i can't see the volume notification. btw volume changes correctly.

i didn't have this problem with 8.04 and 8.10,

any idea ?

thanks all,

---

### Post by sco01 on 2009-04-26
Same here on a T42. This worked in beta but not in release. Annoying.

---

### Post by MiRaCL on 2009-04-26
Same problem here on an Tp x60s. Worked fine in 8.10. Installed 9.04 yesterday. Onscreen volume notification is gone.

---

### Post by the_lex on 2009-04-26
Same problem on my Thinkpad R60e. I have an external wireless keyboard I use most of the time and when I use the volume hotkeys on that I get a nice shiny Jaunty volume notification. However, I've noticed that when changing volume on the external keyboard the "master" volume on the volume mixer moves. When using the Thinkpad's own hotkeys, I can hear my volume level changes, but the levels in the mixer DO NOT move to reflect this, and there is no notification. In previous versions of Ubuntu my PCM level in the mixer would move with my laptop hotkeys, though somewhat erratically. Now nothing moves, although the volume definitely still changes. What's happening I wonder!?

---

### Post by the_lex on 2009-04-26
Well launchpad says this is a confirmed bug and at the moment there isn't a fix. In short: 'notifications were originally working because each time you pressed a key, it was handled both through hardware and software, which meant that it was as if you had pressed the key twice. To correct that problem, software handling of those keys was removed for the ThinkPads. However, because the notifications were handled by the software handler, a side effect of this was that notifications were lost. What really needs to be done is to enable notification on hardware events.'

Read more on: [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/357673](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/357673)

I'm giving up and going to bed!

---

### Post by Das Pike on 2009-05-01
Bump so I can keep track of this thread since I'm having the same problem.

---

### Post by Lorenz on 2009-05-02
I'm experiencing the same problem on my T60. It's a pity, I used to be proud of how well mine copes with Ubuntu...It used to work till the RC, btw!

---

### Post by djconnel on 2009-05-04
The audio just completely doesn't work on my T60.  My temporary fix for the volume button issue is to reassign these functions to F5 (mute), F6 (volume down) and F7 (volume up).  

System->Preferences->Keyboard Shortcuts
click on the shortcuts for each audio function so it says "new shortcut", then press the F-key to which that function should be assigned.

But it doesn't help me in any case, Audio doesn't work.  For example, I test it with:
aplay -fcd /home/djconnel/backup/home/djconnel/.openoffice.org2/user/gallery/whoosh.wav

Nothing.

Everything was fine under 8.10.

% uname -a
Linux djconnel-t60 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

To make matters worse, "System Testing" fails to execute (I get a notice it's starting, then it just terminates).

---

### Post by metalf8801 on 2009-05-12
I'm also not seeing the volume bar on my T60 does this have anything to do with the new notification system and is there anything anything that can be done?

related posts it just too bad that these post are of other people having the same problem on their thinkpad with no solution 
[http://ubuntuforums.org/showthread.php?t=1133982](http://ubuntuforums.org/showthread.php?t=1133982)  
[http://ubuntuforums.org/showthread.php?t=1135449&highlight=volume+display+thinkpad](http://ubuntuforums.org/showthread.php?t=1135449&highlight=volume+display+thinkpad)

---

### Post by bishounen on 2009-05-18
Same problem here on my T60.  Brightness OSD works, but the Volume OSD does not.

---

### Post by musarraf172 on 2009-05-20
Same problem on my R 51.All hot key osd were working fine in 8.10 but now they all are gone with 9.04...Waiting for a fix.

---

### Post by metalf8801 on 2009-05-20
Is this happening on none Lenovo/IBM laptops? I'm wondering because when I change the volume on my desktop using my Memorex keyboard I see a volume bar on the screen.  So is this problem exclusive to Lenovo/IBM laptops or does it happen with all laptops?

---

### Post by tux2005 on 2009-05-20
I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

---

### Post by metalf8801 on 2009-05-23
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

I could be wrong but I don't think thats going to help because the Keys still work its the display that doesn't work like it used to and still does on other computers 

If that does work please tell me because I would like to be wrong 

Thanks 
Dan

---

### Post by dmillard10 on 2009-05-24
Not working here either.  I did see a solution on a launchpad page where someone downgraded their hotkeys package to the Intrepid version and got their OSD back.  He linked to the Intrepid package, which I downloaded, but Gdebi won't let me install it because I have a newer version installed.  Unfortunately, I'm not smart enough to either install it manually or override the Gdebi problem, but I'm sure it can be done.

Here's a link to that launchpad page: [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/364127](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/364127) (the post is near the bottom)

And a link to the package: [http://archive.ubuntu.com/ubuntu/pool/main/h/hotkey-setup/hotkey-setup_0.1-23ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hotkey-setup/hotkey-setup_0.1-23ubuntu7_i386.deb)

If anyone can help me with the installation that would be much appreciated.  I hope this link to the package helps.  Thanks.

---

### Post by lelamal on 2009-05-27
> **dmillard10 said:**
> Here's a link to that launchpad page: [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/364127](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/364127) (the post is near the bottom)

And a link to the package: [http://archive.ubuntu.com/ubuntu/pool/main/h/hotkey-setup/hotkey-setup_0.1-23ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hotkey-setup/hotkey-setup_0.1-23ubuntu7_i386.deb)

If anyone can help me with the installation that would be much appreciated.  I hope this link to the package helps.  Thanks.

Hey dmillard10, many thanks for this workaround! Actually, to me it was more than a mere workaround, for it was a proper solution. I had the same problem, having a Thinkpad R50e. I followed your link, and after trying Dominic's suggestion, i.e. "downgrading" to the Intrepid version of the package, not only do I have visual feedback whenever I adjust the volume or the brightness levels, but the on-screen display is now using the new notification system (Jaunty's), like anything else. Indeed, I thought that downgrading would have brought back the old notifications from Intrepid (which were great, by the way), instead of fixing things as they were supposed to be for the current version. Oh well... :D

As for your request, I had the same problem downgrading to an older version, so I figured I had to uninstall the newer, first. And it worked. So, go to Synaptic, click on "Search" and type "hotkey-setup". Set it to "Complete removal", then apply changes. Now you can install the older version - you will be informed that a newer version exists and advised to install that, instead. Just ignore this, and go ahead with the installation. It worked for me. I hope it works for many others out there.

Peace! ;)

---

### Post by dmillard10 on 2009-05-27
Major thanks lelamal!  I'm glad I was able to help out and I'm so glad you were able to help me install the package.  I have, however, accidentaly disabled my computer's sound while trying to turn off the horrendously loud system beeps, so I need to fix that, but the Jaunty notifications are working just fine and the buttons appear to be linked.  Thank you again! :grin:

---

### Post by richard.e.morton on 2009-06-01
T60 here... same problem.

I have also been using my T60 with Ubuntu and Kubuntu for over a year and in that whole time it runs very hot - multiple rebuilds in that time... same problem everytime.

With WinXP the system runs much cooler. I odnt have anything wierd installed. when playing video the system overheats and auto-shuts down.I have tried a few things on previous builds... 

On a differnet subject with a Via SP13000 motherboard, hardware Mpeg2 decodiing isn't enabled and can't playback video smoothly (it works fine with fedora)... I am starting to wonder about ubuntus legendary out of the box hardware support... maybe I have just had bad experiences.

what are other peoples experiences?

Thanks

Richard

---

### Post by petitbootang on 2009-06-04
[http://d.hatena.ne.jp/shimobayashi/20090506/1241569677](http://d.hatena.ne.jp/shimobayashi/20090506/1241569677)

---

### Post by mkkohls on 2009-06-04
Works great! Thanks for the tip on downgrading.

---

### Post by OptikKnight on 2009-06-06
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```


This worked for me. 

Mine is an R51 laptop. 

Before applying this, the brightness seemed to control the hardware properly, but there was no OSD, and the volume keys did nothing. 

Now both seem to work well - though the brightness OSD doesn't seem to update to reflect actual brightness.

---

### Post by johnnyhostile on 2009-06-07
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

Thinkpad T60 1951

Worked instantly for me!

---

### Post by maKA28 on 2009-06-20
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

works instantly for me too T60 model 8741!!

---

### Post by lelamal on 2009-06-21
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

Hi! This worked for me, too! I was annoyed by the icon always sitting in the tray suggesting me to update to the latest version of the *hotkey-setup*. So I applied the update, made sure the hotkeys OSD had gone again, then used the above code. I had to use a root terminal, though, as for some reason I couldn't use *sudo* in a normal terminal window, for I kept receiving:
> bash: /proc/acpi/ibm/hotkey: Permission denied
However, many thanks!

Update: was this solution permanent for you, guys? After restarting, OSD disappeared again here. Is there a way to make the change permanent? Thank you.

---

### Post by bismark on 2009-07-02
Just add the line to your /etc/rc.local file before the ```
exit 0
``` line.

```
sudo gedit /etc/rc.local
```

---

### Post by lelamal on 2009-07-03
> **bismark said:**
> Just add the line to your /etc/rc.local file before the ```
exit 0
``` line.

```
sudo gedit /etc/rc.local
```

Cheers, mate! This one worked.

---

### Post by ldrn on 2009-08-15
Downgrading worked for me, too, with an X60 tablet, thanks! :)

---

### Post by NetComrade on 2009-08-28
I have tried the both tricks above (echo and downgrade) and it didn't work.
Anyway to further troubleshoot? I am really fond of my volume keys :)
BTW, I did notice the same thing on the X41 I have when upgraded from 8.10 (the T500 was installed straight with 9.04)

T500/Ubuntu 9.04

---

### Post by cssa1 on 2009-11-08
For those hunting for a solution using Ubuntu 9.10, the method above worked on my Thinkpad T60.

Chris

---

### Post by m.h.shams on 2009-11-08
Thanks everybody.

this is work for me. 

Ubuntu 9.10  on  IBM (Lenovo) ThinkPad T60

---

### Post by richard.e.morton on 2009-11-08
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

worked for me on Kubuntu 910 with T60 Type 2007-CTO

---

### Post by migfix on 2009-12-01
> **tux2005 said:**
> I found the following at [http://bbs.archlinux.org/viewtopic.php?id=70891](http://bbs.archlinux.org/viewtopic.php?id=70891)

As root run:
```
echo enable,0x00ffffff > /proc/acpi/ibm/hotkey
```

Worked for me on T60P [2007-CQ8] Ubuntu 9.04

---

### Post by Khopstick on 2010-07-28
Just for the record: worked for me too! Many Thanks! I'm running kubuntu 10.4 (KDE 4.4) on a T60p.

---

### Post by Cyberto on 2010-09-21
```
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

```

Works on 10.10

---

### Post by ibcrusn on 2010-10-31
> **Cyberto said:**
> ```
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

```Works on 10.10

This works on my T60p (8742) but isn't permanent, when I reboot the notification and sound are gone. I tried bismark's fix but there was no change. What am I missing here?

---

### Post by ibcrusn on 2010-11-01
Tried tux2005 step as root and no change. Is there a permanent solution?

---

### Post by ibcrusn on 2010-11-06
Well, installed Fedora 14 and the sound works fine but still ahve the same issue with the volume buttons. At least it's halfway there. We'll see if this solution works on it.

---

