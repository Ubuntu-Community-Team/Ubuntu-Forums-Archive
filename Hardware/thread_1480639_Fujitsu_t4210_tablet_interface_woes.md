---
title: "Fujitsu t4210 tablet interface woes"
date: 2010-05-11
forum: Hardware
---

### Post by Thipp on 2010-05-11
Ok, I am totally new to this, I just downloaded my first Ubuntu cd earlier today and I have spent pretty much every moment since trying to get the tablet portion of my Fujitsu t4210 working. Most everything else worked as soon as I installed Ubuntu which was nice and the tablet does receive a degree of input so I know the system reads it, there is no on screen cursor but if I touch the screen anywhere with my stylus it opens the trash bin. However, that isn't really all that useful. What do I need to to in order to get my tablet working normally on 10.04? I have spent hours searching around for some instruction but everything was for older versions and the instructions didn't really mean much to me.

---

### Post by Thipp on 2010-05-11
It would seem that if I start my computer and the Ubuntu login screen comes up I have the same stylus limitation (no cursor movement and it only clicks the bottom right corner of the screen). The same is true when I log into my account. However, if I then hit the switch user button to kick myself back out to the login screen I suddenly have regular stylus interaction. It goes away again as soon as I log back in though.

---

### Post by Favux on 2010-05-11
Hi Thipp,

Welcome to Ubuntu forums!

Let's look at the output of:
```
xinput --list
```
in a terminal.  Also check in Synaptic Package Manager that you have xserver-xorg-input-wacom installed.

Hope this is helpful.

---

### Post by Thipp on 2010-05-11
I do have xserver-xorg-input-wacom installed. The input list comes up as this:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=14    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

So it shows both the pen and the eraser part of the stylus but other then seeing that the system recognizes them I am not sure what to do with that knowledge.

---

### Post by Favux on 2010-05-11
Hmmm.  With that output from xinput I would think your stylus and eraser should be working.  What's the output in a terminal of?
```
xsetwacom list
```

---

### Post by Thipp on 2010-05-11
Serial Wacom Tablet eraser ERASER
Serial Wacom Tablet STYLUS

I just dual booted Ubuntu on this tablet but I have been running Windows 7 on it for months and I have run into a similar (perhaps even the same) problem before on games set to use relative mouse movements rather then absolute movements. The stylus is measured on an absolute scale. So the cursor flys around the edge of the screen like crazy and can't interact normally in any usable manor. So my guess would be that somewhere I need to tell the system to register an absolute measurement.

---

### Post by Favux on 2010-05-11
Absolute should be default.  Does entering:
```
xsetwacom set "Serial Wacom Tablet" Mode Absolute
```
in a terminal fix it?

---

### Post by Thipp on 2010-05-11
It accepts the command but nothing changes.

---

### Post by Favux on 2010-05-11
OK, let's take a look at your Xorg.0.log.  It's in /var/log/.  Right click on it and compress it with Create Archive.  Then post it with Manage Attachments.  It sounds like the wacom driver isn't picking your tablet up correctly.  This will let us check that.

---

### Post by Thipp on 2010-05-11
Here it is. Thanks for all your help so far.

---

### Post by Favux on 2010-05-11
Hi Thipp,

Not a problem.  OK , this:
```
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
```
may indicate the FUJxxx Product ID may not be in the default 0.10.5 xf86-input-wacom driver in Lucid.  Then it looks like the evdev driver is picking up the stylus:
```
II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
```
And the same happens with eraser.

I wonder if it has been added recently?  I know they submitted more Fujitsu identifiers to the kernel a month or so ago.  I wonder what would happen if we cloned the git repository?  I'm pretty sure I saw a recent commit with Fujitsu identifiers too.

Let's try something else first.  The configuration file is called 10-wacom.conf.  It is located at /usr/lib/X11/xorg.conf.d/.  Let's see what happens if we make a change I saw another user use successfully.  Change the serial snippet/section from:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection
```
to:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7|Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

```
Save and reboot.  To edit use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
Let's see if we can get the wacom driver to pick it up that way.

