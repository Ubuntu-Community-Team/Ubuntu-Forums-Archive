---
title: "Pinnacle HD Pro, HDA Intel, and Chicony webcam"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by calfax on 2007-11-27
Hi ,

Keywords: HDA Intel, ALSA,  Realtek ALC268, Chicony USB webcam, uvcvideo driver, em28xx driver, Pinnacle PCTV HD Pro TV tuner stick. 
     
Problem:  No sound with the Pinnacle HD Pro TV tuner stick when watching analog or digital TV.
Problem:  The ALSA driver loads and detects card but no sound is heard during playback.  The standard fix (upgrade to ALSA 1.0.15) breaks the em28xx-audio driver (kernel header mismatch...unknown symbols) 
Problem:  If the uvcvideo driver is loaded, TVtime confuses the input from webcam and attempts to play back from the webcam.  Standard fix (make kernel-links in v4l-dvb-experimental) breaks the uvcvideo driver (kernel header mismatch...unknown symbols).

Problem Summary: Damn...maybe I shoulda bought a Mac after all.  The Pinnacle supplied software doesn't work properly in Windows Vista either.

Solution: (note: I'm not an expert, follow my directions at your own risk)  Separate functions into 2 separate kernels.

Introduction: This is a slow and dirty guide to installing the em28xx driver for the Pinnacle PCTV HD PRO usb tv receiver stick with systems that have Intel HDA audio controllers and Chicony web cams. You see it at the store....on sale....HDTV ready...even comes with a remote.  Looks good right?  Hah!  Take it home and welcome to my nightmare... 
     
     I have a Toshiba A205-S4607 laptop with an Intel 82801G audio controller.  This audio controller  has a Realtek ALC268 chipset which uses the snd_hda_intel module.  A brief search of the Ubuntu forums, the Gentoo forums, and Google reveal that the HDA controller has been very difficult to get operating.  The word notorious was mentioned....more than once. 
     The Intel HDA controller is supported out of the box in Ubuntu Gutsy by the ALSA drivers but not for the Realtek ALC268 chipset.   Upgrading to ALSA 1.0.15 supports this chipset and you can easily compile and install an out of kernel ALSA by following the directions on the ALSA website or by checking out this post: 

[http://ubuntuforums.org/showthread.php?t=551615]("http://ubuntuforums.org/showthread.php?t=551615")

and this one :
[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]
https://help.ubuntu.com/community/HdaIntelSoundHowto[/URL]

However, the em28xx modules necessary to run the audio for the Pinnacle HD Pro USB stick will not work with an out of kernel ALSA 1.0.15 modules.  You will have sound on your computer but no sound on your TV.

So you must recompile the ALSA 1.0.14 drivers and load them into your kernel before you compile the em28xx modules.  But, before you  do that, you must compile a second kernel if you want to use your Chicony webcam.  And before you do that......you must must have an enchanted staff and the Helm of Torvalds and a scroll of Kernel Hacking.  It's like just like WOW except you don't get to kill anything....except all your important files.  Go forth and compile, you undead mage because it will take all night.

So step 1:  Back up your important data and file you really want to keep.  Put them on some external media or a partition that you can access later.  If you screw up a kernel compile too badly, reformatting is usually the easiest way to solve the problem.

Step 2:  Compile a new kernel.  We're not going to do anything with it right now but get it done first. That way, if your current kernel tanks, you still have a way to use your system to recover.  The Master Kernel thread on Ubuntu forums is the best? safest? easiest? way to build new kernels in Ubuntu.  There is also a nice utility called kernelcheck available thru Apt that does most of the heavy lifting in kernel building.

Check out the Master Kernel thread here:

[http://ubuntuforums.org/showthread.php?t=311158&highlight=poll+master+kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=poll+master+kernel")

Step 3:  Did you successfully make a new kernel?  Did it boot properly?  Everything work alright? Ok, boot into your regular kernel (at the time of this writing 2.6.22-14-generic).  We are going to patch the ALSA driver that came with the kernel.
	3a: Get alsa-source from apt or synaptic
	> sudo apt-get install alsa-source
	3b:  This will place an archive (alsa-driver.tar.bz2) in /usr/src/
                   Go ahead and extract it there which should produce a dir called alsa-driver in /usr/src
            3c: Change to root (either “su root” or “sudo -s” and enter /usr/src/alsa-driver
            3d: Insert the realtek patches either from the ALSA driver from the Reaktek site or from the realtek12.tar.gz archive in this bug report:
[URL="https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104"]
https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104[/URL] 

           Insert hda_proc.c and patch_realtek.c into /usr/src/alsa-driver/pci/hda/ and copy over the existing files.  Then recompile and install this driver.
           make clean --> ./configure --> make --> make install (you should still be root otherwise sudo make install).
           Then reboot.
           3e:   Did you hear that?  No?  Well, neither did I at first but what I wound up doing was deleting the alsa source archive in /usr/src and pasting in the ALSA1.0.14 source archive from the ALSA website, extracting it to a folder alsa-driver-1.0.14 in /usr/src/.  Compile the module, again inserting the patch files, and reboot.  You should hear sound now.  If that doesn't work, test an out of kernel compile of ALSA 1.0.15 and see if that works.  The end result is that you want a successful patch of the in-kernel alsa module that matches the ALSA headers so that everything says ALSA 1.0.14

Step 4:  Install the em28xx drivers.  These module are under heavy development.   You will also need  Mercurial (available from apt or synaptic).  How to install the modules can be viewed here.

[http://mcentral.de/wiki/index.php/Em2880]("http://mcentral.de/wiki/index.php/Em2880")

	4a: After compiling the modules, type 

> sudo modprobe em28xx

	and plug in your TV tuner.  Check dmesg and you should see an indication that your card has been detected, something like this:

> Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
xc3028-tuner.c: firmware 2.7
ANALOG TV REQUEST
em28xx #0: V4L2 device registered as /dev/video0
em28xx #0: Found Pinnacle PCTV HD Pro
usbcore: registered new interface driver em28xx
em28xx-audio.c: probing for em28x1 non standard usbaudio
em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
Em28xx: Initialized (Em28xx Audio Extension) extension


Next, get Tvtime and sox (available from Apt or Synaptic).   You should see pictures but this module uses OSS to process analog sound so you have to run the audio output thru sox in order to hear sound.

You can use this handy shell script (thanks to whomever wrote it) to open Tvtime with sox and have the sound synced to video properly. 

> #/bin/bash 

/usr/bin/tvtime &

/bin/sleep .25

sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

You may have to play around with Tvtime and sox to get it to work right.  For more on that go here:

[http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html")

Step 5: Hopefully you have gotten em28xx going and you are able to watch TV.  Reboot into your new/other kernel and install ALSA 1.0.15 as above in your new kernel.  Now you got sound.  Then get the uvcvideo modules from:

[http://linux-uvc.berlios.de/#download]("http://linux-uvc.berlios.de/#download")

You will need Subversion (available from apt).

Compile the driver and then type:

> sudo modprobe uvcvideo

and fire up your webcam.  If you can see your tired, pasty unshaven face, that means you are hereby awarded 1500 experience points!  Congrats on leveling up.

The various sources I pulled this information from indicate that Ubuntu plans to support these modules in future releases.  I sure hope so.  

Additional resources:[URL="http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices"]
http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices[/URL]
[http://www.linuxtv.org/]("http://www.linuxtv.org/")
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
[http://ubuntuforums.org/showthread.php?t=568463]("http://ubuntuforums.org/showthread.php?t=568463")
[http://www.kroah.com/lkn/]("http://www.kroah.com/lkn/")
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")
[http://mcentral.de/mailman/listinfo/em28xx]("http://mcentral.de/mailman/listinfo/em28xx")
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

---

### Post by master_kernel on 2007-11-27
KernelCheck is in apt? :)

---

### Post by calfax on 2007-11-27
I was mistaken.  Kernelcheck is not available through apt or synaptic.  It is available here: 

[http://kcheck.sourceforge.net/]("http://kcheck.sourceforge.net/")

and is easy to install with a simple python setup script.

---

### Post by master_kernel on 2007-11-27
> **calfax said:**
> I was mistaken.  Kernelcheck is not available through apt or synaptic.  It is available here: 

[http://kcheck.sourceforge.net/]("http://kcheck.sourceforge.net/")

and is easy to install with a simple python setup script.
Thanks. I'm the author of KernelCheck and I didn't want people to get confused.

master_kernel

---

### Post by psyced on 2008-04-16
Thanks for this guide, I finally found this after trial and error for ~4.5hrs. (works wonderfully, though I just used the sox bit because I wasn't getting audio in tvtime)

---

### Post by Yellow Pasque on 2008-04-16
ALSA 1.0.16 is out now and the process has been scripted for ease:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

