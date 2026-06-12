---
title: "Hello new kernel and broken NVIDIA"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Mikael P. on 2009-08-03
I like updates. But not when they break the system.
Last night's new kernel broke my nvidia drivers for some reason.

As I am quite green to all these new wonders I am a bit lost about what to do.

At first I got a basic screen saying hey I am going to run in low graphics mode. But after some safe booting and automatic fixing of graphics issues I got my desktop at least.
But I lack certain features like the top bar of all windows, so they are a bit hard to move. I also lack a list of running software at the bottom of the screen. Lastly the screenlets refused to start.

I don't know how to tell you what version of kernel I am running, but it should be the absolute latest out there. My Nvidia driver should be 185.something. I had to use the beta ones as the plain 180 version broke some other things.

So.. how do I get my system back to normal? With working Nvidia drivers? Is it as simple as re-installing the beta drivers. Or do I need to do some tinkering in that famous x.org file?

Grateful for all help!

---

### Post by Mikael P. on 2009-08-03
Nevermind. I'm getting lazy with this friendly forum available.

I did not know it was mandatory to re-install nvidia drivers after a major kernel update. But I know now...

---

### Post by Sooda on 2009-08-03
To check kernel version type in terminal:
```
uname -r
```to make backup of xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```to edit xorg.config:
```
sudo gedit /etc/X11/xorg.conf
```to replace modified xorg.conf with backup:
```
sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```New kernel update most of times breaks manual NVIDIA install.

In xorg.conf file module and device sections belong to graphics.

I got it fixed by uninstalling NVIDIA driver manually. Like you would install manually, but adding to end
' --uninstall' (without ''). Restart computer and let Synaptic install recommended driver, restart computer.

You want to make sure all Mesa packages are installed for Ubuntu. Mesa is OpenGL variant for Linux.

Or use previous kernel by following commenting out instructions on this link: [http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

---

### Post by Mikael P. on 2009-08-03
Thanks for the help! But I can't use the version from Synaptic as that breaks my display slightly when I turn off Compiz.
But everything is back to normal now.

---

