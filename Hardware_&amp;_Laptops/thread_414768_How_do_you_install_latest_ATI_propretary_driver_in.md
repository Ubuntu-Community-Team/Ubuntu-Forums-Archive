---
title: "How do you install latest ATI propretary driver in feisty?"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by MindRiot on 2007-04-20
How in the hell do you install the ATI proprietary driver? :mad: 

I've had no difficulty following these instructions from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2") for Edgy.  Of course, those instructions aren't working with Feisty.  I see there is a startup entry for a restricted driver manager. I have no idea how that effects anything. Unchecking the startup entry did nothing to help.

If I follow the Edgy instructions (--build Ubuntu/feisty) in an xsession, and I try to run aticonfig at the end of the installation process, --initial returns a memory dump, wipes out the xorg.conf file and creates a backup called xorg.conf.original-0.

This pissed me off, so I uninstalled vesa with Synaptic, which dropped me at a terminal prompt upon restarting the computer.  I repeated the installation process from the prompt, including running the command to reconfigure xorg.conf.  This walked my through a couple of questions and then surprisingly the aticonfig --initial and aticonfig --overlay-type=Xv worked correctly, since apparently I wasn't in an xsession.  However, upon restarting the computer, I'm still stuck with the vesa driver.

Here the result from fglrxinfo:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

Why do I want XFree86?  I don't want XFree86.  I want Xorg. I have an ATI Radeon X1600. That's what it should say.  How do I rid Ubuntu of this unwelcome driver so I can enjoy 3d rendering, or is that against Ubuntu philosophy? ;)

Sometimes an effort to be helpful turns out to be the opposite. 

Any help would be appreciated.  Also, it would be fantastic if someone knowledgeable could update the ATI BinaryDriver Howto.  Thanks

---

### Post by Erlander on 2007-04-20
System/Administration/restricted Drivers Manager

Check that you have enabled the repositories in software sources and if it doesn't work it could be because the repositories are too busy.  I had trouble for a while earlier today.

Rob

---

### Post by Jagot on 2007-04-20
Could [this]("http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/") help?

---

### Post by MindRiot on 2007-04-20
> **Jagot said:**
> Could [this]("http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/") help?

Thanks for the link, but that not my problem, and that same issue is raised in a sticky.

As for System/Administration/Restricted Drivers Manager, I opened that program and checked the box next to ATI accelerated graphics driver, which proceeded to download and install the driver. However, it has been mentioned that this driver doesn't support the Radeon X1600 series, which is the card I have. See. [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

Right now I'm following this guide I found through Google.  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") 


Hopefully, this works, but I'm not optimistic.

---

### Post by MindRiot on 2007-04-20
> **MindRiot said:**
> Thanks for the link, but that not my problem, and that same issue is raised in a sticky.

As for System/Administration/Restricted Drivers Manager, I opened that program and checked the box next to ATI accelerated graphics driver, which proceeded to download and install the driver. However, it has been mentioned that this driver doesn't support the Radeon X1600 series, which is the card I have. See. [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

Right now I'm following this guide I found through Google.  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") 


Hopefully, this works, but I'm not optimistic.

Edit:  The guide I googled worked. I copied the xorg.conf.fglrx-0 file as xorg.conf and then deleted xorg.conf.fglrx-0.  I have no idea how the instructions in this guide differed from the instructions for Edgy, so I'm lost as to how to explain why it now works.

Oops, I hit the quote button rather than edit.  Oh well. I've been up all night messing with this and other things, and I'm tired.

---

### Post by contro on 2007-04-20
did you use method one or two to install the drivers for ATI X1600

---

### Post by MindRiot on 2007-04-20
> **contro said:**
> did you use method one or two to install the drivers for ATI X1600

Method 2. 

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6458 (8.36.5)

However, as I mentioned above, the Restricted Drivers Manager downloaded and installed a driver before I undertook Method 2 (I did restart the computer before following Method 2).  I really couldn't say what version driver the Restricted Driver Manager downloaded.

