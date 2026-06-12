---
title: "Nvidia Geforce 9500 GT Driver won't"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by gregsmith_to on 2009-09-24
[Yes I've been through basically all the the other 9500GT posts. In fact I read them all before I bought the card, and it looked like it would be easy]. 

This is a Shuttle PC running 8.04 LTS, there's an Nvidia chipset on the MBoard which has been working with the 'restricted' driver since I set the machine up (with some minor annoyances I won't go into). But it won't push 1920x1080, which I found out after my monitor died and I replaced it with a 1920x1080; I got this 9500 GT and now I can't get the driver to work no matter what. It keeps coming up with 'ubuntu is running in low res mode'.

I have this:
```
lspci
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)

```

My /var/log/Xorg.0.log always has this near the top
```
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 24 20:47:55 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"

```

I'm guessing from the 'failsafe' part that the problem has occurred already before this log starts (i.e. the xorg.conf has failed?)

I tried using envyNG, no useful errors (except that it couldn't auto-detect the card). No visible effect after it finished running. The nvdia-xconfig utility likewise ran, did not complain, didn't fix anything.

I tried installed the driver from Nvidia. Installation ran, said it needed to compile something, did so, ran, restarted, no improvement.

Then I started looking all over for log files.
I got stuff like this in /var/log/messages after the Nvidia install:

```

Sep 24 20:30:43 ubu kernel: [ 1820.874008] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Sep 24 20:31:42 ubu kernel: [ 1849.882138] PCI: Setting latency timer of device 0000:02:00.0 to 64
Sep 24 20:31:42 ubu kernel: [ 1849.882347] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.12  Thu Jul 17 18:10:24 PDT 2008
Sep 24 20:31:42 ubu kernel: [ 1849.889955] NVRM: API mismatch: the client has the version 185.18.36, but
Sep 24 20:31:42 ubu kernel: [ 1849.889957] NVRM: this kernel module has the version 173.14.12.  Please
Sep 24 20:31:42 ubu kernel: [ 1849.889958] NVRM: make sure that this kernel module and all NVIDIA driver
Sep 24 20:31:42 ubu kernel: [ 1849.889959] NVRM: components have the same version.

```

So that's helpful. But I couldn't find a 173.14.12 from Nvidia.

Then I ran envyNG again, when I restart X there's no messages like the above in /var/log/messages, but there's nothing about X and the thing still won't work. 

Also, the 'restricted drivers' app does not show anything in use and does not offer a way to add anything.

Here's what is in /etc/X11/xorg.conf, under Device:
```

Section "Device"
	Busid		"PCI:2:0:0"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Boardname	"nv"
	Screen	0
EndSection

```
I put the Busid in myself, it didn't make any difference.

So, I will keep banging my head into this wall but it's starting to get sore. I would please like to know these answers, though:

(1) Anything obvious I'm missing?
(2) is that the right Busid to use if lspci says "02:00.0 ..."
(3) where is the best place to check for error logs about this issue

Bonus question:
(4) the little 'ubuntu is in low-res mode' has an option to choose the setup manually. Is that actually usable? It seems the 'OK' button does not do anything. Not important, since the goal is to make that go away.

Thanks!

Also: Machine is AMD64 dual core, /proc/version is:
Linux version 2.6.24-24-generic (buildd@yellow) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Sat Aug 22 00:30:49 UTC 2009

---

### Post by tuxxy on 2009-09-24
Your in luck as I have that card too and it runs excellent :D

Did you remove the first driver before installing all the others? also theres no need to install the binary from nvidia website as nvidia-glx-180 in the repos will work great.

I suggest you reconfigure the xorg and then try and start again fresh, so when you reboot the restricted manager should alert you that new drivers are available specifically 180 version.  To reconfigure xorg run this command;

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gregsmith_to on 2009-09-24
No, I didn't, but the physical installation of the new card caused the old driver to not load, it no longer appeared in the 'restricted drivers' list. Should have removed it before installing the new card, I guess.

I will do what u suggest.

---

### Post by tuxxy on 2009-09-24
Restricted drivers should show you 2 drivers when its working the 180 and 173 versions, I would recommend the 180 :D

If it does not show anything then try manually install the 180 using Synaptic search for nvidia-glx-180

---

### Post by gregsmith_to on 2009-09-24
Well, I did what u said, answered all the questions, rebooted, and for the first time I get a 1920 x 1080 display! Still not running the nvidia driver, tho, and nothing appears on the 'Hardware drivers' list. I'll try the synaptic install.

---

### Post by tuxxy on 2009-09-24
Well finally you get 1080! now its time to just install the correct nvidia-glx-180 driver and then reboot and all should be working :D

---

### Post by gregsmith_to on 2009-09-24
Can't find nvidia-glx-180. I already have nvidia-glx-new-envy installed (envyNG did that). How can I tell what's actually running? There's a 'NVIDIA X Server settings' util (I think it wasn't there this morning) which tells me I'm not running their driver. What makes a driver appear in the Restricted Drivers list?

---

### Post by gregsmith_to on 2009-09-24
ok, the xorg.conf was totally minimal so I ran nvidia-xconfig again, it's now running the 173.14.12 driver according to 'NVIDIA X Server settings'. Thanks, man. Look at all those little pixels... and the circles are round too... cool.

---

### Post by gregsmith_to on 2009-09-24
But GLX isn't there now. I have this in xorg.conf
```

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

``` 
...but things which use GLX (like google earth, pinball) say it's not available. Nvidia util says so too.

Excerpt from Xorg.0.log:
```

(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000133gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "record"


```


... where does libglx come from and why do I seem to have a version mismatch? urg...


