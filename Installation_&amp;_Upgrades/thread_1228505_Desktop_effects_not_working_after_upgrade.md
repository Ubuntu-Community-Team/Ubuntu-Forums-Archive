---
title: "Desktop effects not working after upgrade"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by Notre on 2009-08-01
Hello,

I'm sorry if I have the wrong forum.  Please direct me to the appropriate place, if I'm in the wrong one.

I upgraded from Hardy Heron to Intrepid Ibex and then to Jaunty Jackalope.  I noticed when upgrading to Intrepid Ibex that the desktop events were not working, but they had worked fine with Hardy Heron.  I ignored the problem and continued to upgrade to Jaunty Jackalope.  Unfortunately, the problem persisted.

A google search found the compiz-check tool.  I downloaded and ran that.  It did report a problem and I'm embarrassed to say I didn't record the error message.  I believe it mentioned by driver was black listed, and then mentioned some other potential problem.  I chose the option to skip the check.  Now when I try to turn on desktop effects, it hangs the system.  

After rebooting, I re-ran the compiz-check tool, but now it reports everything okay (presumably it's skipping some checks now).  This is what it reports now:

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

I remember it was in the last check' hardware/setup problems' that the problem was originally discovered.  

I don't know why the compositing effects aren't working now, but was with the earlier release.  I'd like to go back so I'm not skipping the Compiz checks, but I don't know how to do that.  I'm hoping the additional information the tool originally provided will aid someone in telling me how to get it working with Jaunty Jackalope.

Thank you!
Notre

---

### Post by tommcd on 2009-08-01
There is a regression in the Intel driver that ships with Jaunty that impairs 3D acceleration for many Intel video chips. So the Ubuntu devs blacklisted a number of Intel graphics cards from working with compiz so you don't experience system lockups when running desktop effects. There is a work around though. It involves reverting to the older intel driver. See this:
[http://ubuntuforums.org/showthread.php?t=1128253](http://ubuntuforums.org/showthread.php?t=1128253)
and the page from the Ubuntu wiki here:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
The other option is to not use compiz and desktop effects. My intel 945G in my laptop works fine in Jaunty with desktop effects disabled. I never use any desktop effects anyway.
There is a way to force compiz to skip the checks; but I would not recommend it as it will likely cause your system to lockup, as you have already experienced.

And welcome to the Ubuntu forums!

---

### Post by Notre on 2009-08-01
Thank you very much tommcd for taking the time to answer my question!

I certainly don't need compiz, but I do enjoy the eye candy and the solid (no flicker)/clean window transitions you get with the compositing.  So I'm hoping to get it working, somehow...

I followed the instructions on [https://wiki.ubuntu.com/ReinhardTart...telDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").  I didn't notice any error messages in the terminal window when running the various commands.  

Unfortunately, when I went tried to turn on desktop effects, I still got the hanging.  I think the compiz checks are still disabled, because of the option I selected in compiz-check, but I don't know how to turn off the 'ignore' the skip checks.  Any ideas?

After running compiz-check again, I get the same message to the terminal window as in my original post.  Is there any way to tell if I have successfully reverted to the earlier Intel driver?

I also don't know if I need to do anything with the  xorg.conf file (or what to do with it), so I've done nothing so far.  Do you think I should do something with this file?

Thanks again for your help!

---

### Post by tommcd on 2009-08-02
> **Notre said:**
> 
Unfortunately, when I went tried to turn on desktop effects, I still got the hanging.  I think the compiz checks are still disabled, because of the option I selected in compiz-check, but I don't know how to turn off the 'ignore' the skip checks.  Any ideas?
Disabling compiz-checks sgould not cause it to fail, as far as I know. The compiz-check is there to make sure everything is ok compiz wise. So the checks are there to stop compiz if things are not ok, not to disable compiz if everything is ok.
> **Notre said:**
> 
  Is there any way to tell if I have successfully reverted to the earlier Intel driver?

To see what intel driver you are using, run this in terminal:
```
aptitude show xserver-xorg-video-intel
```
and check the version number it reports. On my system (with the current intel driver, not the old one, it reports version:2:2.6.23-0ubuntu9.3. If it shows a 2.6 driver, then you have not managed to install the 2.4 driver.
> **Notre said:**
> 
I also don't know if I need to do anything with the  xorg.conf file (or what to do with it), so I've done nothing so far.  Do you think I should do something with this file?

As long as the driver in xorg.conf is listed as "intel" you should not need to change anything.
I'm not exactly an expert on compiz though. If no one else with more experience with compiz offers any help here, you may want to ask over on the compiz forums or check their wiki:
[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)
There is lots of stuff pertaining to Ubuntu over there.

---

### Post by Notre on 2009-08-02
Thanks again for your reply.  It looks like I might have failed to successfully install the Intel 2.4 driver.  Does that look to be the case? I just noted that the 'State' says not installed. I guess I should try the steps again...?

Package: xserver-xorg-video-intel
**State: not installed**
**Version: 2:2.6.3-0ubuntu9.3**
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 1323k
Depends: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.5), libdrm2 (>= 2.3.1),
         libpciaccess0 (>= 0.8.0+git20071002), libxext6, libxv1, libxvmc1,
         xserver-xorg-core (>= 2:1.5.99.901)
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
           2:1.9.91-1), xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting
Replaces: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
          xserver-xorg-video-i810 (< 2:1.9.91-1),
          xserver-xorg-video-i810-modesetting,
          xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-5
Provided by: xserver-xorg-video-intel-2.4
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
 
 This package also provides an XvMC (XVideo Motion Compensation) driver for i810
 and i815 chipsets. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xf86-video-intel driver module.

---

### Post by Notre on 2009-08-02
In addition to my last post, where I believe I have not successfully installed the earlier driver, I have some further questions on the xorg.conf file.  I'm not sure what folder to look for this file.  I found one file with this name in /etc/X11.  The uncomment section of that file looks like this:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

There's also a couple more xorg.conf files:
xorg.conf.dist-upgrade-200907311101
xorg.conf.dist-upgrade-200907311101

Are these relevant as well?  Which file is most current?  Is there more xorg.conf files in other folders?  Thanks!

---

### Post by tommcd on 2009-08-03
> **Notre said:**
>   It looks like I might have failed to successfully install the Intel 2.4 driver.  Does that look to be the case? I just noted that the 'State' says not installed. I guess I should try the steps again...?

Package: xserver-xorg-video-intel
**State: not installed**
**Version: 2:2.6.3-0ubuntu9.3**

If the 2.6 driver is not installed, then I would think that you must be using the 2.4 driver. What is the output of:
```
dpkg -l xserver-xorg-video-intel
```
and:
```
aptitude search xserver-xorg-video-intel
```

---

### Post by tommcd on 2009-08-03
> **Notre said:**
> In addition to my last post, where I believe I have not successfully installed the earlier driver, I have some further questions on the xorg.conf file.  I'm not sure what folder to look for this file. 
The correct working file is /etc/X11/xorg.conf. As far as I know, you should not need to edit xorg.conf. The tutorial I linked to did not mention this. The tutorial does state though that this may not work for everyone. The intel graphics problems in Jaunty (which seem to persist in Karmic alphas) are well documented:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_intel&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_904_intel&num=1)
[http://www.phoronix.com/scan.php?page=article&item=intel_q309_flakes&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_q309_flakes&num=1)
> **Notre said:**
> 
There's also a couple more xorg.conf files:
xorg.conf.dist-upgrade-200907311101
xorg.conf.dist-upgrade-200907311101
Are these relevant as well?  Which file is most current?  Is there more xorg.conf files in other folders?  Thanks!
Well, post the output of those other xorg.conf files as well and lets look at them.
 You can try them out if you like by running:
```
sudo cp /etc/X11/ /etc/X11/xorg.conf.bak
```
This will backup your current xorg.conf to be safe. Then to try the others, just run:
```
sudo cp /etc/X11/xorg.conf.dist-upgrade-200907311101 /etc/X11/xorg.conf
```
Then reboot. You can try the other one the same way. Use tab autocompletion so you don't need to type the exact file name. Just start typing the path to the file and hit the tab key. Type a few more letters for the file path and hit tab again, etc, ubtul it selects the file you want. 
If they are not better, you can go back to your original xorg.conf like this:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
and reboot. If X won't start, then run that command from recovery mode to revert to the original xorg.conf.

The /etc/X11 directory is the only place that you should have xorg.conf files.

There is one more thing you could try. But, as this link says, it tends to be very unstable and just may lockup your X server:
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
Some people have had some good results with this though. Again, be sure to keep a known working copy of your xorg.conf backed up so you can easily revert to it if things don't work.

---

### Post by Notre on 2009-08-03
Thank you so much again for taking your time to answer my questions!!:D

The output of 

dpkg -l xserver-xorg-video-intel

is 

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  xserver-xorg-v 2:2.6.3-0ubunt X.Org X server -- Intel i8xx, i9xx display d



The output of 

aptitude search xserver-xorg-video-intel

is

c   xserver-xorg-video-intel        - X.Org X server -- Intel i8xx, i9xx display
i   xserver-xorg-video-intel-2.4    - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-intel-2.4-db - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-intel-dbg    - X.Org X server -- Intel i8xx, i9xx display


The two xorg.conf files are: 

xorg.conf.dist-upgrade-200907311101:

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

 xorg.conf.dist-upgrade-200907311529:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

I haven't had a chance to try the two alternative xorg.conf files nor the UxaTesting thing yet, but I will. Thanks again!

---

### Post by Notre on 2009-08-04
/etc/X11/xorg.conf.dist-upgrade-200907311529 is the same as /etc/X11/xorg.conf.

/etc/X11/xorg.conf.dist-upgrade-200907311101 is different, in that these lines are not commented out:

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

I don't expect this would make any difference to the compiz issues.

I'm not clear on the output of:

dpkg -l xserver-xorg-video-intel


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  xserver-xorg-v 2:2.6.3-0ubunt X.Org X server -- Intel i8xx, i9xx display d

It seems to suggests something went wrong.  Do you agree?

---

### Post by tommcd on 2009-08-05
> **Notre said:**
> 
I don't expect this would make any difference to the compiz issues.

I don't either. Those sections of xorg.conf deal with the options for your keyboard and mouse and do not affect the use of the graphics driver.
> **Notre said:**
> 
I'm not clear on the output of:

dpkg -l xserver-xorg-video-intel


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  xserver-xorg-v 2:2.6.3-0ubunt X.Org X server -- Intel i8xx, i9xx display d

It seems to suggests something went wrong.  Do you agree?
The **rc** before the **xserver-xorg-v 2:2.6.3-0ubunt** means that the package has been "r" removed, and that the "c" config files still remain, which is the expected output if a package has been removed:
[http://www.linuxquestions.org/questions/debian-26/dpkg-what-does-a-status-of-rc-mean-355593/](http://www.linuxquestions.org/questions/debian-26/dpkg-what-does-a-status-of-rc-mean-355593/)
Your output of "aptitude search xserver-xorg-video intel" indicates that the 2.4 driver has an "i" before it, which indicates that it is installed. A "p" before a package indicates that it is purged, or has never been installed.
 Your output of "aptitude show xserver-xorg-video-intel" indicated that the 2.6 driver was not installed. So it looks like you are running the 2.4 driver now.

Do you have direct rendering enabled at this point? Run:
```
glxinfo | grep -i direct
```
to find out. It should return "yes".

---

### Post by Notre on 2009-08-05
The output of 
glxinfo | grep -i direct
is


Failed to initialize GEM.  Falling back to classic.
direct rendering: Yes

I haven't tried the UXA approach yet, but based on the web page you sent me earlier, it seems to suggest this is for improving graphics performance.  I'm happy enough with the performance of the graphics in Hardy, and even now, except I'd like to get compiz working (maybe that's considered performance too).  Do you think this might help in this regard?  If so, I'm very willing to try it.

---

### Post by tommcd on 2009-08-06
> **Notre said:**
> The output of 
glxinfo | grep -i direct
is
Failed to initialize GEM.  Falling back to classic.
direct rendering: Yes

If direct rendering is enabled, then your driver seems to be working. As for the GEM error, an explanation of that can be found here:
[http://bbs.archlinux.org/viewtopic.php?id=59983](http://bbs.archlinux.org/viewtopic.php?id=59983)
[http://ubuntuforums.org/showthread.php?t=890843](http://ubuntuforums.org/showthread.php?t=890843)
I don't get the GEM error when I run the glxinfo command on my laptop. I am still using the intel 2.6 driver though, not the 2.4 driver.
> **Notre said:**
> 
I haven't tried the UXA approach yet, but based on the web page you sent me earlier, it seems to suggest this is for improving graphics performance.  I'm happy enough with the performance of the graphics in Hardy, and even now, except I'd like to get compiz working (maybe that's considered performance too).  Do you think this might help in this regard?  If so, I'm very willing to try it.
Well first off, are you running Hardy or Jaunty???
Your first post said you upgraded from Hardy > Intrepid > Jaunty. This problem should not happen in Hardy if I remember correctly.

The UXA thing may help, as some have reported. As the article I linked to said though, it tends to be unstable, so your mileage may vary.

---

### Post by Notre on 2009-08-06
Thanks for the information on the GEM error.

I'm using Jaunty now.  You're right - I have upgraded from Hardy->Intrepid->Jaunty.  My comment was just that I was happy with Hardy, in terms of desktop effects / compiz.  It's with both Intrepid and Jaunty where I'm seeing the problem.  Sorry for the confusion :D

When I try the UXA approach, should I first move back to the intel 2.6 driver, should I stick with 2.4, or do I need to move up to 2.8?

Also, I finally figured out how to get rid of the "skip checks" option so I can re-run compiz-check to get the error information. Now, with skip checks removed, I get:

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
[B] Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. [/B]

Would you like to know more? (Y/n) 

Answering Y to this says tells me my graphics card might be black listed and gives me the option to skip the compiz blacklist checks.

Note sure if this helps...

---

### Post by tommcd on 2009-08-07
> **Notre said:**
> 
When I try the UXA approach, should I first move back to the intel 2.6 driver, should I stick with 2.4, or do I need to move up to 2.8?
Good question. I suppose you could try it with the 2.4 driver. If it doesn't work you could try it with the 2.6 driver. As for the 2.8 driver, do you have that available from apt-get since you added the ppa repo for the 2.4 driver to your sources.list? To find out if you can get the 2.8 driver from apt-get, run this command:
```
apt-cache policy xserver-xorg-video-intel
```
This will return the installed driver, and the candidate driver that is available. If the 2.8 driver is available to you, it should be listed there. If it is not, then the only way you could get the 2.8 driver would be from the Karmic repos. I would not recommend that. It may have a lot of newer dependencies that may lead to broken dependencies, or a broken X server. I don't know.

I would not expect much from UXA. Upon reading that UXA page on the Ubuntu wiki, one user reported this when trying UXA with your intel 82845G:
> mouse shows up as a few red dots before screen blinks and gdm kicks in (after that mouse is fine), upon logging in through gdm, blank desktop loads, pointer is movable but clicking on the blank desktop does nothing
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
IF you feel brave though, then go for it. You can always remove the UXA stuff from xorg.conf if it causes problems. 
> **Notre said:**
> 
Answering Y to this says tells me my graphics card might be black listed and gives me the option to skip the compiz blacklist checks.

This is because compiz is known to be problematic with the current intel drivers, which is of course the whole problem here.

---

### Post by Notre on 2009-08-07
I tried UXA with both 2.4 and 2.6, but unfortunately neither worked (desktop hung).

According to the results of this command:

apt-cache policy xserver-xorg-video-intel

The only driver available is 2.6 (nothing for 2.8 ).  I'm not brave (nor knowledgeable) enough to try the 2.8 driver from Karmic.

So, at this point, it seems my options would be:

1. Live with Jaunty, without desktop effects
2. Buy a new graphics card that isn't black listed, and disable the internal Intel graphics card
3. Revert back to Hardy

In your experience/opinion, and I expect you can't speak for the Compiz/Ubuntu development community with authority so I'm just looking for your gut feeling, do you think any effort will be made by developers to create a new driver that fixes/worksaround the issues with the Intel graphic cards?  If so, do you think it is likely any fix will work with my presumably quite dated Intel graphics card (compared with newer Intel cards)?

Thank you,
Notre

---

### Post by tommcd on 2009-08-07
> **Notre said:**
> ... do you think any effort will be made by developers to create a new driver that fixes/worksaround the issues with the Intel graphic cards?  If so, do you think it is likely any fix will work with my presumably quite dated Intel graphics card (compared with newer Intel cards)?

I doubt there will be a fix for this in Jaunty. I'm just hoping that they they get these intel driver problems fixed before Karmic is released. According to the testing that Phoronix has done with the alpha releases of Karmic, there has been little, if any, improvement on this issue:
[http://www.phoronix.com/scan.php?page=article&item=intel_q309_flakes&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_q309_flakes&num=1)
These problems are caused by upstream development in the kernel, xorg, and the intel drivers. There is probably not much the Ubuntu devs can do to fix this.

---

### Post by Notre on 2009-08-08
That's what I was afraid of, but kind of expected.

I guess I'll look at my budget and see if I can afford a cheap dedicated graphics card, and check that it's not on the black list.  I see on this page,[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) , a few black listed Intel and ATI cards, so maybe a basic NVidia that supports DirectX 10 (I know this is a MS thing, but I'm thinking it will be an indicator of a decent, "modern" card) might be what I would get.  Hopefully setting it up under Ubuntu to use this new card and not the builtin Intel dedicated card is simple enough.  Either that, or I'll fallback to Hardy and review the latest Ubuntu release in another year's time.

I really want to thank you for all the time you spent trying to help me.  My first experience, despite the outcome, was a very positive one on these forums.

Cheers,
Notre

---