---

### Post by nickpaton on 2007-04-20
Radeon XPRESS 200M on HP nx6125 laptop

Also used wiki Method 2 having tried various methods before that.

Started off by copying back into the existing messed up version of xorg.conf, the original backed up one.

Went through all of method 2 no probs.

At "Configure the Driver" I initially found that running the aticonfig commands as given deleted xorg.conf file contents.

Having got it copied back in again from the original backup, simply changed "ati" for "fglrx" as the author suggests.

HTH

---

### Post by Barnaba on 2007-04-20
followed step 2 but fglrxinfo delivers this to me:

Error: unable to open display :0

And if I try to Enable the Desktop Effects I get the message:

The Composite Extension is not available

I tried to get the old initial xorg.conf via this command:
sudo dpkg-reconfigure -phigh xserver-xorg

and went through the steps several times now.
I am also using the ATI X1600 in the Asus A6JA

How to clean up the whole diver mess I got now and start over with this step-by-step tutorial?

---

### Post by contro on 2007-04-20
i know i am running ito the same issues this is so confusing they have to make a better guide for us ATI X1600 users

---

### Post by div- on 2007-04-20
> **Barnaba said:**
> followed step 2 but fglrxinfo delivers this to me:

Error: unable to open display :0

And if I try to Enable the Desktop Effects I get the message:

The Composite Extension is not available

I tried to get the old initial xorg.conf via this command:
sudo dpkg-reconfigure -phigh xserver-xorg

and went through the steps several times now.
I am also using the ATI X1600 in the Asus A6JA

How to clean up the whole diver mess I got now and start over with this step-by-step tutorial?

try adding the following to the bottom of your xorg.conf

```

Section "Extensions"
        Option  "Composite"     "0"
EndSection

```

---

### Post by jamesmccain on 2007-04-20
is/have anyone got "composite" to work with any drivers for ATI X1600/X1X00's so you can enable desktop effect? I've been able to do a few work arounds but when I actually get the composite error to go away I am not able to enable it.

---

### Post by willnapier on 2007-04-21
Hi. I am having problems with playing video. I don't have any problems playing video with realplayer from say the bbc news site, not with seeing flash video at youtube. However if I try to play video files (eg .wmv) I get a green-yellow interference and choppy playback - I presume this is a frame rate problem but I wouldn't know for sure. I tried uncommenting the part of the config file that enables dma (dma=yes). It seemed to work at first, but it was evident that the choppy frame rate was still there every few seconds. I tried method 1 mentioned above. No change. Then method 2. Now it is even worse. Here is my fglrxinfo

~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Note that the ATI card isn't even recognized as present (I have the ATI RADEON X1600). When use sysinfo there is similarly no mention/appearance of the ATI card.

I am on a newly installed kubuntu feisty with an intel dual core processor and 1Gb ram.

Update: I have found a utility on my menu called the ATI Catalyst Control Center. This was presumably install in one of the steps I followed for either method 1 or 2 mentioned in above posts. When I run it, it gives me the following error:

"Problem in fglrx-amdcccle: The problem cannot be reported. This is not a genuine ubuntu package."

I don't know if that sheds any light on things.

With thanks for any help

Will

---

### Post by optimus.prime on 2007-04-22
According to this thread:

