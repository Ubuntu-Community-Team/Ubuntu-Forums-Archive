---
title: "Ubuntu 9.04 on Thinkpad T60, Screen flickering"
date: 2009-04-26
forum: Hardware
---

### Post by m.h.shams on 2009-04-26
Hi everyone,

i just installed 9.04 on my Thinkpad T60p,
my Graphic card is ATI mobility X1300 or X1400 (sorry, i forgot the exact number).

there a little flickering on right side of the monitor.

from right bottom to right up corner. (with about 2cm length)


any idea ?

thanks all,

---

### Post by Shwan.c on 2009-04-26
> **m.h.shams said:**
> Hi everyone,

i just installed 9.04 on my Thinkpad T60p,
my Graphic card is ATI mobility X1300 or X1400 (sorry, i forgot the exact number).

there a little flickering on right side of the monitor.

from right bottom to right up corner. (with about 2cm length)


any idea ?

thanks all,

do more tst , live cd , on windows, using another pc / monitor and explain more

---

### Post by kha on 2009-04-26
Hi,

I have the same issue also. I've got a Dell Inspiron 6400 with an ATI Mobility Radeon X1300.

I've upgraded to Ubuntu 9.04 and had the issue with the new ATI drivers which dropped support for these cards. The ATI Catalyst Driver 9.3 was the one used in Ubuntu 8.04. In Ubuntu 9.04 they upgraded to ATI Catalyst Driver 9.4 (to be compatible with the new Xorg i think ?), and this version do not support my card...

So currently to make the video works i must remove the package xorg-driver-fglrx and use this xorg.conf file:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"ati"
EndSection
```

My display flicker sometimes in example when i switch window to window, when i change tab to tab in firefox, when i minimize or maximize windows, when i move windows.

Do you have an idea ? Are there some options i could try in my xorg.conf file ? Are there some other settings i should check ?

Thanks !

---

### Post by m.h.shams on 2009-04-26
> **kha said:**
> Hi,

My display flicker sometimes in example when i switch window to window, when i change tab to tab in firefox, when i minimize or maximize windows, when i move windows.



my problem is same. when i move window or open new tab in firefox or ...   but its just in right side of my monitor. 

i didn't change xorg.conf or any other thing. it is default behavior.

---

### Post by vbmendes on 2009-04-27
I have a Dell Inspiron e1505 and this same video card: ATI x1300

And experiencing the same problems, the right side of the screen start to flicker wher I am changin window, tab or anything. I think it occurs when the computer is processing something.

---

### Post by barbadechiva on 2009-04-27
Same here. On an Averatec (with a VIA K8N890 chipset). It's fairly unusable, at present.

---

### Post by ryanbin on 2009-04-28
I'm having the same issue.  Flickering / white lines / screen tearing on the right side of my monitor after upgrade to jaunty.  Originally I had the fglrx driver installed with compiz but when the upgrade told me it was incompatible, I exited out of the upgrade, removed the fglrx driver and ran the upgrade without a problem.

Now it flickers on the right side of the screen intermittently even when I'm not doing anything, and seems to do it more when I use the scroll wheel in certain applications or open new firefox tabs.  It's particularly active when I'm working in remote desktop windows.

I have a HP Compaq dc7700p ultra-slim desktop.

---

### Post by NickWilsdon on 2009-05-04
I'm seeing the same behaviour here on my Dell Inspiron 6400. Flickering on the right hand side - horizontal lines, esp when moving windows about. I notice this is more visible when using Firefox than a normal file explorer window so maybe CPU use activates it. 

I tried installing xorg-driver-fglrx but that borked the graphical login screen. I had to reboot in recovery mode and remove it. 

As the graphics were fine before with 8.10 I assume Jaunty installed something that needs to be deleted. We've been unlucky with this 9.04 upgrade, lost sound on both machines and had networking/wifi performance degrade. We may roll back to 8.10 until all these quirks are worked out.

---

### Post by topplehat on 2009-05-05
I am also having the same problem, and it's rather obnoxious.  As many others, I am running on a Dell Inspiron 6400 with the ATI x1300.

---

### Post by barbadechiva on 2009-05-05
Still no leads on this? I'm either reverting to 8.10 (which was working just fine) or jumping to Fedora this afternoon. It's out of control. Listening to an .mp3 on Totem, I got a constant flicker with nasty horizontal lines and an occasional whole-screen flash. Very, very unpleasant.

---

### Post by marplede on 2009-05-08
Same symptoms here.  I have a Toshiba Satellite A215 laptop.  Very frustrating when switching tabs or windows or sometimes even starting a program.  I should have stayed with 8.10.

---

### Post by barbadechiva on 2009-05-09
I installed Fedora 10 and had the same problem, and parallel discussions in the Fedora universe seem to pin the problem on the latest version of Xorg. I'm guessing Ubuntu is using the same thing. 

Switched back to 8.10 and now I love my laptop again. I didn't mean for that to rhyme.

---

### Post by niclas_ on 2009-05-17
I had the same problem here but I found a solution on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351423](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351423)

Switching from EXA to XXA or adding "greedy" migrationheuristic in xorg.conf fixes the flickering.[B]
[/B]

---

### Post by Makrin on 2009-05-17
Jaunty working fine here. New installation.Using t60 with x1300.
Compiz,video work great, no flickering.No 3d support yet though.
Using latest drivers from volden ppa
[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)


I need 3d so went back to Ubuntu 8.10  kernel 2.6.28.7(using kernelcheck) 
Everything is working good :-)
tried 2.6.28.10 but couldn't get 9-3 driver to work...

---

