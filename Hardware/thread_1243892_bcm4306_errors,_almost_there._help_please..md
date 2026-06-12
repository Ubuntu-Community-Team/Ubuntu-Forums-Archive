---
title: "bcm4306 errors, almost there. help please."
date: 2009-08-18
forum: Hardware
---

### Post by itdoesnot on 2009-08-18
hey i'm trying to get the built-in wireless card to work on my laptop
i'd done it before, so i know it's feasible. i set up a dual boot with windows xp
so i did fresh partitions. and i should have backed up my network settings.
either way, i've been at this for about 36 hours and i can't get it to work again.
i've learned alot though, still no wireless. the wireless indicator near the touchpad
lights, but there's nothing in network manager, i know i'm probably just missing
one small step somewhere but i can't figure it out. either way here are the details.

i had some errors starting with:
ndiswrapper -l

the details->

gateway 7330 gz
ubuntu 9.04 -linux kernel 2.6.28-15-generic
broadcom bcm4306 rev3
14E4:4320
used bcmwl5.sys, bcmwl5.inf
following/tried both:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
they're very similar. other guides haven't gotten me this far.
----------
i blacklisted bcm43xx
got the build-essentials
updated headers
symlinked to /lib/modules/2.6.28-15-generic/build
installed ndiswrapper
------------
everything to here i understand and came out perfect
(well except the headers)
----------------------------
Install the wireless driver using ndiswrapper:
---------------------------------
after 
sudo ndiswrapper -i /home/jose/drivers/bcmwl5.inf
-------------------------------------
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
--------------------------------------
just to see what came out of it ->
because the ndiswrapper wikipedia entry said it
would only have 3 files
------------------------------------------------
jose@ubuntu:/etc/ndiswrapper/bcmwl5$ ls
14E4:4311:1363:103C.5.conf  14E4:4319:1359:103C.5.conf
14E4:4311:1364:103C.5.conf  14E4:4319:135A:103C.5.conf
14E4:4311:1365:103C.5.conf  14E4:4319.5.conf
14E4:4311.5.conf            14E4:4320:00E7:0E11.5.conf
14E4:4312:135F:103C.5.conf  14E4:4320:12F4:103C.5.conf
14E4:4312:1360:103C.5.conf  14E4:4320:12F8:103C.5.conf
14E4:4312:1361:103C.5.conf  14E4:4320:12FA:103C.5.conf
14E4:4312:1362:103C.5.conf  14E4:4320:12FB:103C.5.conf
14E4:4312.5.conf            14E4:4320.5.conf
14E4:4318:1355:103C.5.conf  14E4:4324:12F9:103C.5.conf
14E4:4318:1356:103C.5.conf  14E4:4324:12FC:103C.5.conf
14E4:4318:1357:103C.5.conf  14E4:4324.5.conf
14E4:4318.5.conf            bcmwl5.inf
14E4:4319:1358:103C.5.conf  bcmwl5.sys
-----------------------------------------------
i'm not sure what -l does but it's in the guide
-------------------------------
jose@ubuntu:/etc/ndiswrapper/bcmwl5$ ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)
-----------------------------------------------
differing guides. other says copy .conf files, so
---------------------------------
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
-----------------------------
no errors. ^there. but my card is (i forget what command i got it with)
it's supposed to be 4320 not 4324 or 4324.5. 
----------------------------------------
sudo depmod -a
-----------------
this is supposed to load the module. at first it hangs,
but i came back to terminal and it was fine..
--------------------------
sudo modprobe ndiswrapper
-------------------------
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
--------------------------
guide says replace ndiswrappercommon with ndiswrapperutils or something
for this fatal error:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-
generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
not sure what to do,
---------------------------
/etc/iftab is empty.
-------------------
/etc/network/interfaces returns->

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto wlan0
iface wlan0 inet dhcp
---------------------------------
but i vaguely remember manually editing this at some point, i dont' think ndiswrapper did this
----------------------------------------------
iwconfig returns
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

pan0      no wireless extensions.
------------------------
that is my correct card
##sidenote: i think lo is supposed to say something
and i think i deleted its entry somewhere
--------------------------------------
returning to the guide
pasted this in the /etc/network/interfaces file
--------------------------------------
auto wlan0
iface wlan0 inet dhcp
wireless-essid your_essid
----------------------------
(99% certain "your_essid" doesn't need to be there but still..
make ndiswrapper permanent->
sudo ndiswrapper -m
--------------------------------
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
module configuration already contains alias directive
--------------------------------------------------
there was a line break between each "module configuratition alread..."
but it's stupid enough to paste them all here.
----------------------------------
sudo nano /etc/modprobe.d/ndiswrapper
---------------------------
came out empty. pasted this in there.
----------------------------------
alias wlan0 ndiswrapper
----------------
that should do it???? rebooting with fingers crossed. (halphazardly)
------------------------

network manager 0.7.0.100 now shows
the wireless icon. wireless not active icon.
wireless networks not managed, it says too.
though the wireless light below my touchpad 
(next to power, caps lock,etc..) is now on
i know for a fact that there is 4-5 wireless
networks in range at my exact physical location.

thanks if someone can help

---

### Post by Ayuthia on 2009-08-18
Have you tried the following:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```
It might be that the current b43 modules are still loaded and preventing the ndiswrapper module from working.

I am also not for sure if the copying of the 4324.conf file is going to help or not.  I don't know how much of a difference there is between the two.  It is another chipset of the 4306 card.

---

### Post by itdoesnot on 2009-08-19
sudo modprobe -r b43 ssb ndiswrapper
---------------------------
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ssb is in use.
---------------------------
i think ssb might have been loaded because at one point before i finished trying to set
up ndiswrapper for the built-in card, i inserted an external wireless LAN adapter
to see if it was functional; it worked without having to install drivers or configure anything.
but i rebooted the machine to see if that changed anything, and i still got the same output.
--------------------------------------
sudo modprobe ndiswrapper
-----------------------------------
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
-----------------------------
sudo iwlist scan
-----------------------------------
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
pan0      Interface doesn't support scanning.
-----------------------------------

thanks for helping me out man

---

### Post by itdoesnot on 2009-08-19
this is f'in impossible, i'm going doing a fresh install

---

### Post by sergiom99 on 2009-08-19
I dont think you need to use ndiswrapper and window$ drivers.
> 
Broadcom Wireless Card
**UPDATE**
The latest kernels have new broadcom drivers in them. To install the new drivers simply hook up your ethernet cable. Update. Reboot. Then go System > Administration > Hardware Drivers and check "Broadcom STA Wireless Driver." If you've already installed the broadcom drivers with my script simply run the uninstaller, reboot, and then follow the previous steps.

Check [here]("http://ubuntuforums.org/showthread.php?t=870575") for the full story.

---

### Post by itdoesnot on 2009-08-20
yeah but i think that only applies to (new/different?) broadcom cards
my "hardware drivers" tab is empty anyway and i have the latest kernel

---

