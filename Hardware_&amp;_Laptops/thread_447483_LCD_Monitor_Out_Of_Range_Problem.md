---
title: "LCD Monitor Out Of Range Problem"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by Kevin Funnell on 2007-05-18
I am having problems in getting an BENQ LCD Analog Monitor (Model FP92W 19” Wide Screen) to work with Ubuntu.  When I first fire up the computer it displays a Pop-Up Message:  Input:Sub-D.
Selecting either OS:   Ubuntu OS (Kernal 2.6.15-28-386) or Ubuntu OS (Kernal 2.6.15-28-386 (Recovery Mode)), all appears normal  - displaying  OK for all.
At the end of the boot sequence a Pop-Up Message appears on a blank screen:   OUT of Range! (nothing else).

I an unable to proceed past this point,  if I CTRL, ALT, BACKSPACE to recovery it keeps going to the blank screen and Pop-Up message:    OUT of Range! 

There have bee similar posts on this problem but most are dealing with from within Ubuntu , I haven't been able to get Ubuntu up and running with the LCD monitor.

What I would like to know is How can rectify the problem, I have no problems using the monitor with that other OS (Windows XP).
Some System Info:
System: Intel P4, RAM 512Mb, 4 x HD - various size
Display Adapter: NVIDIA GeForce2 MX/MX 400
Dual Boot: Ubuntu Dapper Drake (6.06 LTS) and Windows XP.

Thanks in advance,

Old Kevin

---

### Post by heimo on 2007-05-18
You should probably try to reconfigure your Xorg using these instructions (first change to virtual console using ctrl+alt+F2):
[Fix Video Resolution]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by Kevin Funnell on 2007-05-18
Heimo,

Had a look at your reference and have a question: Can this be done for the Log in Screen - Where you select the OS under Option C (I think) as I am unable to log-in to the OS.

Old Kevin

---

### Post by heimo on 2007-05-18
> **Kevin Funnell said:**
> 
Had a look at your reference and have a question: Can this be done for the Log in Screen - Where you select the OS under Option C (I think) as I am unable to log-in to the OS.

I don't understand your question. You need to get to command line - and if your system starts, but monitor doesn't show anything (out of range), you should still be able to change to virtual console (ctrl+alt+F2) and log in. Or you could try starting in recovery mode.

---

### Post by Kevin Funnell on 2007-05-18
Heimo,

You answered my question sorry about not expressing it correctly, I give it a go over the weekend after readin throuh your reference and other tips.

Thanks, 

Old Kevin

---

### Post by Herman on 2007-05-18
Hello Kevin Funnell, 
I agree with heimo, that link he provided contians all about it.

I just bought myself a nice new 20"W Acer LCD monitor, for 1680x1050 resolution for my desktop machine. I just unplugged my old 17" CRT model and I already was expecting to need to run '[sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")', and that is what I tried first when I got the same message as you, "Input out of range" or something like that.
I tried several times re-running sudo dpkg-reconfigure xserver-xorg but each time I did so it would not allow me to change the resolutions, I tried all the different keys on my keyboard I though likely, and then some. Nothing I tried would let me change the default suggested resolutions (which were wrong).

Finally I gave up on re-running sudo dpkg-reconfigure xserver-xorg and booted the Fiesty Fawn LiveCD and mounted my hard disk installed Ubuntu filesystem in that.
```
sudo mkdir /media/ubuntu
``````
sudo mount -t ext3 /dev/hda2 /media/ubuntu

``````
sudo gedit /media/ubuntu/etc/X11/xorg.config
```In xorg.conf I found the lines where the resolutions are given, like in heimo's link, for example,
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "AL2016W"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes          [COLOR=Navy] **"1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"**[/COLOR]
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes          **[COLOR=Navy] "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]**
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes          **[COLOR=Navy] "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]**
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes          **[COLOR=Navy] "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]**
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes         **[COLOR=Navy]  "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]**
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes          **[COLOR=Navy] "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"[/COLOR]**
        EndSubSection
```   Okay, I knew those resolutions are wrong, I know my new monitor should use "1680x1050", from the documentation (not to mention the big label on the box it came out of). So I did some quick maths and figured that 3/4 the width x 2.5 will give me the new height. So I figured out and went with the following resolutions, ```
 Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV280 [Radeon 9200 SE]"
    Monitor        "AL2016W"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes       **[COLOR=Red] "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"[/COLOR]**
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        [COLOR=Red]**"1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"**[/COLOR] 
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        [COLOR=Red]**"1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"**[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        [COLOR=Red]**"1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"**[/COLOR]
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes       **[COLOR=Red] "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"[/COLOR]**
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes       **[COLOR=Red] "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"[/COLOR]**
    EndSubSection
EndSection

```I edited my xorg.conf file with those and saved it from the LiveCD and rebooted and it's working fine! :) As a matter of fact I'm typing to you on it now. You might notice I also took the opportunity to go a notch higher even than advertised! "1920x1200" works and with the extra width plus the smaller size text it's like having two monitors now. I can fit two pages side by side and read them both!
This is pretty much the same information heimo already gave you in the Wiki link, just explained a little differently.
I hope it helps.
Regards, Herman :)

---

### Post by Kevin Funnell on 2007-05-19
Thanks Heimo and Herman with your help I was able to resolve the problem using  'sudo dpkg-reconfigure xserver-xorg', I dot think I would of been able to work out all the information required to input if it did not work.

The problem is sovled
Thanks, Old Kevin

---

### Post by Herman on 2007-05-19
Kevin Funnel, 
Good, thanks for the feedback, I'm happy to read you fixed it okay. 
Regards, Herman :)

---

