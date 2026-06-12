---
title: "fglrx and &quot;low-graphics mode&quot;"
date: 2008-05-02
forum: Hardware
---

### Post by morphx on 2008-05-02
I have been doing a lot reading before deciding to post but I just haven't found anyone with the exact same problem, so, here it goes:

This is a fresh install of Ubuntu 8.04 on a HP ZD8000 laptop with an ATI X600 video card.
I previously had Ubuntu 7.10 working just fine with my video card.

So, the problem is that once I enable the OpenSource drivers for my X600 and reboot everything works fine but as soon as I reboot again I get the "Ubuntu is running in low-graphics mode" dialog.

Removing the drivers through the "Hardware Drivers" applet rebooting, re-enabling and rebooting solves the problem until I reboot again.
So, on the second reboot I always get the "Ubuntu is running in low-graphics mode" dialog.

I have tried absolutely everything -- even tried the proprietary drivers with no luck.

As I said at the beginning I have been doing a lot of reading and testing and I have found a way to be able to boot using the OpenSource drivers:
- Wait for the "Ubuntu is running in low-graphics mode" dialog.
- Click "Continue"
- Wait for GDM (running at 800x600 of course)
- Switch to a terminal (CTRL+ALT+F1)
- Type the following in the console:
$ sudo aticonfig --initial -f
$ sudo /etc/init.d/gdm restart

This restarts GDM running at full resolution and I'm then able to use my laptop without problems (Compiz is working great)... but as soon as I reboot I have to do the exact same thing again.

Does anyone have the slightest idea of what may be going on?

NOTE: [SIZE="1"]I forgot to mention that when I use the proprietary drivers I get the white-screen-of-death... but that's not the problem, as I know how to correct it. The interesting thing is that once I reboot, the dreaded "Ubuntu is running in low-graphics mode" dialog appears again... so the same behavior occurs after rebooting regardless of the driver I'm using.[/SIZE]

---

### Post by sibbe on 2008-05-04
I have a simliar problem on a fresh Ubuntu 8.04. Graphic Card is an ATI Radeon 9700 Pro.

When I enable the restricted driver via the System Menü, it tells me to reboot in order to activate the fglrx-driver. When the system reboots I always get the little "Ubuntu is runnig in low resolution"-Windows which tells me to configure Graphic Card and Monitor. After configuring and rebooting as told, the same box appears and all settings done before reboot are gone. 
Clicking continue in this box results in maximum resolution of 800x600. When I disable the fglrx in this "mode" and reboot again everything works just fine with the open-source driver.

Lot's of googleing and searching Ubuntu-forums haven't given me a solution.
Can anyone help?

---

### Post by morphx on 2008-05-05
sibbe,

Could you please confirm that following the same steps as I do allows you to use the restricted driver?

- Wait for the "Ubuntu is running in low-graphics mode" dialog.
- Click "Continue"
- Wait for GDM (running at 800x600 of course)
- Switch to a terminal (CTRL+ALT+F1)
- Type the following in the console:
$ sudo aticonfig --initial -f
$ sudo /etc/init.d/gdm restart

If this allows you to log-in using the restricted drivers may confirm this is a bug that affects both our systems and there's a common "way" of using the driver -- hopefully, this might help the developers figure out what's wrong with our systems.

---

### Post by johnswb on 2008-05-06
I was getting the same thing.  This is what I did on my system running a ATi X1600.

