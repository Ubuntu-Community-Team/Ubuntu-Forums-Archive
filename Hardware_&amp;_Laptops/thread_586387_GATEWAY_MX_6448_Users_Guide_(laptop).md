---
title: "GATEWAY MX 6448 Users Guide (laptop)"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Selcal on 2007-10-22
I know I wasn't the only one that received that magical email from tiger direct about an inexpensive 'open box' or 'refurbished' Gateway computer.  I am sure you, like myself, went for it and purchased this little beauty in the hopes and dreams of spreading the joy of ubuntu throughout the cosmos.

I have been working with this thing for the past week and have installed "Gutsy Gibbon" to fully utilize all my hardware.  If you have found out something i haven't then lets, conglomerate our efforts.  There a lot of users out there for this computer, we are all in this together.

This is where i am at so far...

First things first, desktop effects.  I DID activate my restricted driver and did a restart.  As far as i knew, XGL xserver is required to get it just the way it needs to be for it all to be super hunky dory.

to get the xgl xserver
> sudo apt-get install xserver-xgl
this allowed me to use the pretty show off graphics that compiz is famous for.

Next i installed the applet from [http://art.gnome.org/]("http://art.gnome.org/").called Art manager to allow me to download all the themes, backgrounds, icons and such straight from their website.

to get the art manager do this
> sudo apt-get install gnome-art
it will give you an icon in System>Preferences> called 'Art Manager'

Next, i find it important to play DVDs on my laptop.  

You have not got all the pluggings to play some DVDs.. Open Terminal!

> sudo apt-get install ubuntu-restricted-extras
and do this as well
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs]
special thanks to UK-Wobbie

i popped in a DVD from the "masters of horror series" and it started right up.

for good measure i also installed the 'VLC player"  through the Applications>Add/Remove.  You never know when you will need a good player. 

I have reached a major impass when it came to using my integrated wireless adapter.  I did install the 'Firmware for Broadcom 43xxx chipset family' but my computer would not get about 0% signal strength and it would never connect, even without any security on my wireless.  I then proceeded to 'not in use' the thing and follow these directions. 

[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4311]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4311")

these instructions just got me into trouble and now my 'network-manager' applet doesn't even recognize that i have wifi capabilities.  I did go back to the restricted driver as well, but upon restart the wireless section of my applet just goes away again.  I am not in any kind of hurry to get my wireless working, but it would be nice to use it what it was meant for.  I have tried to use ndiswrapper but i don't know where i can get my driver.  I am currently attempting all that it says in here,

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

 since we have a BCM94311MCG min-pci adapter, more to come, if you see any problems with this guide please help me edit it.  I never claimed to be perfect but i like to think i could be borderline nerdsane.

---

### Post by Selcal on 2007-10-28
Okay i figured wireless out.  I had to do everything manually.  I removed NM-Applet and the WiFi-radar and reset my router.

then i used iwconfig such as below

> sudo modprobe ndiswrapper
sudo iwconfig  <-to see if wifi is on
sudo iwlist scanning  <-to see if it picks up your network
sudo iwconfig eth0 essid yournetworkname
sudo iwconfig eth0 key whateveryourkeygoeshere
sudo dhclient eth0  

(eth0 is my id, your may vary)

but i actually didin't use the key, i am just blocking mac address on my netgear router.  Thanks Sim777


i also fixed a black screen at boot up by following this one
1. It takes incredibly long time to start up. It takes roughly 3-4 mins to startup. I am attaching the bootchart. I am new to Ubuntu and stuff in the chart makes very little sense to me. I would appreciate if someone can please take minute or two and review the chart for me and advice on how can I fix this problem and speed up the boot process.

2. On startup the Ubuntu splash screen/logo with boot progress is missing. As I power on my machine, it loads Grub .. prompts starting up.. and goes blank screen ... and after a long wait screen goes little grayish and logon screen pops up. It seems running fine after that.
Here are the contents of my /etc/usplash.conf
# Usplash configuration file
xres=1280
yres=1024

---

### Post by Biyabo on 2007-11-04
I have problems with the sound, it doesn't work for me. I'll reattempt the process.

---

### Post by Selcal on 2007-11-05
Hey try this out,  I do remember having to re-instal the ALSA drivers and even update them.

> apt-get remove alsa-driver
apt-get remove kernel-module-alsa-`uname -r`

then follow up with 
> apt-get install kernel-module-alsa-`uname -r`=1.0.5a
apt-get install alsa-driver=1.0.5a


  If this doesn't work then follow parts of this guide.
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