---

### Post by Thipp on 2010-05-12
My file looks like this and not that:

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

---

### Post by Thipp on 2010-05-12
Just for the hell of it I did try replacing that section with yours and it didn't fix the problem.

---

### Post by Favux on 2010-05-12
Ahhh.  That's interesting.  I wonder if Lucid updated from 0.10.5 to 0.10.6 xf86-input-wacom, which the X driver for Wacom for Lucid's Xserver 1.7?

I checked the commit log and sure enough the Fujitsu identifiers were added to xf86-input-wacom 2 weeks ago, which is after 0.10.6.  So we can probably get it to work if you clone the git repository.  That's described in Appendix 5 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Read the section on Lucid near the top first.  It's not as complicated as it looks.  There's just a lot of explanation woven in.  So reread it several times until you get a feel for it.  And remember since you have a serial tablet you do not need the wacom.ko.

---

### Post by Thipp on 2010-05-12
I will take a look at that. Oddly, I did get it sort of working. I took the value that was in your suggestion for MatchProduct and put it in place of both Wacom class and Wacom serial class on my end and now it works but only if I restart my computer, log in, then switch out of my user and then log back in again. Then suddenly the stylus works fine until I restart the computer again and I have to jump through the same hoops.

---

### Post by Thipp on 2010-05-12
Hrm, I tried to follow the instructions there but somehow made a mess of things. Now the tablet is 100% unresponsive to the stylus and I get an error message when I restart my computer that my config files are screwed up so I have to run in low graphics mode.

---

### Post by Favux on 2010-05-12
Hi Thipp,

That's a new one on me.  A linuxwacom compile wouldn't install any config files, you'd have to do that manually.  I've wracked my brains and this is what I've come up with.  Maybe xf86-input-wacom is installing the .conf file.  I know they talked about changing the number from 10 to 20 or 50-wacom.conf.  Check in the .conf directory and see if there are two wacom.conf's.  Maybe with the number changed it didn't overwrite or remove your 10-wacom.conf?  If so delete one of them, presumably the original one.

---

### Post by Thipp on 2010-05-12
Well I figured that maybe I had messed something up so I went ahead and did a fresh install. I then followed the instructions from [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)  as best as I understood them. I followed the steps in appendix 5 for installing xf86-input-wacom and cloning the git. I redid the changes to /usr/lib/x11/xorg.conf.d/10-wacom.conf that you had me try earlier and that was also in that guide and I tried editing /etc/x11/xorg.conf using the generic tablet pc example provided. I find myself in the same spot again, I now have no tablet functionality at all, when I check xinput --list it no longer shows the wacom entries. Also, when I boot into ubuntu I get the message again saying that there is an error parsing the config file and that it has to boot into low graphics mode.

---

### Post by Favux on 2010-05-12
Hi Thipp,

I'm going to guess that it was editing the xorg.conf that broke X for you.  That is a sensitive file.  Can you post your original working xorg.conf (I hope you made a backup) and your current one?  We should be able to fix it.

---

### Post by chaosdx on 2010-05-16
Just want to add my $0.02 to the original issue.

