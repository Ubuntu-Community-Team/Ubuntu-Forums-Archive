---
title: "Laptop display too small with Lucid"
date: 2010-07-17
forum: Hardware
---

### Post by Debbie on 2010-07-17
I installed xubuntu lucid on an elderly HP Pavilion N5415 laptop.  Everything went fine, except that the display is too small for my screen. There is a black border of about 1 1/2 inches all around the display, and I cannot find any way to stretch it to fill the screen.  The largest resolution it will give me is 800x600, but that is not my biggest problem.  I just want to use the whole screen.  This laptop was previously running gutsy with a normal full screen.  I saw something somewhere about manually editing xorg.conf, but cannot find that file in lucid.  Did they move it or rename it?

My question is, if I manually write an xorg.conf file and put it in /etc, will the system find and use it?  Gutsy said I had a Trident Microsystems CyberBlade/XP with 1024x768 resolution.  Fortunately, I did backup my old configuration file when I saw that the lucid live CD did not use the whole screen.  Or is there another way to fix this?  Thanks.

---

### Post by amsterdamharu on 2010-07-17
Not sure if this is still the same on lucid but is there a driver for your videocard available under&#65306;
System->Administration->Hardware Drivers

---

### Post by Debbie on 2010-07-18
All Hardware Drivers says is "No proprietary drivers are in use on this system"  which is not particularly helpful.  I don't know where to find information about what driver it is using.

---

### Post by amsterdamharu on 2010-07-19
Not sure if you are already using the latest driver but here is an old post that explains how to install the driver for your videocard:

[http://ubuntuforums.org/showthread.php?t=319261](http://ubuntuforums.org/showthread.php?t=319261)

> Went to Debian Unstable Packages website
packages.debian.org/unstable/allpackages.html
Downloaded the xserver-xorg-video-trident.deb file from the  xserver-xorg-video-trident package page
Extracted the trident_drv.so file from .deb with Archive Manager
Renamed the existing trident_drv.so in /usr/lib/xorg/modules/drivers/
Copied the new file to this location.
Restarted X

What is the output of the following commands? (you can copy and paste in the terminal)
```
lspci | grep VGA
sudo lshw -C video

```

---

### Post by Debbie on 2010-07-21
lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)

Here is the information you asked for.

sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/XP
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 63
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=64
       resources: memory:ec000000-edffffff memory:e8400000-e87fffff memory:ea000000-ebffffff memory:e8100000-e8107fff memory:30000000-3000ffff(prefetchable)

---

### Post by amsterdamharu on 2010-07-21
There is a trident driver but I can't be sure if it's the same one:
[http://packages.ubuntu.com/lucid/xserver-xorg-video-trident](http://packages.ubuntu.com/lucid/xserver-xorg-video-trident)

You can see if it's already installed by checking if any of these files are present:
usr/lib/xorg/modules/drivers/trident_drv.so[FONT=monospace]
[/FONT]/usr/share/bug/xserver-xorg-video-trident/script[FONT=monospace]
[/FONT]/usr/share/doc/xserver-xorg-video-trident/changelog.Debian.gz[FONT=monospace]
[/FONT]/usr/share/doc/xserver-xorg-video-trident/changelog.gz[FONT=monospace]
[/FONT]/usr/share/doc/xserver-xorg-video-trident/copyright[FONT=monospace]
[/FONT]/usr/share/man/man4/trident.4.gz

Googling for cyberblade gave me no hits:
site:packages.ubuntu.com cyberblade

This thread uses xorg.conf (page 4 and 5) but not sure if it'll fix your problem:
[http://ubuntuforums.org/showthread.php?t=806835&page=4](http://ubuntuforums.org/showthread.php?t=806835&page=4)

---

### Post by Debbie on 2010-07-22
It looks like I already have a trident driver installed with a date of 2009-12-07, so I assume it is a recent one.  I am going to try to create an xorg.conf file with the pertinent sections copied from the one that worked in Gutsy.  The worst that can happen is either nothing or I lose the graphic display. If I do lose the display, I should be able to delete the file and be back where I started.  Hopefully...:)

---

### Post by Debbie on 2010-07-22
Bravo!  I now have a full screen. :D Thanks for all your help. 

Here is my xorg.conf in case it will be useful to anyone.

Section "Device"
	Identifier	"Trident Microsystems CyberBlade/XP"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade/XP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

---