[http://ubuntuforums.org/showthread.php?t=778142&highlight=ati](http://ubuntuforums.org/showthread.php?t=778142&highlight=ati)

---

### Post by morphx on 2008-05-07
I'm sure I already did this and didn't help.
I will try it again and will report back.

---

### Post by morphx on 2008-05-07
Unfortunately it didn't work for me -- XOrg is still using the OpenSource drivers and I still need to "sudo aticonfig --initial -f" every time I log off or reboot

---

### Post by sibbe on 2008-05-08
> **morphx said:**
> sibbe,

Could you please confirm that following the same steps as I do allows you to use the restricted driver?

- Wait for the "Ubuntu is running in low-graphics mode" dialog.
- Click "Continue"
- Wait for GDM (running at 800x600 of course)
- Switch to a terminal (CTRL+ALT+F1)
- Type the following in the console:
$ sudo aticonfig --initial -f
$ sudo /etc/init.d/gdm restart

If this allows you to log-in using the restricted drivers may confirm this is a bug that affects both our systems and there's a common "way" of using the driver -- hopefully, this might help the developers figure out what's wrong with our systems.

Hey morphx,
sorry that I replay so late, but I wasn't at home the last days. I tried you method and as you mentioned it worked. After "aticonfig --initial -f" and restarting gdm everything worked (Hardwaremanager showed "using" of the ati driver). After reboot again the low-graphics dialog.

So there seems to be a bug. Now I'll try the method of johnswb, will edit my post with the result.

**Edit:** The method of johnswb worked not for me. fglrxinfo dropped an "Segmentation fault" error. Is there a method I can remove everything that the method of johnswb installed (for example the ATI Control Center)?

---

### Post by morphx on 2008-05-09
Hello sibbe,

Thank you very much! Now I know I'm not the only one.
I also tried johnswb method and didn't work for me -- actually, things are much worst now: lots of flickering, slower than ever...

Anyway, to uninstall ATI's drivers you could try this:
$ sudo /usr/share/ati/fglrx-uninstall.sh

---

### Post by sibbe on 2008-05-09
I'm now doing the aticonfig and every boot, not great but works ;) 

I noticed (in a moment only Crtl + Alt + Remove worked), that the aticonfig I had done inside gnome, before "gdm restart" worked AFTER the bootup. But it doesn't stay when I reboot via the gnome button or power-off and then on. 

Really seems to be a bug. But what to do, wait?

---

### Post by morphx on 2008-05-09
I just found out something: every time I log-off, the xorg.conf file gets overwritten.
The xorg.conf that gets generated after logging off appears to be missing lots of information both about the video card as well the monitor.

I'm posting it here so, hopefully, someone can give us (sibbe and me) some idea of what's going on.

The "xorg.conf.20080509034803.tar.gz" is the one that gets generated when logging off and/or rebooting and that doesn't work. With this file, X seems to try to auto-detect the video card and monitor but it fails.

The "xorg.conf" is the one generated after running "aticonfig --initial" and which works perfectly with my system

I really hope someone can tell me why Ubuntu/GDM/X is overwriting my xorg.org file or why is it that the one generated by the system doesn't work.

---

### Post by danpos on 2008-05-09
@All

At terminal type:

```
sudo displayconfig-gtk
```

So choose the model monitor that matches your one and choose the mode (video resolution) supported by your graphic card.

I hope that this post help you out.

Regards,

Danpos.

---

### Post by morphx on 2008-05-09
Hello Danpos,

Thank you for the suggestion but the displayconfig-gtk application already shows the correct display and graphics mode.

---

### Post by morphx on 2008-05-09
Here's something I just tried:
- I booted up
- Ran aticonfig in order to start GDM using fglrx
- Then, I tried testing different resolutions using displayconfig-gtk and they all failed. The only way I could get a successful test was using the vesa driver.

Any ideas?

I'm also attaching Xorg's log in case that is of any use.

---

### Post by danpos on 2008-05-10
@morphx

I know well what you've passing with proprietary drivers on Ubuntu. I'd the same weird behavior on my daughter's machine, which has a NVIDIA video adapter. After I did install the nvidia-glx-new driver and then to do a some uninstall/install of this driver through Synaptic (in order to try out correct some problems in my system), I'd got the video card with the configuration completely messed up, only it worked just only vesa driver. Freak!

What I did was a complete reinstall (formating the / partition), so I did all updates (hardy-security and hard-updates) and **just after that I did install the proprietary driver to my video card through System -> Administration -> Restricted Drivers**. [COLOR="Blue"]After that the use of displayconfig-gtk worked out like a charm.[/COLOR]

I repeat: this is a weird behavior but it worked at here with a NVIDIA card using proprietary driver so I guess that it should work for your ATI card also.

Regards,

Danpos.

---

### Post by sibbe on 2008-05-12
@danpos
I think the reinstall isn't an option, because my system is a clean install. And only the updates that came after the release of hardy are installed.

---

### Post by morphx on 2008-05-12
Unfortunately I have already re-installed 8.04 twice and I end up experiencing the exact same behavior.

I'm seriously thinking of going back to 7.10 (which worked perfectly).

---

### Post by neuthral on 2008-06-28
Hello i have had the exactly same problem.

Im running Xubuntu 7.04 atm and i found this worked for me, after you do a succesfull login with the drivers working change the privilages on xorg.conf "sudo chmod 555 /etc/X11/xorg.conf" and it cant be overwritten :)

---

### Post by sibbe on 2008-08-14
Hello!

After my problems with the fglrx-drivers I took a long break from Ubuntu to give it time to develop. Yesterday I reinstalled the 8.04 and updated directly to the 8.04.1. Then I activated the fglrx-drivers and I had to see after booting this morning that there was no change in behaviour.

Has anyone found a better solution than using aticonfig at every boot-up? The last mentioned method with chmod 555 doesn't work for my system.

**Edit:** Found a solution myself, using the ati.com driver now. So far it works! :)

---