I have the exact same model of laptop, but I went to Lucid through normal dist-upgrade from Karmic. In Karmic, I got my pen to work (can't recall if the pressure sensitivity really worked, but the pointer behaved normally).

Things, however, broke in the exact same way as described above in the OP post -- after the upgrade.

I wonder if, under those circumstances, a new version from the git repository can help? It's not like the pen had never worked with prior versions of the driver (or am i missing something here? was there a drastic change?).

Could anyone give a clarification? Thanks in advance.

**ETA: (partially solved)**

I compiled the driver without any issue, it didn't hurt, didn't help either. However, after a careful consideration of the problem, I had to decide that the driver itself wasn't the issue - the stylus is NOT in relative mode, in fact.

The issue seems to be that, without wacomcpl (so far in Lucid), there is no way to easily calibrate the stylus, and the default combo of input resolution and BottomX/BottomY produces the observed result: about a square inch of the left-top input area maps to the whole screen.

Thus, I got it to map the screen more or less correctly by:

```
xsetwacom --set "Serial Wacom Tablet" bottomx 24576
xsetwacom --set "Serial Wacom Tablet" bottomy 18432
xsetwacom --set "Serial Wacom Tablet eraser" bottomx 24576
xsetwacom --set "Serial Wacom Tablet eraser" bottomy 18432

```

-- which will have to be included in my .xinitrc file to autostart, I gather.

But after this, my "primary" stylus and eraser buttons doesn't seem to work ("middle/right" stylus button works perfectly). I'll try to alter sensitivity to see what it can do. (The button mapping seems to be correct, as far as I can tell.)


**P.S.** Just in case someone tries it, by "compiling the driver without any issues" I mean I had to substitute

```
make && make install 
```
in the tutorial for 
```
make && sudo make install
```
otherwise, it errored out.

---

### Post by Favux on 2010-05-16
Hi chaosdx,

Nice work, and thanks for the update.  It's not clear to me why you had to use sudo make install instead of make install.  What errors were you getting?

---

### Post by chaosdx on 2010-05-17
> **Favux said:**
>   It's not clear to me why you had to use sudo make install instead of make install.  What errors were you getting?

```
~/wacomdrv/xf86-input-wacom$ make install
Making install in conf
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/home/kami/wacomdrv/xf86-input-wacom/conf'
make[2]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/home/kami/wacomdrv/xf86-input-wacom/conf'
make[2]: &#1062;&#1077;&#1083;&#1100; `install-exec-am' &#1085;&#1077; &#1090;&#1088;&#1077;&#1073;&#1091;&#1077;&#1090; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1103; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;.
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
/usr/bin/install: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1076;&#1072;&#1083;&#1080;&#1090;&#1100; «/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi»: &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;
make[2]: *** [install-dist_fdiDATA] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/kami/wacomdrv/xf86-input-wacom/conf'
make[1]: *** [install-am] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/kami/wacomdrv/xf86-input-wacom/conf'
make: *** [install-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1

```

Sorry for the localised system :) It essentially says "cannot delete «/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi»: access denied" and subsequently exits with Error 1 .. Error 2 ... Error 1

---

### Post by chaosdx on 2010-05-17
Still can't get the "1st button" of stylus/eraser to work normally. It doesn't show up as an event in "xinput test".

I can confirm, though, that after logging out from gnome session both buttons start working immediately, and continue to work after a re-login.

Is there anything I can check about that? Not very convenient...

---

### Post by marcosalvatori on 2010-05-26
I also ran into the problem with the tablet functionality / stylus  not working on my Lifebook T4210.  I did a fresh install of Lucid yesterday.  I started by booting my system with the live CD and after boot up the tablet was working fine so I went ahead with the full install.  It was only after the full install that the tablet functionality was broken. as described in the previous posts. 
Without any changes to the default install.  I can get the cursor to follow the stylus point with the commands described above - xsetwacom --set "Serial Wacom Tablet" bottomx 24576 etc etc.  I cant click with the pointer however -- kind of -- if I bring the tip of the stylus into proximity of the screen and then out of proximity, that action results in a click being registered in the underlying window.
Anyway, Ill just confirm that that easiest thing I have found to get the tablet functionality working is just to log in and then log out.  One can also reboot X with
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
and things work fine as well.  Things that dont correct the problem are booting into the system in safe mode.  So given whats happening Im inclined to think that the driver code and default configuration are correct as is. There seems to be something going on during the os initialization process that has to be understood.

---

### Post by cntmn8td2006 on 2010-06-19
Hello,

I have Fujitsu T4210, and have installed Ubuntu 10.04. The pen works right out of the box but needs some adjustments. There are two issues that I had initially. Note that I did not install any additional drivers, and the solution below works for a clean install of Ubuntu 10.04. 

1. The cursor wanders off to the corner of the screen
       Solution
               Navigate here 
               ```
cd /usr/lib/X11/xorg.conf.d
```
               then open the following
              ```
 sudo gedit 10-wacom.conf
```
               
               compare the 10-wacom.conf to the text below
               
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"

        Option "Button1" "1"
	 Option "Button2" "2"
	 Option "Button3" "3"
        Option "TopX" "0"
        Option "BottomX" "24700"
        Option "TopY" "0"
        Option "BottomY" "18600"
 
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```

Adding

        ```
Option "Button1" "1"
	 Option "Button2" "2"
	 Option "Button3" "3"
        Option "TopX" "0"
        Option "BottomX" "24700"
        Option "TopY" "0"
        Option "BottomY" "18600"
```

will calibrate your stylus. Save the file, close the file, and restart. The cursor should now follow the stylus.

2. The stylus behaves as if it is clicked all the time.
     Solution 
            Add the following line just like "Option 'Button1' '1'."
         ```
Option "PressCurve" "0,15,85,100"
```

    Unfortunately, I am experiencing a side effect. After I reboot my machine and first use the stylus the system appears to panic. It then goes back to the log in screen, I log in, and the stylus can be used no problem.

3. The screen rotation is not automated.
          A possible solution would be to create a script that rotates the screen once clicked. It worked for me in Ubuntu 9.04, but I have not tried it on Ubuntu 10.04.


Please let me know how the solutions above work for your Tablet PC.

---

### Post by chaosdx on 2010-06-20
> **cntmn8td2006 said:**
> 

1. The cursor wanders off to the corner of the screen
       Solution
               Navigate here 
               ```
cd /usr/lib/X11/xorg.conf.d
```
               then open the following
              ```
 sudo gedit 10-wacom.conf
```
               
               compare the 10-wacom.conf to the text below


I added the calibrating section to the 10-wacom.conf, but it works no better than the manual "xsetwacom" I had tried before -- that is, the cursor moves, but button1 and eraser clicks are not recognized as events at all.

The trouble with trying your second solution is that you admitted you had to logout/login/restart GDM, and as we in this thread know from the previous experience :) this action "fixes" the stylus with no further action required. Thus, it can't be trusted as a fix :).

---

### Post by chaosdx on 2010-06-20
Subsequently, I tried to compare Xorg.log files between "fresh reboot, not working properly" and "gdm restart, working ok" and what I got was this (diff output).

```
< (II) Serial Wacom Tablet eraser: **serial tablet id 0x93**.
---
> (WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
> (WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
> (II) Serial Wacom Tablet eraser: **serial tablet id 0x90**.
481,482c483,484
< (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=0 maxY=0 maxZ=0 resX=2540 resY=2540  tilt=disabled
< (--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=0 bottom Y=0 resol X=2540 resol Y=2540
---
> (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=24576 maxY=18432 maxZ=127 resX=2540 resY=2540  tilt=disabled
> (--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
485c487
< (--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=0 bottom Y=0 resol X=2540 resol Y=2540
---
> (--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=24576 bottom Y=18432 resol X=2540 resol Y=2540
```

Note the difference in "serial tablet id". It occurs consistently, but I'm not sure what to make of it, or whether there are more logfiles I could look at.

---

### Post by Favux on 2010-06-20
Hi chaosdx,

We're seeing the same:
```
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.

```
also.  We added some debug lines and then got a floating point exception.  I'd love to see what your output is like and if it replicates this.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1513140](http://ubuntuforums.org/showthread.php?t=1513140)

---

### Post by cntmn8td2006 on 2010-06-20
I tried using the following command

```
xsetwacom set "Serial Wacom Tablet" PressCurve "0 15 85 100"
```

Unfortunately, I get sent back to the log in screen. 

When modifying the "PressCurve" option the default value is "0,0,100,100." Is there anyway of finding the origin of this default setting? Specifically, where and what file is it?

---

### Post by chaosdx on 2010-06-20
> **Favux said:**
> Hi chaosdx,

We're seeing the same:
```
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.

```
also.  We added some debug lines and then got a floating point exception.  I'd love to see what your output is like and if it replicates this.  See this thread:  [http://ubuntuforums.org/showthread.php?t=1513140](http://ubuntuforums.org/showthread.php?t=1513140)

I compared my logfiles to the ones posted in the thread. My issue is different: when the "tablet id" is set to 0x93 (fresh reboot), the eraser error doesn't show up in the logs, but the stylus/eraser doesn't work as intended (as I've mentioned earlier in this thread).

And when the id is 0x90 (after logout/login), the error manifests itself in Xorg logs, but everything works perfectly: no pressure issue I would need to solve, either.

However, if some extra input on the pressure curve option is needed, I will get a fresh copy of source (since git is set up already :p) and post my results to the relevant thread.

---

### Post by Favux on 2010-06-20
They just did a commit on the PressureCurve:  [http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTik1ukqndNopQGzHc6FaWhWELKBeEEehxA2UvbTi%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTik1ukqndNopQGzHc6FaWhWELKBeEEehxA2UvbTi%40mail.gmail.com&forum_name=linuxwacom-devel)

Maybe that will fix it?  To clone the git repository see Appendix 5 in the [linuxwacom How TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by chaosdx on 2010-06-21
Summarizing, my findings from building xf86-input-wacom 0.10.7 from git are as follows:

[LIST]
[*]after a reboot, the tablet is wrongly initialized as having touch (0x93), no error in logs is reported. subsequently, the reported capabilities aren't parsed correctly, and the device behaves as described by the OP and others in this thread.
[*]after an attempt to re-initialize the device (after X restart), the detection code fails with a timeout, an error "Waited too long for answer (failed after 3 tries)" is reported in logs.
subsequently, "tablet id" falls back to "default" (0x90), which is either true for T4210 or close enough to truth to work properly for most of the users. the device behaves as expected.
[*]adding any significant debugging output to the detection code slows it down enough so that timeout errors "Waited too long for answer (failed after 3 tries)" appear immediately after a reboot. subsequently, "tablet id" falls back to "default" (0x90), see above.
This fact makes it very hard to trace anything.
[/LIST]

Moreover, after a few compiled versions, my pressure curve isn't behaving as expected any more, even with 0x90 identifier.

I removed the changed source and did a clean clone/compile. However, when using any pressure-aware graphics program, it is easy to see that pressure sensitivity (eraser and stylus both) quickly goes from mix to max, and then immediately clips off to 0. xsetwacom registers changes I make to PressCurve, but there is no visible effect.

Wonder where to dig for that...

---

### Post by oroberos on 2010-10-19
I'm also using the T4210 and I solved the problems with disabling auto-login. I installed the fsc-btns-kernel-source package from the fjbtndrv-package I found on Google. With xbindkeys I binded the rotate-button to the rotation.py (attachment). My /usr/lib/X11/xorg.conf.d/10-wacom.conf is also attached.

Auto-rotation doesn't work at the moment, but when I get it working, I am going to post it here.

Hope it helps somebody :).

Edit: At first I installed the default wacom-drivers from the Ubuntu reps and then the newest linuxwacom-drivers from the git-repository with the following commands:
```

git clone gite://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
./configure
make
sudo make install

```

After that I changed the 10-wacom.conf. And of course I am also using Ubuntu 10.04 (because of LTS).

---

### Post by cntmn8td2006 on 2010-10-20
Does your fix resolve the issue in the following post?

[http://ubuntuforums.org/showthread.php?t=1513140&highlight=presscurve](http://ubuntuforums.org/showthread.php?t=1513140&highlight=presscurve)

---