[http://ubuntuforums.org/showthread.php?t=405487&highlight=ati+composite+extension+available](http://ubuntuforums.org/showthread.php?t=405487&highlight=ati+composite+extension+available)

ATI restricted drivers do not work with desktop effects at all.

You can, however, do a fresh XGL install and get it to work, however during that XGL session, no 3D software will work.

---

### Post by MindRiot on 2007-04-23
I want to add a few more comments about installing the ATI 8.36.5 binary driver in either edgy or feisty.

You can follow the instructions for 6.10 in the ATI Binary Driver Howto.

See: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2")

Under the section Modifying xorg.conf

Ignore both sudo aticonfig --initial and aticonfig --overlay-type=Xv

Run the following commands, then reboot

```
sudo /sbin/lrm-manager
sudo depmod -a
```

Once you're logged back in, open the terminal and enter

```
sudo gedit /etc/X11/xorg.conf
```

Under Section "Device" change

```
Driver      "vesa"

```

to

```
Driver      "fglrx"
```

Save the file, then reboot the computer.

When you log back in run in the terminal

```
sudo aticonfig --overlay-type=Xv
```

Ignore running aticonfig --initial.

Your Section "Device" in /etc/X11/xorg.conf should look like this:

```
Section "Device"
	Identifier  "ATI Technologies, Inc. ATI default card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```

---

### Post by willnapier on 2007-04-24
Hi all, I have tried the suggestions in the above post (for which, thanks MindRiot). I have tried everything suggested in the links from here. Basically I'm not seeming to get the ati recognised at all (although it is in lspci).

Would it help if I post the core dump (below)? I think that problems may have been caused by aticonfig --initial deleting the previous xorg.conf but due to aborting, no updated xorg.conf is put in its place.

I don't feel like I'm any further on than when I encountered the problem. Any encouragement very welcome.

Will

sudo aticonfig --initial
Password:
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfbe6a7f ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d01f5b]
aticonfig[0x805bff7]
aticonfig[0x805c2a5]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7cacebc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 511126     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 511126     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c89000-b7c8a000 rw-p b7c89000 00:00 0
b7c8a000-b7c8c000 r-xp 00000000 08:01 8619272    /lib/tls/i686/cmov/libdl-2.5.so
b7c8c000-b7c8e000 rw-p 00001000 08:01 8619272    /lib/tls/i686/cmov/libdl-2.5.so
b7c8e000-b7c8f000 rw-p b7c8e000 00:00 0
b7c8f000-b7c93000 r-xp 00000000 08:01 509275     /usr/lib/libXdmcp.so.6.0.0
b7c93000-b7c94000 rw-p 00003000 08:01 509275     /usr/lib/libXdmcp.so.6.0.0
b7c94000-b7c96000 r-xp 00000000 08:01 509264     /usr/lib/libXau.so.6.0.0
b7c96000-b7c97000 rw-p 00001000 08:01 509264     /usr/lib/libXau.so.6.0.0
b7c97000-b7dd2000 r-xp 00000000 08:01 8619266    /lib/tls/i686/cmov/libc-2.5.so
b7dd2000-b7dd3000 r--p 0013b000 08:01 8619266    /lib/tls/i686/cmov/libc-2.5.so
b7dd3000-b7dd5000 rw-p 0013c000 08:01 8619266    /lib/tls/i686/cmov/libc-2.5.so
b7dd5000-b7dd8000 rw-p b7dd5000 00:00 0
b7dd8000-b7dfd000 r-xp 00000000 08:01 8619274    /lib/tls/i686/cmov/libm-2.5.so
b7dfd000-b7dff000 rw-p 00024000 08:01 8619274    /lib/tls/i686/cmov/libm-2.5.so
b7dff000-b7eec000 r-xp 00000000 08:01 509260     /usr/lib/libX11.so.6.2.0
b7eec000-b7ef0000 rw-p 000ed000 08:01 509260     /usr/lib/libX11.so.6.2.0
b7ef0000-b7efd000 r-xp 00000000 08:01 509277     /usr/lib/libXext.so.6.4.0
b7efd000-b7efe000 rw-p 0000d000 08:01 509277     /usr/lib/libXext.so.6.4.0
b7efe000-b7eff000 rw-p b7efe000 00:00 0
b7eff000-b7f06000 r-xp 00000000 08:01 509299     /usr/lib/libXrender.so.1.3.0
b7f06000-b7f07000 rw-p 00006000 08:01 509299     /usr/lib/libXrender.so.1.3.0
b7f07000-b7f0c000 r-xp 00000000 08:01 509297     /usr/lib/libXrandr.so.2.1.0
b7f0c000-b7f0d000 rw-p 00005000 08:01 509297     /usr/lib/libXrandr.so.2.1.0
b7f11000-b7f1c000 r-xp 00000000 08:01 8585278    /lib/libgcc_s.so.1
b7f1c000-b7f1d000 rw-p 0000a000 08:01 8585278    /lib/libgcc_s.so.1
b7f1d000-b7f20000 rw-p b7f1d000 00:00 0
b7f20000-b7f39000 r-xp 00000000 08:01 8585237    /lib/ld-2.5.so
b7f39000-b7f3b000 rw-p 00019000 08:01 8585237    /lib/ld-2.5.so
bfbd2000-bfbe8000 rw-p bfbd2000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

