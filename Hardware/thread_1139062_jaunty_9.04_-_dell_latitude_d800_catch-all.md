---
title: "jaunty 9.04 - dell latitude d800 catch-all"
date: 2009-04-26
forum: Hardware
---

### Post by freonchill on 2009-04-26
i have had 7.10, 8.04 & 8.10 on my dell inspiron 1150 for about a year now

was waiting on 9.04 to put it on my latitude.

well, i was hoping that since over the previous builds that it would be fully supported out of the box.

pentium mobile - 1.6ghz (cpu speedstep works out of the box)
1gb pc2100 ram
60gb 7200rpm ide 2.5" hd
nvidia geforce 4 4200 mobile to 1920x1200 LCD - works with restricted driver (version 96)
AC97 sound - works (comments later)
keyboard - works
touchpad - works
ethernet - works out of the box
wifi - shows up as wmaster00 - does not work (comments later)
serial - did not test
parallel - did not test
dvdrom/cdrw - works (reads discs, havent tested burning)
pcmcia - did not test
IR - did not test
FN keys - brightness, sound work, cd eject, battery info, others not tested
suspend - does not work (assuming nvidia driver problem)
hibernate - does not work (assuming nvidia driver problem)

when installing, formatted drive as follows
55gb ext4
4gb swap

installing ubuntu from the cdr drive worked fine

was 800x600 before used wired ethernet to get nvidia restricted driver; havent tested s-video out port

installed vlc, opera, xchat, bootchart

AUDIO
it works, disabled sound themes
though the login sound is there there
and i need to figure out why there is a pc-speaker sound when i shutdown/reboot/suspend/hibernate - cant find a way to turn that off, even though i have de-selected "play sound alert" and "play sound effects"

also, i have killed the "startup applications" for "gnome login sound" though when it gets to the login, it still does the "drum beat" telling me i can login. i cant remember what i did on 8.10 to get that to go away...

WIFI
initially it did not work, there is an option for "enable wireless" on the "network manager" panel icon, but no networks detected

ifconfig showed lo, eth0, wmaster00

figured the driver was not installed (dell 1400 wifi card (BCM4309 802.11a/b/g [14e4:4324]) and since the restricted did not pick it up as it had for my dell inspiron 1150 (dell 1100 b/g mini-pci) i searched the forums here and found this tutorial...
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=7152253#post7152253](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=7152253#post7152253)

though, after doing that, i found no real changes other than having added wlan0, which still does not see any ESSID, either through "network manager" or "iwlist wlan0 scan"
```
user@machine:~$ iwlist wlan0 scan
wlan0     No scan results
```

[http://linuxwireless.org/](http://linuxwireless.org/) (do not know when webpage was last updated - but it says that the bcm4309 14e4:4324 is not supported

but several people on these forums have comments that they were able to get it working with ndiswrapper... though i have yet to find a way to do it.

SUSPEND / HIBERNATE
dont really know where to start to figure out why this isnt working...
please reply and tell me what information i need to do / give you to help figure out why this does not work, from previous experience (browsing the forums, etc) the nvidia driver has been a problem in the past, do not know if this is the problem)

it will suspend or hibernate successfully, but when i bring the laptop back up, it just sits at a black screen after loading the ubuntu load screen/bar... but never gets to login screen (as my 8.10 box)

any suggestions, comments, help would be much appreciated

---

### Post by freonchill on 2009-04-28
bump on suspend / hibernate diagnosis

---

### Post by GlennBoschmans on 2009-05-17
I have the same sound problem. I had the problem in 8.04, Linux Mint (based on Ubuntu 8.04) and now in 9.04. I had my hopes on that it would be fixed, but it seems like it is not. 

Did you find the solution?

---

### Post by GlennBoschmans on 2009-05-18
Solution for the beeps:

First, I installed the libs from this post: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html) , I guess only the libs concerning alsa are needed (asoundconf-gtk, gnome-alsamixer, alsa-oss).
After that I opened the alsa-mixer via Applications --> Sound and Video --> Alsa Mixer and there I put the PC Speaker on mute. It works like a charm!

---

### Post by barbara.surfdancer on 2009-06-04
with all your experiences, which Linux would you now recommend for a Dell Latitude D800?  (NVIDIA GeForce 4 4200, 1.256 RAM, 30 GB HDD)  I am playing with learning Linux, and this laptop crashed from/with Windows XP, so thought I'd rebuild it w/Linux .  I've started playing with Ununtu Hardy  (this is not my main computer for either work or home).  thx all

---

### Post by george314 on 2009-06-08
Here is a fix for dell d800 wireless if your wireless card is the Broadcom b43:

go to the following website:
[http://linuxwireless.org/en/users/Drivers/b43#firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#firmware_installation)

if you are using Ubuntu you can skip most of the stuff until you get to:
"In latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package:

          sudo apt-get install b43-fwcutter
          - when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter) "

then just reboot and connect to your wireless network
:p

Vili

---

### Post by freonchill on 2009-07-05
update

did a clean ubuntu 9.04 install after getting dell 2200BG wifi card
(since its pretty much impossible to get the wifi card i had (broadcom abg / dell 1400 card)

using ext4

it detected the screen correctly (1920x1200) before installing the nvidia driver. installing nvidia driver did break hibernate/suspend, but this was fixed by editing the Xorg.conf file adding the following "option" to fix the nvidia driver suspend/hibernate bug

Section "Device"
        Option  "NvAGP"         "1"
EndSection

then hibernate / suspend works. 

i am having a random problem with the machine locking-up, a hard lock-up. where everything just stops working - the mouse/keyboard does not do anything. and the screen does not update. had to force shutdown the machine (power button for 8 seconds). this did cause a problem with the drive, but fsck the drive seems to have fixed it. but i believe that might have to do with the harddrive and or a cmos battery problem (getting a replacement cmos battery and checking the drive)

ethernet works out of the box
keyboard and touchpad work out of the box
usb works
sound works
detects both batteries (primary and d-bay drive)

have NOT tested the following:
PARALLEL PORT
SERIAL PORT
D-BAY USB JACK
D-BAY DRIVE (CD/DVDRW)
PCMCIA
iR port
speaker/mic jack

need to see if there is a way to load the d-bay cdrw drive by just slotting it after removing the extra battery.

---

