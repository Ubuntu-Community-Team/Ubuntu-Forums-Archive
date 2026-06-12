---
title: "compiz error (User error) :)"
date: 2009-05-17
forum: Hardware
---

### Post by LinuxTAd on 2009-05-17
```
thomas@Ubuntu-6600:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2304x960) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 
```I am hoping someone here may be able to help me with this error :KS

my  current xorg.conf:

```
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2304 960
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

```

I currently run a Tri-boot system and would like to keep my Crossfire setup in tact. I have 2 Radeon HD 3870's bridged.

---

### Post by drs305 on 2009-05-17
It looks like it is having trouble with the resolution you are running:
> [noparse]Checking screen 1Comparing resolution (2304x960) to maximum 3D texture size (2048): Failed.[/noparse]

which xorg also shows your resolution of 2304x960.

Have you tried running a slightly lower resolution?

---

### Post by LinuxTAd on 2009-05-17
> **drs305 said:**
> It looks like it is having trouble with the resolution you are running:

which xorg also shows your resolution of 2304x960.

Have you tried running a slightly lower resolution?

Thank you drs! 

After several trial and error attempts I managed to progress a bit :). 



> 
thomas@Ubuntu-6600:~$ X -version
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Ubuntu-6600 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
> 
thomas@Ubuntu-6600:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1952x864) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity I am working on two monitors and trying my best to get a 2nd monitor of the same size. I have as my main a 22" widescreen, and as my secondary I think it is a 15 LCD.

Any ideas as to this new error?

---

### Post by LinuxTAd on 2009-05-17
Attached is xorg log file as well.

---

### Post by drs305 on 2009-05-18
LinuxTAd,

Glad we made some progress. I am not a compiz expert, especially dual-screen. I did a search of "Software rasterizer detected, aborting" with the advance search feature of ubuntu search, using the past month. I came up with several posts. One user solved it by uninstalling metacity (though that wouldn't be my choice, at least initially). Other users tried other methods.

One user was able to use his original display settings by disabling a section in xorg ([http://ubuntuforums.org/archive/index.php/t-1115208.html    post from 0939 on 4/30)]("http://ubuntuforums.org/archive/index.php/t-1115208.html")

I'd take a look at all the results, expand it to the last year if you don't find good solutions, and post back with further info if you still need some help. You could also try posting in the Multimedia and Video forum. It's not as heavily traffic-ed but the readers are probably more in tune with your issue in that forum.

Best of luck.

---

### Post by LinuxTAd on 2009-05-19
> **drs305 said:**
> LinuxTAd,

Glad we made some progress. I am not a compiz expert, especially dual-screen. I did a search of "Software rasterizer detected, aborting" with the advance search feature of ubuntu search, using the past month. I came up with several posts. One user solved it by uninstalling metacity (though that wouldn't be my choice, at least initially). Other users tried other methods.

One user was able to use his original display settings by disabling a section in xorg ([http://ubuntuforums.org/archive/index.php/t-1115208.html    post from 0939 on 4/30)]("http://ubuntuforums.org/archive/index.php/t-1115208.html")

I'd take a look at all the results, expand it to the last year if you don't find good solutions, and post back with further info if you still need some help. You could also try posting in the Multimedia and Video forum. It's not as heavily traffic-ed but the readers are probably more in tune with your issue in that forum.

Best of luck.

thank you! I will need alot of luck for sure :p

---

