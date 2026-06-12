---
title: "Bad video performance Radeon HD 5850"
date: 2011-01-27
forum: Hardware
---

### Post by W-Unit on 2011-01-27
Hi there, absolute linux noob here.

I just managed to install ATI Catalyst and now I am noticing that, when I drag windows around the screen, it takes about a half-second for the window to "follow" the cursor, and then the bottom half of the window arrives at its destination maybe 10ms before the top half.
Other similar problems also occur when I do things like scrolling up or down in Firefox (Chrome does not seem to do this, or at least it makes it unnoticeable), but the window dragging is probably the most prominent.

Incidentally, I also can't enable any desktop effects from System > Preferences > Appearance.

Anybody know how to fix this?
Extra-detailed instructions are greatly appreciated, I really don't know what I'm doing on Linux yet :D

P.S. When installing Catalyst, I followed this tutorial, however at the end it describes some commands you can run to test your installation - those commands produce errors for me. However, ATI Catalyst itself runs just fine...
The tutorial is for Fedora users, not Ubuntu, and a bit outdated, but everything at least appeared to be the same in this case... perhaps something in there was wrong though?
[http://gofedora.com/how-to-install-ati-catalyst-fglrx-98-drivers-fedora-11/](http://gofedora.com/how-to-install-ati-catalyst-fglrx-98-drivers-fedora-11/)

--EDIT--
Disabled the ATI drivers and commented out the changes to blacklist.conf described by the above tutorial. Video performance is now doing just fine and overall look is improved, however I don't consider the problem solved because I would like to be able to use Catalyst, if possible. I still cannot enable desktop effects (if you could tell me what to do to enable these effects, I'd appreciate that as well)

---

### Post by Grafens on 2011-01-27
To get effects you need "compiz" installed. goto ubuntu software centre > select installed software, to see if you already have it installed.

Cheers
Grafens

---

### Post by tcrapper on 2011-01-27
When installing the ATI driver you should create debian packages.

I'd remove the driver and try installing using the method below.

To remove do the below.

```
sudo apt-get remove fglrx fglrx-amdcccle
sudo /usr/share/ati/fglrx-uninstall.sh
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -fr /usr/lib/fglrx
sudo rm -fr /etc/ati

```

Before rebooting download [this]("http://kanotix.com/files/install-fglrx-debian.sh") script which will install the ATI driver the correct way for debian based distros like Ubuntu.

```
wget http://kanotix.com/files/install-fglrx-debian.sh
chmod 755 install-fglrx-debian.sh
sudo reboot

```

Sudo reboot will reboot your system.

After it starts back up click ctrl alt f1 and login then enter the following commands.

```
sudo ./install-fglrx-debian.sh -z
sudo aticonfig -f --initial
sudo reboot

```

---

### Post by W-Unit on 2011-01-28
> **Grafens said:**
> To get effects you need "compiz" installed. goto ubuntu software centre > select installed software, to see if you already have it installed.
Affirmative, it's installed.

> **tcrapper said:**
> After it starts back up click ctrl alt f1 and login then enter the following commands.

```
sudo ./install-fglrx-debian.sh -z
sudo aticonfig -f --initial
sudo reboot

```
I'm afraid pressing CTRL+ALT+F1 simply makes my monitor go into power saver mode (i.e. the monitor doesn't think it's getting any video input)
I tried running these commands from the terminal but of course it tells me to run them from the console...
Tried typing them to the blank screen, hoping maybe it would receive them, but apparently not :(

I think it has to do with the fact that my monitor uses weird settings. I've never NOT had to tweak my monitor settings after plugging in a different device.

On another related note, I've noticed that if I fullscreen a video (i.e. off of Youtube or something), it gets really choppy. Small videos display fine, but 720p or larger, or anything if I fullscreen it, is noticeably choppy. Perhaps getting the console to work and then installing the drivers as you described will fix this though...

Thanks! :)

---

### Post by tcrapper on 2011-01-28
Open a terminal after logging in and run
```
DISPLAY= sudo sh install-fglrx-debian.sh -z
```

That should let you run the script without the console.

Then run
```
sudo aticonfig -f --initial
```

Then reboot.

---

### Post by W-Unit on 2011-01-28
The console command worked, but it told me it was missing.. er.. something about fglrx. So I did a **sudo apt-get -f install**, then tried again, and it appeared to work.

The **aticonfig** command didn't work the first time ("command not found") so I searched the filesystem and found a file called **aticonfig** in **/usr/lib/fglrx/bin**.

Here's what I get when I try to run the command from there.
```
will@ubuntu:/usr/lib/fglrx/bin$ sudo ./aticonfig -f --initial
./aticonfig: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```Once again thank you for your help :)

However, after enabling ATI FireGL from the Hardware Drivers menu and rebooting (even without having successfully excecuted the aticonfig command), performance seems to be improved in most areas. I can now watch full-screen 1080p video with no choppiness.
I still cannot enable Desktop Effects (don't know if this is a related issue at this point) though.
Also, when I drag windows around now, their bottom half "bends" towards the direction it came from momentarily. So if I drag a window from left to right, the bottom half will bend to the left before correcting itself. This is definitely a minor issue and doesn't bother me nearly as much as other problems described in this post, but just in case you happen to know the solution I thought I'd mention it :D

---

### Post by W-Unit on 2011-01-31
Just thought I would try adding on to this thread before creating a new one, although this is segwaying a little bit now. Only a little though :)

I just purchased a new netbook (Asus Eee PC 1215T) and am running Ubuntu alone (no Windows or anything else).
I'm having the exact same type of problem with videos being choppy, and tried to use the exact same solution. It almost worked, but after having run the commands from the console (the CTRL+ALT+F1 works fine on this machine) and rebooting, I get a different error message when I try to run **aticonfig** - it tells me it can't detect any ATI driver installation.
This, I think, is what's keeping the problem (choppy videos and mildly sub-par desktop performance) from being solved.

I suspect the desktop machine worked despite not having run the **aticonfig** command because I'd already spent a few hours messing around with FGLRX before I ran the shell script, and at some point in doing so, I'd somehow created the environment that FireGL runs in. If that makes sense :P

Like I said before, on the desktop machine (which basically is working properly now), the Hardware Drivers menu shows "ATI FireGL" as the video driver, however on this machine that doesn't show up. Instead it has "ATI/AMD Proprietary FGLRX Driver," which I've got disabled (I tried enabling it first, before running the shell script, but it almost made it inoperable... something should be done about that, no?).

How do I get the "ATI FireGL" driver to show up and work?

Incidentally, the Eee PC 1215T has a Radeon HD 4250 GPU

---