Also...
```

lrwxrwxrwx 1 root root      19 2009-09-24 20:46 libglx.so -> libglx.so.173.14.12
-rw-r--r-- 1 root root 1752320 2008-10-20 07:37 libglx.so.173.14.12
-rwxr-xr-x 1 root root 1748816 2009-09-24 20:31 libglx.so.185.18.36

```
...

That so's not executable...

---

### Post by gregsmith_to on 2009-09-24
OK. this is getting silly, making the so executable didn't help. Pointing the symlink at the 185 version made it load:
```

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
(II) Loading extension GLX

```
but then I get this further on down:
```

(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 173.14.12; GLX
(EE) NVIDIA(0):     module version: 185.18.36.  Please try reinstalling the
(EE) NVIDIA(0):     NVIDIA driver.


```
But... you didn't like the 173 either. 
Clearly I need to reinstall, but I'm not sure how it actually got installed in the first place.

---

### Post by tuxxy on 2009-09-24
Im not either just remove all nvidia drivers from Synaptic first then you may need to reconfgure xorg and start again.  Yes I much prefer the 180 drivers to 173

---

### Post by gregsmith_to on 2009-09-24
I reinstalled all the nvidia-glx-new-envy etc, and it went back to the first error (undefined symbol: _nv000133gl). Something is still trying to load 185.18.36 of glx, and whatever it is was not replaced by the reinstall. I think whatever it is may have been built when I ran NVIDIA-Linux-x86_64-185.18.36-pkg2.run earlier today?

Enough for tonight, I think.

---

### Post by tuxxy on 2009-09-24
Yes it is likely, this is why you should stick to supported packages in the repos.  You need to remvoe ALL drivers even the binary from website then reconfigure and start again.

---

### Post by gregsmith_to on 2009-09-24
Any idea what that is? I can do a find and sort by creation time I guess.

---

### Post by tuxxy on 2009-09-24
Find what is? im out need some sleep bud speak tomrrow

---

### Post by gregsmith_to on 2009-09-24
There were dozens & dozens of files created at the time when I ran NVIDIA-Linux-x86_64-185.18.36-pkg2.run. Docs, libs, all over.
But it created an 'uninstall' script, I ran that, it complained a bit but now it all seems to work. Thanks for your help man, I was totally stuck tell you helped me.

---

### Post by gregsmith_to on 2009-11-29
Well, I'm back in the same boat, but what I did before isn't working this time. A while ago I successfully installed the 185.18.14 driver so I could use CUDA. But after ubuntu pushed a kernel upgrade, it wouldn't work, it wanted to rebuild itself and claimed the headers were not there (and they were). Also, it's buggy, I kept getting black smears on the command line so I can't see what I'm typing.

So I decided to go back to the plain old ubuntu-approved  nvidia driver. I uninstalled the nvidia driver, and reinstalled 'nvidia-glx', but it won't run. Using the 'dpkg' command you gave me, I have a 1920x1080 display (which I'm currently very thankful for after the last 90 mins of messing around) but it's not running nvidia. If I run 'nvdia-xconfig' (which worked for me before) it puts the xorg.conf into a broken state. I don't know where my nvidia-xconfig came from, it may be a remnant of the 185 driver (or the 190 driver I had to install, just to get an uninstall script in place). Synaptic shows that I *don't* have nvidia-xconfig, but if I try to install it it tells me I need to uninstall nvidia-glx first ??!?!?!????? I'm trying to figure out how to make any forward progress here, I must be really close... .

Here's what my xorg.conf looks like
```
 xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by js6seaj on 2010-01-21
I have a Galaxy GeForce 9500GT as well. I downloaded the driver from Nvidia because the monitor video goes out every few seconds or so. The problem is that I have no idea on how to install a driver in Ubuntu. I am new to Ubuntu, have had little experience with it. So, how do I install the driver correctly?

---

### Post by geraldgrogan on 2010-03-27
Sorry to post to this old thread, but after searching all day for an answer the very same issue with this same video card, I was guessing that others might be interested in what worked for me.

After a kernal update my video stopped working. I had my PC connected to my flat screen monitor via a vga cable, which apperently was causing the problem, The log file mentioned that it could not determine the monitor model number. Appearently, this card needs to be connected via a dvi cable in order to operate properly (or at all).

Once I connected this video card to the monitor using a dvi cable, and then rebooted, the high resolution started working perfectly. Just in case I am not the last person on Earth to upgrade to DVI, I urge everyone to upgrade to DVI cables ASAP.

I hope this helps.

---

### Post by gregsmith_to on 2010-03-27
I eventually started this in another thread (since it was really another event around the same issue) and eventually got the thing working. It seems that Ubuntu 8.04 somehow doesn't detect the presence of the Nvidia board properly - I don't think I was ever offered the 'restricted driver' for it, and even when I ran EnvyNG, it told me it couldn't detect a suitable card, but gave me the option of installing the nvidia driver anyhow, and that's what worked. Part of the problem, I think, is that I installed it that way the first time around without noticing that that was unusual (too many other weird things going on) and so I was suspicious the second time when I was just trying to 'back down' to the normal 8.04 situation where you normally get offered the restricted driver. The fail-to-detect occurred with both the motherboard's Nvidia video and the 9500 I plugged in later.

( I also had problems with the driver failing to load when I used the VGA output, didn't have time to play around with that too much. The network interface was disabled as a side-effect).

I would avoid using the driver downloaded from Nvidia; I did get it working but it interacts poorly with ubuntu. You will need to reinstall it each time the kernel gets updated. EnvyNG can be installed using synaptic, that worked for me.

Good news, I just booted the 9.10 LiveCD on this machine and it offered a restricted driver, version 185 (not that you can use it in the LiveCD, but nice to see it's detected). I'll probably upgrade to 10.04 when that comes out.

---

