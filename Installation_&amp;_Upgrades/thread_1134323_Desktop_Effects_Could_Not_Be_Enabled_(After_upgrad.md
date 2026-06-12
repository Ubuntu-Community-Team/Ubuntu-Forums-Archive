---
title: "Desktop Effects Could Not Be Enabled (After upgrade)"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by zalberico on 2009-04-23
Lenovo Thinkpad T61 with Intel X3100.
Had Desktop Effects working fine in 8.10, will not activate in 9.04.

I remember something like this happening way back when I installed 8.10 too and I think I fixed it by installing sudo apt-get install xserver-xorg or xgl something. I can't really remember.  Anyone else have this issue?

Thanks

---

### Post by mysoogal on 2009-04-23
do not reinstall compiz ! you will get a black screen in your next boot ! for now wait for more help.

---

### Post by CK009 on 2009-04-23
Desktop Effects functionality is dependent on installation of the correct video drivers.  If you have an ATI or NVIDIA card, try EnVy.

---

### Post by empty_spaces on 2009-04-23
maybe this might help.
[http://ubuntuforums.org/showpost.php?p=7119458&postcount=10](http://ubuntuforums.org/showpost.php?p=7119458&postcount=10)

---

### Post by kaixi on 2009-04-23
Intel X3100 has been blacklisted on purpose by the Ubuntu dev team due to a critical bug. In other words, it has nothing to do with the upgrade.

Follow the link below for more information:

[http://ubuntuforums.org/showpost.php?p=3614750&postcount=2](http://ubuntuforums.org/showpost.php?p=3614750&postcount=2)

---

### Post by jblackhall on 2009-04-23
This is the bug they're working on fixing, if you're interested: [https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392)

---

### Post by zalberico on 2009-04-23
Thank you.

---

### Post by zalberico on 2009-04-23
>  Re: Gutsy Compizfusion and Dell M1330
The X3000 and X3100 have been blacklisted by compiz-fusion on purpose. The basic explanation is that playing video with desktop effects enabled causes a crash. More on that here:
[http://www.realistanew.com/2007/09/2...ubuntu-update/](http://www.realistanew.com/2007/09/2...ubuntu-update/)

Once you understand the problem, you can enable effects anyway by following the instructions here:
[http://ubuntuforums.org/showpost.php...31&postcount=1](http://ubuntuforums.org/showpost.php...31&postcount=1)

Be aware, however, that if you play some video with effects enabled, something is guaranteed to break.  From above post.

Code to bypass blacklist:
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

I have bypassed the blacklist and now 9.04 is great, I can play video with effects on and the world didn't end.  Nothing bad happened.  Also flash installed and now works correctly, it didn't before this blacklist was bypassed.

---

### Post by Quirinius on 2009-04-24
Thank you, this worked straight away!!!

---

### Post by stukpixel on 2009-04-24
> **kaixi said:**
> Intel X3100 has been blacklisted on purpose by the Ubuntu dev team due to a critical bug. In other words, it has nothing to do with the upgrade.

Follow the link below for more information:

[http://ubuntuforums.org/showpost.php?p=3614750&postcount=2](http://ubuntuforums.org/showpost.php?p=3614750&postcount=2)

My graphic card worked perfectly in ubuntu 8.10.

---

### Post by raintheory on 2009-04-24
Same experience with my T61, the suggested workaround does not seem to have worked either..  still get the message,,,   

Anything I could have overlooked/missed?

EDIT: Seems I got it worked out.  Spoke too soon.  A Logout/Login was all it took for it to work.

---

### Post by eatayeh on 2009-04-25
> **zman14321 said:**
> From above post.

Code to bypass blacklist:
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

I have bypassed the blacklist and now 9.04 is great, I can play video with effects on and the world didn't end.  Nothing bad happened.  Also flash installed and now works correctly, it didn't before this blacklist was bypassed.

That solved mine straight away! thanks a million!

---

### Post by enthdegree on 2009-04-25
Thank you, this worked for me as well. (on my Inspiron 1525) :KS

But if this was marked as a critical bug, does anyone know about the risks involved in enabling this stuff?

---

### Post by zalberico on 2009-05-02
Glad this worked out for everyone :-).

A word of caution though, it may be unrelated but my system broke for what appears to be no reason and the data was unrecoverable.  Back up just in case it's from the integrated graphics stability issue.

---

### Post by cptrohn on 2009-05-08
> **zman14321 said:**
> From above post.

Code to bypass blacklist:
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

I have bypassed the blacklist and now 9.04 is great, I can play video with effects on and the world didn't end.  Nothing bad happened.  Also flash installed and now works correctly, it didn't before this blacklist was bypassed.

OK thanks, i'll give it a shot and see what happens..

---

### Post by monikgtr on 2009-07-02
I just upgraded to 8.10 from 8.04 but I can't enable desktop effects. Whenever I try to do so, I get a pop-up saying "Desktop Effects could not be enabled." 

I've looked for a possible solution in other threads but I can't post anything there anymore... so, this is what I get when I run:

**Compiz**
```
monikgtr@monikgtr-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 

```

**grep -v ^# /etc/X11/xorg.conf**
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

** glxinfo | grep render**
```
monikgtr@monikgtr-desktop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061102 x86/MMX/SSE2

```

If I try to run **SKIP_CHECKS=yes compiz**, I just get a screen with my wallpaper... no panel, no windows, nothing. All I can see is my cursor.

Does anyone know if my card is blacklisted? Is there anything I can do to get compiz working? Thanks in advanced! :)

---

### Post by empty_spaces on 2009-07-02
Have you tried Compiz Check?
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by monikgtr on 2009-07-02
> **empty_spaces said:**
> Have you tried Compiz Check?
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Thanks man! This is what I got after running compiz-check:

```
monikgtr@monikgtr-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. 

Would you like to know more? (Y/n) y 

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n

```

So... I am blacklisted, huh... :/

---

### Post by empty_spaces on 2009-07-02
If you enter "Y" to skip blacklist checks, then you will most likely be able to enable desktop effects.
My card was blacklisted too, but I was able to enable Desktop effects after I entered "Y" to skip the check. I haven't had any issues yet, although it varies from person to person.

---

### Post by monikgtr on 2009-07-02
Didn't work :/ 

When I clicked on enable desktop effects to "normal", I got: "searching for drivers" and then, just got a screen with my wallpaper and my cursor...

---

### Post by empty_spaces on 2009-07-02
In the Compizconfig-Settings-Manager, do you have "Window Decoration" enabled?

---

### Post by monikgtr on 2009-07-02
Yes, it's enabled.

Command: emerald
Decoration windows: any
Shadow windows: any

---

### Post by empty_spaces on 2009-07-02
I don't use Emerald.
In my case, Command = /usr/bin/compiz-decorator

---

### Post by monikgtr on 2009-07-02
Tried to change to the command you're using, but still no good :/ 
Ran checkcompiz again and now got this:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Tried to enable Desktop Effects again but I still get my wallpaper screen without bars or anything else... just my mouse's arrow T__T

---

