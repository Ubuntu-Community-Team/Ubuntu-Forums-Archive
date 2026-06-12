---
title: "HOWTO: Acer 5024WLMi wireless for 32bit version of Ubuntu"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by kaks on 2006-03-16
Hi everyone i think i have the wireless fixed for the Acer 5024WLMi. Im running Mandriva 2006 32bit version.

first you need to download ndiswrapper the newer version:
```

wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz
tar xvzf ndiswrapper-1.7.tar.gz
cd ndiswrapper-1.7
make
sudo make install

```

now get the driver from the acer website. The normal 32bit driver for broadcom:
```
wget ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip
unzip 80211g.zip 

```

now get the acer acpi:
```

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install

```

one note: # if make or make install fails try:
```

gzip acer_acpi.ko
sudo cp acer_acpi.ko.gz /lib/modules/`uname -r`/kernel/drivers/char/

```

Update module dependencies and load the acer_acpi module:
```

sudo depmod -a
sudo modprobe acer_acpi

```

The driver should be loaded and working now, but of course you have to make sure:
```

dmesg | grep acer

```

THE FOLLOWING I HAVE NOT ADDED AND IT WORKS IN MINE, BUT IF IT FAILS TO LOAD EVERY TIME THEN:
```

---
OPTIONAL:
Edit /etc/modprobe.preload in your favourite text editor and add the line acer_acpi.  Like this:


# /etc/modprobe.preload: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a `#', and everything on the line after them are ignored.
# this file is for module-init-tools (kernel 2.5 and above) ONLY
# for old kernel use /etc/modules

nvram
evdev
amd64-agp
acer_acpi


-------------------

```


install win32 drivers using ndiswrapper
```

cd 80211g su ndiswrapper -i bcmwl5.inf

```


check if driver is installed:
```

ndiswrapper -l

```


if it is installed you should get:
```

Installed drivers: bcmwl5 driver present, hardware present

```

next initialise the module
```

modprobe ndiswrapper

```

check if it is loaded
```

dmesg | grep ndis

```

next initialise acer_acpi
```

su 
modprobe acer_acpi 
cd /proc/acpi/acer 
chmod 777 .wireless 
echo "enabled: 1" >/proc/acpi/acer/wireless

```

check it worked
```

dmesg | grep acer_acpi

```

now it has initialised you should be able to scan for wireless networks.
```

iwlist wlan0 scan

```

you should get some info back.
----------------------------------------

Create Init Script
It is working for now but you don't want to initialise the modules on every boot. So you need to create a init script.
```

su cd /etc/init.d gedit wirelessAcerAcpi

```

add this text to the file, save and exit
```


#!/bin/sh 
	case "$1" in 
		start|"") 
			modprobe ndiswrapper 
			modprobe acer_acpi chmod 777 /proc/acpi/acer/wireless 
			echo "enabled: 1" >/proc/acpi/acer/wireless 
			;; 
		stop) 
			echo "enabled: 0" >/proc/acpi/acer/wireless 
			;; 
esac

```

make the file executable
```

chmod 755 /etc/init.d/wirelessAcerAcpi

```

add the script to startup
```

cd /etc/rc2.d ln -s ../init.d/wirelessAcerAcpi S99wirelessAcerAcpi

```

I WOULD LIKE TO REALLY THANK THE FOLLOWING SITES FOR ALL THE INFORMATION:
-------------
equilibrium for making the post:
[http://ubuntuforums.org/showthread.php?t=140007](http://ubuntuforums.org/showthread.php?t=140007)

and the following site for a veery nice reference:
[https://wiki.ubuntu.com/WifiDocs/Acer5021WLMi_Amd64?action=show&redirect=WiFiHowto%2FAcer5021WLMiConfiguration](https://wiki.ubuntu.com/WifiDocs/Acer5021WLMi_Amd64?action=show&redirect=WiFiHowto%2FAcer5021WLMiConfiguration)
-------------

I hope equilibrium doesnt mind that i borrowed some/most of the stuff. He has a post on getting this to work with ubuntu in 64bit, mine is for 32bit in mandriva. It should however work in other distros so please pass it around.
It took me a very very very long time of reading and getting frustrated with linux. I am a linux newbie, and i kind of feel proud for getting it to work.

Basically referring to the stuff above, this is what did the trick:

one note: # if make or make install fails try:
> 
```

gzip acer_acpi.ko
sudo cp acer_acpi.ko.gz /lib/modules/`uname -r`/kernel/drivers/char/

```


And some other commands after that :) heh.
One thing im also trying to get the rest of the keys working, and i dont think im far off, so i might make another post on that. 
I cant really answer most questions on linux as i am a newbie, put please do post maybe i can try and answer it or someone else might.
Also i tried installing acerhk, which didnt work. But it might be since i have both acer_acpi and acerhk then, the wireless worked. As far as i can tell its only when i did install acer_acpi that the wireless worked.

Oh and for all other newbies using the on and off script would work something like this:
```

to start:
./S99wirelessAcerAcpi start 
to stop:
./S99wirelessAcerAcpi stop

```

Thats all for now....
Thanks for listening :)
P.S  im having trouble with my senao nl-3054cb+, well basically i insert it in the pcmcia and it doesnt get detected at all. Not even as pcmcia, let alone make it work. please help!!

---