---

### Post by MindRiot on 2007-04-24
If you run aticonfig --initial, it should make a backup of xorg.conf named xorg.conf.original-0.  Look in the /etc/X11 folder to see if the file is there, if it is:

```
sudo cp -p /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf
```

Then sudo gedit /etc/X11/xorg.conf and then, under the Section "Device" replace "vesa" with "fglrx"

---

### Post by willnapier on 2007-04-24
MindRiot, thank you. It worked. Fantastic. Still feel a little out of my depth with it all, but really pleased to have sorted this.

Will

---

### Post by SomeCallMeTim on 2007-04-25
I've just installed Feisty on my IBM R60 with an ATI 1400 and although the restricted drivers did seem to work ok with 3D I couldn't get compiz or beryl to work. 

I ran through [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

Using method 1 which worked fine but compiz and beryl still won't run. 

Has anyone got compiz or beryl to work on an ATI 1300, 1400,1600 ?

I've put Feisty on a crappy Dell GX280 with built in Intel graphics and beryl works just fine! 

It's so frustrating I'm getting very tempted to sell the laptop and get one with an NVIDIA card in it just to get beryl to work!


Tim

---

### Post by KmooreUSN on 2007-04-25
> **MindRiot said:**
> I want to add a few more comments about installing the ATI 8.36.5 binary driver in either edgy or feisty.

You can follow the instructions for 6.10 in the ATI Binary Driver Howto.

See: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2")

Under the section Modifying xorg.conf

Ignore both sudo aticonfig --initial and aticonfig --overlay-type=Xv

Run the following commands, then reboot

```
sudo /sbin/lrm-manager
sudo depmod -a
```

Once you're logged back in, open the terminal and enter

```
sudo gedit /etc/X11/xorg.conf
```

Under Section "Device" change

```
Driver      "vesa"

```

to

```
Driver      "fglrx"
```

Save the file, then reboot the computer.

When you log back in run in the terminal

```
sudo aticonfig --overlay-type=Xv
```

Ignore running aticonfig --initial.

Your Section "Device" in /etc/X11/xorg.conf should look like this:

```
Section "Device"
	Identifier  "ATI Technologies, Inc. ATI default card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```




:KS MindRiot, your a genius! lol, thanks this worked for me when all other attempts failed, im  goin to have to post this on ATI's website forum, hopefully it will work for others as well.:KS 


:guitar:

---

### Post by mrThefter on 2007-04-25
No, you can't run Compiz/Beryl with X series ATI cards without setting up an XGL server.
If one merely looked up installation guides for Beryl/Compiz, they'd see that you would need an XGL server because ATI drivers don't support AIGLX.

---

### Post by jespdj on 2007-04-26
> **MindRiot said:**
> As for System/Administration/Restricted Drivers Manager, I opened that program and checked the box next to ATI accelerated graphics driver, which proceeded to download and install the driver. However, it has been mentioned that this driver doesn't support the Radeon X1600 series, which is the card I have. See. [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")
Really? I also have an ATI X1600, I used that menu option and it worked without problems (64-bit Ubuntu Feisty).

> **jamesmccain said:**
> is/have anyone got "composite" to work with any drivers for ATI X1600/X1X00's so you can enable desktop effect? I've been able to do a few work arounds but when I actually get the composite error to go away I am not able to enable it.
Indeed, the Composite extension is not supported by the ATI driver. However, I do have fglrx, Xgl and Compiz working on my ATI X1600. Have a look at these guides:

[http://compiz.org/ATI](http://compiz.org/ATI)
[http://compiz.org/Ubuntu_Installation_Guide](http://compiz.org/Ubuntu_Installation_Guide)
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

The trick, according to that last page, is to run Xgl on display 1 while fglrx is running on display 0.
> **optimus.prime said:**
> According to this thread:

[http://ubuntuforums.org/showthread.php?t=405487&highlight=ati+composite+extension+available](http://ubuntuforums.org/showthread.php?t=405487&highlight=ati+composite+extension+available)

ATI restricted drivers do not work with desktop effects at all.

You can, however, do a fresh XGL install and get it to work, however during that XGL session, no 3D software will work.
That's right, for example fgl_glxgears does not work by on the default display (display 1, on which Xgl is running), but if I tell it explicitly to use display 0, it works! So I type:

fgl_glxgears -display :0.0

I'm thinking of getting an nVidia 8600GTS instead of this ATI X1600 I have now, it looks like nVidia has better Linux drivers. I'm crossing my fingers that it will work... (read that the 8600GTS might be so new that a good driver isn't yet available...).

---

### Post by germaike on 2007-04-27
hey ubuntu-lover :)


i just installed ubuntu 7.04 on my desktop pc. I have a ati 9800 serie and i tried to install the ati drivers. Then i restarted my desktop and i got a black screen and my Screen gives a pop-up that the mode is not supported! I'm a beginner in linux so i don't know what the do next? Can anyone help me with this?

i did this first > # Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
# Start text mode installer and install Ubuntu/Kubuntu.
# Finish Install and reboot.
# Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
# Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
# Update loaded modules.
sudo depmod -a
# Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Then i followed the instructions on this tutorial where i used method 2.
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

thx 

germaike

---

### Post by 11dayz on 2007-05-04
> **MindRiot said:**
> I want to add a few more comments about installing the ATI 8.36.5 binary driver in either edgy or feisty.

You can follow the instructions for 6.10 in the ATI Binary Driver Howto.

See: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2")

Under the section Modifying xorg.conf

Ignore both sudo aticonfig --initial and aticonfig --overlay-type=Xv

Run the following commands, then reboot

```
sudo /sbin/lrm-manager
sudo depmod -a
```

Once you're logged back in, open the terminal and enter

```
sudo gedit /etc/X11/xorg.conf
```

Under Section "Device" change

```
Driver      "vesa"

```

to

```
Driver      "fglrx"
```

Save the file, then reboot the computer.

When you log back in run in the terminal

```
sudo aticonfig --overlay-type=Xv
```

Ignore running aticonfig --initial.

Your Section "Device" in /etc/X11/xorg.conf should look like this:

```
Section "Device"
	Identifier  "ATI Technologies, Inc. ATI default card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection
```

So I got this far and it "worked" in that I can get back to the desktop instead of it hanging after login.  However, glxgears still has the same performance as before the install, that is the same performance as with the "vesa" driver loaded.  It seems that this method somehow tricks the system into thinking it is using the fglrx driver, but it isn't really using it?

I am at my witts end with this thing.  I can't get 3d acceleration to work with my mobility 9700 on my laptop with feisty.  I have tried all the how-tos, method 1, method 2, envy, etc...  For some darn reason, even my Edgy install CD is hanging when it didn't before.  I am thinking about going back to the dark side :(

---

