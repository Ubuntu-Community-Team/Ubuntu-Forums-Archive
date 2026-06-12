---
title: "Anyone using a Dell Studio XPS 1340?"
date: 2009-02-16
forum: Hardware
---

### Post by Jackster on 2009-02-16
Hey people, I just ordered a new Dell Studio XPS 1340 and I was wondering if anyone has it working with Ubuntu?

Looks like a great laptop, only thing I'm worried might let it down is any Linux incompatibility :(

---

### Post by aniketvb on 2009-02-18
I just received mine today. I dont have an Ubuntu live cd to try right now, but I tried a Fedora 10 64bit live cd. It did not get a gui the first time, so next time I booted with the vesa driver, I got the Gnome desktop. 

This issue is trivial as the latest nvidia driver supports nvidia 9400m, so once ubuntu/fedora is installed just put in nvidia 180.29 drivers.

The big issue is that the Fedora live cd did not recognise the atheros wifi card. (pci id 168c:002a) I dont know how Ubuntu 8.10 will behave, Will try it as soon as I get the cd.

---

### Post by Jackster on 2009-02-20
> **aniketvb said:**
> I just received mine today. I dont have an Ubuntu live cd to try right now, but I tried a Fedora 10 64bit live cd. It did not get a gui the first time, so next time I booted with the vesa driver, I got the Gnome desktop. 

This issue is trivial as the latest nvidia driver supports nvidia 9400m, so once ubuntu/fedora is installed just put in nvidia 180.29 drivers.

The big issue is that the Fedora live cd did not recognise the atheros wifi card. (pci id 168c:002a) I dont know how Ubuntu 8.10 will behave, Will try it as soon as I get the cd.

Ah, I thought wifi might be the main issue. I'm moving to the SXPS from a Macbook which also has an Atheros chip and didn't function with wifi under Linux until recently. Hopefully the wait for support won't be as long with this Atheros chip :(

---

### Post by Zuajiu on 2009-02-21
Hey,
I installed intrepid on my dell studio xps 13 2 weeks ago, works perfectly, only problem is I cannot get those damn nvidia drivers to work, keeps on killing the system, stopping xserver from starting...
Tell me if you get it working

---

### Post by skibota on 2009-02-21
look this

