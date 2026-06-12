---
title: "Anyone tried the pchdtv card for Linux?"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by coolbreeze on 2005-04-01
I found this while googling and wondered how well this card works with Ubuntu.  It's a HD TV card built just for Linux!

[http://www.pchdtv.com/](http://www.pchdtv.com/)

Any feedback?

---

### Post by tube013 on 2005-04-01
I have as pchdtv 3000 card but it is in a mandrake box, I just haven't gotten around to switching it to ubuntu.  I also have an air2pc card which is a atsc dvb card with linux support with the latest linux-dvb driver.  I also have this card and have it working in an ubuntu amd64 machine.  It does require compiling cvs version of the dvb modules though.

---

### Post by coolbreeze on 2005-04-02
How well does the card work in mandrake box?

---

### Post by jarnold_ubuntu on 2005-05-16
I've got the PCHDTV 300 card working on my Hoary machine.  I installed the 2.0 drivers off the pchdtv website and rebooted and everything detected perfectly.  Works great in tvtime though I'm having a couple (unrelated?) minor issues with mythtv.

---

### Post by Drain on 2005-05-17
[QUOTE=jarnold_ubuntu]I've got the PCHDTV 300 card working on my Hoary machine.  I installed the 2.0 drivers off the pchdtv website and rebooted and everything detected perfectly.  Works great in tvtime though I'm having a couple (unrelated?) minor issues with mythtv.[/QUOTE]

Ah, I envy you at the moment. :-) 

I've got the HD-3000 installed, the 2.0 drivers downloaded, and problems with the make/make install. :-P Of course, this might be related to using AMD64 stuff instead of the tried-and-tested x86 stuff, but I'm not going to tinker with it without some more sleep right now. Have any suggestions or howtos or anything for compiling the driver? I'd certainly appreciate it.

---

### Post by Drain on 2005-05-20
[QUOTE=Drain]Have any suggestions or howtos or anything for compiling the driver? I'd certainly appreciate it.[/QUOTE]

The joys of apt-get. ;-) My HD-3000 card works just fine.

So I have the driver working by changing my apt-get sources.list, and then downloading a new 2.6.12 release kernel. Although I'm still doing some configuration to get channels, I can report that the pcHDTV card works under Ubuntu. I know that by the October release, it will be auto-detected - I just hope that Ubuntu developers consider packages to add functionality to xine and other media players in order to take full advantage. (Hey, Mark Shuttleworth, you listening? can you hire the guys over at Knoppmyth? ;-) 'Cause that'd be waaaaay cool). 

Anyway, here was my process:
Step 1. Edit the sources.list file to change hoary to breezy for all the repositories. 
Step 2. apt-get update and apt-get dist-upgrade. (I went and switched over fully to breezy badger, which is unstable. BE CAREFUL, 'cause that can break other things I suppose that you can skip the dist-upgrade, and go right to the next step, but I could be wrong and take no responsibility  [-X ).
Step 3. apt-cache search for the appropriate kernel for your processor (and hopefully find something that says 2.6.12 or higher. ) apt-get install that. 
Step 4. reboot. You may have to reinstall your video drivers (see [www.ubuntuguide.org](www.ubuntuguide.org) for the great nvidia card install instructions). 
Step 6. There is no step 6.
Step 7. dmesg - look for cx88 and DVB in the output, and that should show that your HD card is running. 
Step 8. You take it from there. Good luck!

---

### Post by Az7 on 2005-07-17
What steps did you take to compile the drivers? 
i've untarred them to /pcHDTV-2.0 and ran make but i get the following errors

```
make -C /lib/modules/2.6.10-5-386 /build SUBDIRS=/pcHDTV-2.0 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386'
make[1]: *** No rule to make target `/build'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386'
make: *** [default] Error 2
```

i'm running hoary i386.

---

### Post by varunus on 2005-07-17
Az7,

It looks like you don't have your kernel headers installed.  Install the corresponding "linux-headers" package to your kernel version from synaptic (looks like you should get linux-headers-2.6.10-5-i386).

---

### Post by Az7 on 2005-07-19
i tried 
```
apt-get install linux-headers-2.6.10-5 linux-headers-2.6.10-5-386 linux-headers-386 linux-kernel-headers
```

still receiving the same error.

---

### Post by phewner on 2005-07-31
Ok, so I managed to get the HD3000 working in Hoary, but it took a little bit of doing.  Here's what I did:

1.  First off, the problem with missing headers when you try to make the pcHDTV-2.0 drivers (that's the problem you're seeing right now).  You need to run this command:

sudo apt-get install build-essential linux-headers-`uname -r`

I got that info from here: [http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module](http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module)

The next three problems occured when I tried to do a make install.  They were:

2a.  The driver installation was looking for a directory /lib/modules/2.6.10 while the correct directory seemed to be /lib/modules/2.6.10-5-386.  A little symlink took care of that:

sudo ln -s /lib/modules/2.6.10-5-386 /lib/modules/2.6.10

2b.  The make install was looking for a entry FIRMWARE_DIR in the file /etc/hotplug/firmware.agent but the Ubuntu edition has a FIRMWARE_DIRS entry.  Looking around /lib/hotplug/firmware seemed to be where all the other firmware was.  So I edited the Makefile itself, changing the DESTF entry so it looks like this.

DESTF           := /lib/hotplug/firmware

2c.  The installation was trying to modify modprobe.conf but Ubuntu uses a modprobe directory (modprobe.d) so it was failing.

I created a modprobe.conf

sudo touch /etc/modprobe.conf

Then I ran the make install so it did what it needed to do to that file.  Then I moved the file into the modprobe.d directory

sudo mv /etc/modprobe.config /etc/modprobe.d

After these three steps, the whole thing compiled and installed sucessfully.  I  ran this: 

modprobe cx88-dvb

And tvtime started working....except there was no sound.

3.  To get sound working, I used the included crossthrough cable to pass my HD-3000 line out to the line in on my soundcard.  Then, after a ton of useless messing with the gnome-volume control, I downloaded aumix:

sudo apt-get install aumix

Running aumix and turing the Vol Pcm Spkr, Line and Pcm2 inputs up pretty high seemed to work.  I don't know if this was a necessary step or just an indosyncracy of my sound card though.

Anyways, good luck!

Mike

---

### Post by Az7 on 2005-08-01
Thanks phewner, your directions worked perfectly until step 3.  When i fired up tvtime i got a blank blue screen with "cannot open capture device /dev/video0", "no video source", and "no signal".  I'm using a ATI Radeon 9600 XT with xorg-driver-fglrx.

---

### Post by Az7 on 2005-08-04
Actually i switched pci slots and everything worked fine.. There was some tweaking because Bender was white (as opposed to metallic grey).. Hue 100% Contrast 21% Brightness 75% Color/Saturation 48%..  Thanks again.

---

