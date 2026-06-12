---
title: "ThinkPad T410 Screen Brightness"
date: 2010-02-06
forum: Hardware
---

### Post by dcast on 2010-02-06
I'm having a little trouble with the screen brightness of my new thinkpad T410. Using the hotkeys (fn + Home or fn + End) the applet shows that the screen brightness is changing, however the brightness stays at maximum. I'm running Ubuntu 9.10, with 2.6.32-19. Has anyone had a similar problem? Also the screen brightness applet in gnome does not have any affect.

Thanks in advance.

---

### Post by steve0921 on 2010-02-10
I am having this problem too, since activating the nvidia proprietary drivers. Brightness worked fine before I did so.

---

### Post by dcast on 2010-02-10
There is some more discussion on the T410 in this thread:

[http://ubuntuforums.org/showthread.php?t=1383110&page=1](http://ubuntuforums.org/showthread.php?t=1383110&page=1)

Doesn't look like too many people have the nvidia graphics card, though but hopefully a solution will present itself.

---

### Post by nomnex on 2010-02-21
Do you mind opening a bug on launchpad to troubleshoot the issue? The model is very new.

[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

There is an unrelated bug report with [FONT=monospace]an [/FONT]Intel Corporation Core Processor Integrated Graphics Controller

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/518201](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/518201)

Nothing about FN keys/panel applet (+nvidia card) not working so far

Workaround: can you change the brightness either entering the BIOS menu at boot-time, either entering a tty console after log-in to GNOME?

Enter a console
```

Ctrl+Alt+F2

```Exit the console
```
Ctrl+Alt+F7
```

---

### Post by trampgeek on 2010-06-29
I have the same problem (brightness function keys display an onscreen applet that ramps a brightness display up and down, but has no effect on the actual screen brightness). System:  Ubuntu 10.04 on Lenovo T410 core i5 with nVidia NV34 graphics (GeForce FX 5200); nVidia proprietary drivers.

I can confirm that the workaround (switch to a console with CTRL/ALT/F1, adjust brightness, switch back with CTRL/ALT/F7) works just fine. Many thanks for that.

---

### Post by SephoD on 2010-08-09
Same problem here, started when I installed the nvidia proprietary driver. Running 10.4 on T410. The switch to console, change brightness, switch back trick works, but is pretty annoying.

---

### Post by rifcoder on 2010-08-28
Did someone find solution? Have the same problem running 10.04 on t410

---

### Post by nomnex on 2010-08-31
> **rifcoder said:**
> Did someone find solution? Have the same problem running 10.04 on t410

Solution: uninstall the nVidia proprietary driver.

---

### Post by vinni_f on 2010-09-15
same problem with ThinkPad T510 + nvidia proprietary driver.

---

### Post by JackSchnippes on 2010-09-26
look no further thinkpad users! :) The solution is simple!

from [http://ubuntuforums.org/showthread.php?t=1515079#post9494941](http://ubuntuforums.org/showthread.php?t=1515079#post9494941)

> **BennBuntu said:**
>  
[...] Have to add 
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```to your  /etc/X11/**xorg.conf** under **devices** section. Make sure the quotation marks  are the same as if you type them.

---

### Post by antido on 2010-12-09
Setting that option in xorg.conf worked! Thanks!

---

### Post by MacUntu on 2010-12-15
I have a similar problem with my Optimus T510 (set to Integrated graphics only): setting the brightness within the session works fine (even without the driver option in the xorg.conf), but on session start it's always at 100% (burning my eyes away :D).

Any ideas?

---

### Post by rifcoder on 2010-12-23
Hooray!!! Works like a charm. Thx

---

### Post by anshuiitk on 2011-03-29
The above workaround of changing the brightness from tty1 as well the solution to add brigtness entry under Devices section of xorg.conf file works well.

I am using 10.10 on T410s.

---

### Post by CoreJohnson on 2011-04-30
>  					Originally Posted by **BennBuntu** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9494941#post9494941") 				
 				[I][...] Have to add 
 	Code:
 	Option "RegistryDwords" "EnableBrightnessControl=1" 
to your  /etc/X11/**xorg.conf** under **devices** section. Make sure the quotation marks  are the same as if you type them.[/I]


This worked for me.  Also the FN-HOME/END keyboard brightness adjustment works well now too.  Thanks.

---

### Post by pcvideo on 2011-05-23
> **rifcoder said:**
> Did someone find solution? Have the same problem running 10.04 on t410
A temporary workaround,  just switch to text console by "ALT-Ctrl-F1", adjust the birghtness there and then switch back to graphics console by 'Alt-Ctl-F7".

---

### Post by gregounours on 2012-01-25
> **steve0921 said:**
> I am having this problem too, since activating the nvidia proprietary drivers. Brightness worked fine before I did so.

Hi,
I am trying to troubleshoot brightness control on an iMac with the same graphic card as the t410. Could you tell me what driver you used before installing the nvidia drivers (they don't exist for ppc machines).
Greg

---

### Post by whitethunder922 on 2012-11-28
Having a similar problem with a Thinkpad T530 in 12.10. There is no xorg.conf anymore so I can't apply that solution. Manually adding it didn't work either. Any other ideas?

---

### Post by linrunner on 2012-11-28
Try it this [way]("http://thinkwiki.de/Ubuntu_Schnelleinstieg#Bildschirmhelligkeit_Nvidia") (in German, but I hope you get the point).

---