[http://ubuntuforums.org/showthread.php?t=1067944]("http://ubuntuforums.org/showthread.php?t=1067944")

---

### Post by forreststevens on 2009-02-23
Just wanted to add my experience for anyone searching for something similar. Fresh install of Intrepid, 8.10, on a brand new Dell XPS 1340 laptop dual booting with Vista, and with updates applied. Everything is working quite well so far, but I activated nVidia linux-restricted-modules (177) and then experienced the boot to a command prompt, no X-Windows.

To fix this, I booted to the recovery console and tried the &#8220;fix X&#8221; option which restored a default xorg.conf file. After doing an lspci discovered that the second of the two cards nVidia cards listsed is the 9400G, which for this laptop is the main display, and it was on bus &#8220;3:0:0&#8243;.

So to restore the nvidia specific portions of the xorg.conf file and configure it to use the right card of the SLI setup I did this:

nvidia-xconfig

&#8230; and added the 3:0:0 line to the Device section of the xorg.conf file:

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BusID "3:0:0"
EndSection

On the next boot everything came up fine and the nVidia drivers even went to the native 1200×800.  Hope this helps!

---

### Post by aniketvb on 2009-02-23
Ok guys, I have a small problem...what I want to know is do the speakers turn off after you plugin the earphones!?
If yes could you please tell me what version of alsa-driver and alsa-lib is there on you system. ?

---

### Post by ozzyprv on 2009-05-22
Just got mine two days ago. I inserted the installation (9.04) disc 5 minutes ago....the partition resizing is taking forever.

Did you delete the "Dell Recovery" partition (15 GB)? I did not (yet).

Will update the post later.

[COLOR="Red"]Edit1: No wonder why it was taking so long. The CD/DVD-ROM unit (slot) does not work. I contacted Dell and a new laptop is on its way...[/COLOR]
[COLOR="Magenta"]Edit2: Still haven't received my new laptop....[/COLOR]

[COLOR="Blue"]Edit3: Finally got the new laptop back, last Tuesday. Installed 9.04...working fine so far.[/COLOR]

---

### Post by Dr. Funkenstein on 2010-01-13
I bought one of the newer ones with NVIDIA G 210M card, Intel P9600, 4GB DDR3 RAM, and 128GB Samsung SSD.


I wiped all windows, recovery partitions, and OEM off of the drive, then used gparted and fdisk to align the drive for SSD:

```
fdisk -H 224 -S 56 /dev/sda
```After that I created my boot partition, my SWAP file, and my root partition using fdisk..... then I formated them all to use ext2 (I only had an old version of gparted..... If I were using a new one I would of used ext4 with journaling turned off): [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)


Then, since I'm an Arch user I used my FTP install disk (also an old version of Arch..... so another reason I had to use ext2 instead of ext4 ^has no journaling). Then I went ahead and installed everything as usual..... instead of my regular xfce4 I chose gnome to see what would work out of the box.


I was pleased with most stuff like the mulitmedia keys, and the webcam and microphone worked perfectly OTB, but I was very disappointed with NVIDIA. (I also never tried the Dell 1520 card but I'm sure it didn't work or would need a workaround) 


When I ran lspci it would recognize both my 9400M G motherboard integrated card, and my G 210M dedicated 512MB..... but my nvidia settings manager would not use the dedicated card (only the integrated memory) and I could not find a way to make xorg.conf use the G 210M with the BusId "PCI:2:0:0", so I am very disappointed in the whole Hybrid SLI stuff..... I might as well of just gotten the NVIDIA 9400G M with no upgrade of discrete graphics at all.


I also had a lot of problems with the NVIDIA G 210M crashing and freezing with the factory Windows 7 install and all of that Dell OEM crap. I thought it might have been the OEM stuff so I clean installed Windows 7 and aligned it for the SSD using align=64 (so the starting partition was divisible by 512 and 4096). Again..... nothing but crashing and freezing caused by the NVIDIA G 210M..... simple programs like Google Earth 5 would crash and freeze, even the Windows Experience Index test would constantly freeze my computer and I would have to restart the machine. And when I tried some Video Game benchmark demos it would crash my system and the nvidia driver would "stop responding" and have to restart.... or it would completely freeze up and require a reboot.


As for FPS benchmarks during the Street Fighter 4 demo, the G 210M ran at about 30.70 FPS while crashing every minute and having some video tearing, and the 9400M G (by its self) ran at about 22 FPS without crashing, but with more video tearing and choppiness.


So I'm returning this laptop tomorrow..... I'm sort of pissed because I can't find another ultraportable 13.3" inch laptop with 4GB DDR3 RAM, and a backlit keyboard (with nice chicklet style buttons), a fast Solid State Drive, a slot load cd/dvd drive, and a powerful Intel dual core (or better). This computer booted very fast, and when I took the time to format windows to be aligned for SSD (and use a SSD tweak utility) I had a score of 7.0 for the hard drive in the Windows Experience Index test..... and this article seemed to work for SSD alignment with Linux: [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)


What features I don't mind returning tomorrow are: 

- the NVIDIA G 210M and its Linux/Hybrid SLI/Hybrid Power bull crap (of course) 
- the weak and crackling speakers
- the lack of usb plugs (for my Alfa AWUSO36H USB wifi which needs 2 plugs next to each other)
- the very warm heat vent/bottom which might have been a problem in the very hot summertime
- and the average battery life which was about 3 hours brand new

---

### Post by DodgeV83 on 2010-01-17
> **Dr. Funkenstein said:**
> I bought one of the newer ones with NVIDIA G 210M card, Intel P9600, 4GB DDR3 RAM, and 128GB Samsung SSD.


I wiped all windows, recovery partitions, and OEM off of the drive, then used gparted and fdisk to align the drive for SSD:

```
fdisk -H 224 -S 56 /dev/sda
```After that I created my boot partition, my SWAP file, and my root partition using fdisk..... then I formated them all to use ext2 (I only had an old version of gparted..... If I were using a new one I would of used ext4 with journaling turned off): [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)


Then, since I'm an Arch user I used my FTP install disk (also an old version of Arch..... so another reason I had to use ext2 instead of ext4 ^has no journaling). Then I went ahead and installed everything as usual..... instead of my regular xfce4 I chose gnome to see what would work out of the box.


I was pleased with most stuff like the mulitmedia keys, and the webcam and microphone worked perfectly OTB, but I was very disappointed with NVIDIA. (I also never tried the Dell 1520 card but I'm sure it didn't work or would need a workaround) 


When I ran lspci it would recognize both my 9400M G motherboard integrated card, and my G 210M dedicated 512MB..... but my nvidia settings manager would not use the dedicated card (only the integrated memory) and I could not find a way to make xorg.conf use the G 210M with the BusId "PCI:2:0:0", so I am very disappointed in the whole Hybrid SLI stuff..... I might as well of just gotten the NVIDIA 9400G M with no upgrade of discrete graphics at all.


I also had a lot of problems with the NVIDIA G 210M crashing and freezing with the factory Windows 7 install and all of that Dell OEM crap. I thought it might have been the OEM stuff so I clean installed Windows 7 and aligned it for the SSD using align=64 (so the starting partition was divisible by 512 and 4096). Again..... nothing but crashing and freezing caused by the NVIDIA G 210M..... simple programs like Google Earth 5 would crash and freeze, even the Windows Experience Index test would constantly freeze my computer and I would have to restart the machine. And when I tried some Video Game benchmark demos it would crash my system and the nvidia driver would "stop responding" and have to restart.... or it would completely freeze up and require a reboot.


As for FPS benchmarks during the Street Fighter 4 demo, the G 210M ran at about 30.70 FPS while crashing every minute and having some video tearing, and the 9400M G (by its self) ran at about 22 FPS without crashing, but with more video tearing and choppiness.


So I'm returning this laptop tomorrow..... I'm sort of pissed because I can't find another ultraportable 13.3" inch laptop with 4GB DDR3 RAM, and a backlit keyboard (with nice chicklet style buttons), a fast Solid State Drive, a slot load cd/dvd drive, and a powerful Intel dual core (or better). This computer booted very fast, and when I took the time to format windows to be aligned for SSD (and use a SSD tweak utility) I had a score of 7.0 for the hard drive in the Windows Experience Index test..... and this article seemed to work for SSD alignment with Linux: [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)


What features I don't mind returning tomorrow are: 

- the NVIDIA G 210M and its Linux/Hybrid SLI/Hybrid Power bull crap (of course) 
- the weak and crackling speakers
- the lack of usb plugs (for my Alfa AWUSO36H USB wifi which needs 2 plugs next to each other)
- the very warm heat vent/bottom which might have been a problem in the very hot summertime
- and the average battery life which was about 3 hours brand new

For what it's worth, I just got the Dell Studio XPS 13 (1340) and experienced multiple crashes, bluescreens (related to the video card.  ...etc in Windows 7.  Well, the first thing I did when I got the machine is go to [www.nvidia.com](www.nvidia.com) and download the newest drivers.  After going back to the official Dell drivers the laptop came with (downloaded from their site) I have had nothing but joy from this machine. :)

Since I know the Linux drivers don't support Hybrid SLI, I've decided to run Windows 7 as a "backend" if you will, with Ubuntu running in Virtualbox.  I removed all unnecessary services and startup items (though I kept the Dell facial recognition to login ;)).  I have found this to be better than running Ubuntu and occasionally running Windows in Virtualbox for a few reasons:

[LIST]
[*]All drivers work perfectly (Hybrid SLI is great)
[*]Ubuntu is very light on resources, easily running in Virtualbox
[*]For those times you need a Windows box, it is already running natively
[*]Less Ubuntu bugs (Whenever I close my laptop lid on my Dell m1330 the screen always comes back on after a few minutes, networking issues...etc)
[*]No worrying about using Wine or having to reboot for gaming
[*]I have yet to come across an Ubuntu application which doesn't run well in Virtualbox, while many of my Windows applications do not run well in Virtualbox.
[/LIST]

All in all, I am extremely satisfied with this laptop.

Edit: Posted in both threads to help other's who are having trouble with this laptop.

---

