---
title: "GeForce 8800 | Cannot run advanced graphics | Only single monitor"
date: 2009-03-22
forum: Hardware
---

### Post by designsedge on 2009-03-22
Hey all -

I certainly hope someone can shed some light on my problem here.

I am running Kubuntu 8.04 x64 architecture on the 23-24 kernel.  Video card is a Geforce 8500 series, and until recently, it ran just fine, then - it lost its mind.

First - some background information - getting the Nvidia drivers and config to work was always somewhat of a pain, so I kept an xorg.conf-works copy of the working xorg file.  That file has disappeared. (Yes have looked everywhere for it, and yes, I remember where I left it)

Now, when I run nvidia-xconfig and reboot, I get the ubuntu is running in low graphics mode.  I have dropped to TTY's and tried running the configuration there to no avail.

If I do a recovery mode boot, and repair X, then I get mirrored desktops on my dual monitor, but the xorg.conf file is not using the Nvidia drivers.  Fair enough, I have verified that the correct drivers are installed and that the proprietary drivers are enabled and up to date. 

If I enable the proprietary drivers, and restart, the system goes back to low graphics mode.  If I do recovery - X - then the system functions but only one monitor, and no compiz.

I have a sneaky suspicion that my video card is failing and that linux is using whatever mode is available, but I want to be completely sure.  While logged in with the repaired x-config, I have one monitor (left) and one black (right).  I have advanced resolution options and other such nifty things.

I will be glad to post my xorg.conf file and the most recent one nvidia-xconfig created if it will help.

Someone please tell me what is going on here....
Thanks in advance!

---

### Post by designsedge on 2009-03-29
So after several attempts to get the card firing, I called a linux guru that I know.  I explained to him what was happening, and what I had attempted to remedy the situation.

Turns out several people (that we know) have had problems with these chipsets burning out.  Being a Windows convert, I had come to expect one of two scenarios - it works | it doesn't work.

Turns out Linux has a 3rd option - it works, at a lesser capacity.  In Windoze, the GPU fries, it goes to VGA mode only.  In Linux, it will run the video card without using the GPU - hence my loss of compiz, dual monitors, etc.

Although the "intermediate" state did cause some confusion...is it a configuration or drivers error, it allows me time to find a replacement card to use, I don't have to rush out and find one.

Way to go Linux & Ubuntu - I can still work, and use my computer to shop for my new video card!!
:guitar:

---

### Post by norwoods on 2009-03-29
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
these run very well on my system.

---

