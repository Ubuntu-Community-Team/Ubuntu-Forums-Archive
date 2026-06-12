---
title: "Video card &amp; Audio card not working after migrating from Windows XP to Ubuntu 11.04"
date: 2011-05-02
forum: Hardware
---

### Post by kwanylongy on 2011-05-02
Dear all,

    I'm a newbie to Ubuntu. 

    I just uninstalled Windows XP from my 10yrs old desktop and installed Ubuntu 11.04 :P. After the installation, the video and audio cards are not working.

    The video card and audio card of my desktop are built into the motherboard. From my experience in installing Windows XP on this machine, after installation, I would need to download and install the audio and video drivers from the motherboard's manufacturer [COLOR=Blue][website]("http://www.grandmars.com/driver_mainboard_ps85bl.htm")[/COLOR]. However, as the manufacturer only provides those drivers for Windows OSs (in zip & exe file formats),  I have no idea how I could install the video and audio drivers for my machine under Ubuntu.

    The motherboard is named "PS85-BL" manufactured by "Grandmars". Since it's a very old computer, I doubt they would give support to this problem. As such, I am turning to this forum to see if any Ubuntu guru would have a solution.


Below are the hardware specification of my machine (extracted from 'lshw' output):

CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz
RAM: 1280Mb
VGA compatible controller: Intel 82865G Integrated Graphics Controller
Multimedia audio controller: Intel Multimedia audio controller




Many Many thanks in advance!!

Best,


Carlos

---

### Post by kwanylongy on 2011-05-05
OK... here is an update

I generated the lshw output (in html format), which says the following devices are "unclaimed nodes", whilst all the other devices are "claimed"


Device 1
========
id:		generic
description:	System peripheral
product:	82865G/PE/P Processor to I/O Memory Interface
vendor:		Intel Corporation
physical id:	6
bus info:	pci@0000:00:06.0
version:	02
width:		32 bits
clock:		33MHz
configuration:	latency	= 0
resources:	memory	: fecf0000-fecf0fff


Device 2
========
id:		serial
description:	SMBus
product:	82801EB/ER (ICH5/ICH5R) SMBus Controller
vendor:		Intel Corporation
physical id:	1f.3
bus info:	pci@0000:00:1f.3
version:	02
width:		32 bits
clock:		33MHz
configuration:	latency	= 0
resources:	ioport	: 500(size=32)



I have been googling for 2 days for their drivers. 

For "82865G/PE/P Processor to I/O Memory Interface", I only managed to find driver installation files for windows but not for Linux/Ubuntu. Here is a link to one of the Windows installation file I found [http://www.downloadatoz.com/driver/item_257440.html](http://www.downloadatoz.com/driver/item_257440.html)


For the "82801EB/ER (ICH5/ICH5R) SMBus Controller", I found this site ([http://cateee.net/lkddb/web-lkddb/I2C_I801.html](http://cateee.net/lkddb/web-lkddb/I2C_I801.html)) which seems to provide code for installing the driver in Linux, but I have no idea how I should compile/install it.


Any help/suggestion would be much appreciated!!


Carlos

---

### Post by Evdalo on 2011-05-05
Install[ -->this<--]("http://fr.archive.ubuntu.com/ubuntu/pool/universe/f/freebsd-manpages/freebsd-manpages_7.2-1_all.deb") driver and reboot your machine,

Tell me about result :)

Source: [Ubuntu Manuals]("http://manpages.ubuntu.com/manpages/natty/man4/snd_cmi.4freebsd.html")

---

### Post by kwanylongy on 2011-05-06
> **Evdalo said:**
> Install[ -->this<--]("http://fr.archive.ubuntu.com/ubuntu/pool/universe/f/freebsd-manpages/freebsd-manpages_7.2-1_all.deb") driver and reboot your machine,

Tell me about result :)

Source: [Ubuntu Manuals]("http://manpages.ubuntu.com/manpages/natty/man4/snd_cmi.4freebsd.html")

I did that, but it didn't work. The 2 devices above are still "unclaimed"

The FreeBSD-manpages.deb file you recommended was of version 7.2-1, I had even updated the installation to the latest 8.1-1 version (using Update Manager), but still, it did not work.

Why would installing FreeBSD manpages help... may I please ask? (since I am curious and would like to learn as much as I can about computers)


Many many many THANKS for your help!!!  :P


Carlos

---

### Post by lidex on 2011-05-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kwanylongy on 2011-05-07
The ALSA info of my computer is here

[http://www.alsa-project.org/db/?f=71167bceb18ebd37bf504d3ada12c3dbb6d81b0b](http://www.alsa-project.org/db/?f=71167bceb18ebd37bf504d3ada12c3dbb6d81b0b)

Many Many Thanks :P

---

### Post by lidex on 2011-05-08
Get to know your mixers. Start with this:
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Make sure your PCM and Master levels are up.

---

### Post by kwanylongy on 2011-05-09
Thank you so much lidex!!! :D I got the sound card working!

I followed your instruction (with alsamixer), which I do have to confess I wasn't quite sure what I was doing, but suddenly the sound card started working!! :P


One further question, how do I check whether certain hardware is functioning other than 'lshw'?

With sound restored, I would think this would imply the "unclaimed" sound card node in the lshw output would become "claimed", yet it isn't.

I need to know this for my graphics card (which is also declared 'unclaimed' by lshw, [see above]), since I did try to install a driver that I found for it (i915Graphics.tar, from [http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=zht](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=zht)), but not sure if the installed driver was appropriate or if the installation was successful.


Thank you so much for your help! I wish one day could be as good and help out others in the forum!


Carlos

---

### Post by lidex on 2011-05-10
Did you try this version:
```
sudo lshw -C display
```

---

### Post by kwanylongy on 2011-05-20
I figured out what the problem was - It's Unity

My intel graphic card is not good enough for Unity, but Ubuntu installs Unity by default if the graphics card is an intel one.

I already have it configured to GNOME (ubuntu classic), and it works perfectly since.


Thanks again for your help, lidex and everyone! :D

---

