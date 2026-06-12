---
title: "[SOLVED] Problem installing wireless Dell Vostro 1000 Ubuntu 8.10 32bit"
date: 2008-05-27
forum: Hardware
---

### Post by nugget659 on 2008-05-27
Hello,

I am unable to get my wireless to work on my laptop.

I followed Dell's guide: [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

The driver installs, but the device is not recognized

```
 sudo ndiswrapper -l
bcmwl5 : driver installed
```

```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```


```
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
ndiswrapper
```

```
 cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx
```


From dmesg
```
[   42.275910] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[   42.351299] usbcore: registered new interface driver ndiswrapper
```
Those are the only two lines that reference ndiswrapper in dmesg

From lspci
```

05:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```

The wireless light lights up, but the wireless card is  not recognized in network-admin

Please let me know how to fix this or if I need to post any more information for troubleshooting.

Thanks.

---

### Post by pytheas22 on 2008-05-27
You shouldn't need to be using ndiswrapper with your card; it is supported by the native Linux driver.  You can use ndiswrapper if you really want, but it's a lot better to use a native driver when there's one available.  Try doing this:

1. In a terminal, type:

```
sudo gedit /etc/modprobe.d/blacklist
```

In the text file that comes up, add the lines:

```
blacklist b43
blacklist ndiswrapper
```

2. Also check to see if there's a line in the text file that says "blacklist bcm43xx."  If there is, delete this line.

3. Save the file.

4. install fwcutter:

```
sudo apt-get install bcm43xx-fwcutter
```

During the install, you will be asked if you want to automatically download firmware.  Select yes.

5. insert the wireless driver:

```
sudo modprobe bcm43xx
```

6. restart networking, and your card will hopefully be working:

```
sudo /etc/init.d/networking restart
```

If you run into any trouble, feel free to post.

---

### Post by nugget659 on 2008-05-27
I did what you said, but no go. My wireless light is on, but the card is not visible in network-admin or iwconfig

This is my blacklist:
```
cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist b43
blacklist ndiswrapper

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
```

What else can I do.

I tried rebooting when restarting the networking failed to work, still no go.

---

### Post by pytheas22 on 2008-05-27
What message did you get when you tried the /etc/init.d/networking restart command?

Also, are you positive that there's not a BIOS setting or physical switch that you need to enable in order to start your wireless card's radio?

What is the output of:

```
lshw -C Network
```

---

### Post by nugget659 on 2008-05-27
As far as a BIOS setting goes, I think there should be no problem, this system is dual boot, and XP does wireless. There is a Fn key to enable/disable wireless, but it appears to have no effect. The light above the keyboard which indicates the status of the wireless radio is lit, which indicates that the device is active.

lshw -C Network
```
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:bf:dc:d3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.42.142.216 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
```

```
 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                       [ OK ] 
```

---

### Post by pytheas22 on 2008-05-27
Try running:
```

sudo modprobe -v bcm43xx
```

and then run iwconfig again.  Do you see the interface listed?

---

### Post by nugget659 on 2008-05-27
This is what happened, still no go.

```
 sudo modprobe -v bcm43xx
[sudo] password for cory: 
insmod /lib/modules/2.6.24-17-generic/kernel/net/ieee80211/ieee80211_crypt.ko 
insmod /lib/modules/2.6.24-17-generic/kernel/net/ieee80211/ieee80211.ko 
insmod /lib/modules/2.6.24-17-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko 
insmod /lib/modules/2.6.24-17-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko 
cory@tool:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by pytheas22 on 2008-05-27
I'm sorry you're having such trouble.  I don't know what could be wrong other than that the bcm43xx module is not recognizing the device.  There's a tutorial at [http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946) that has you compile the bcm43xx driver from source; this might make a difference but I'm not sure.

The other option is to give up on the native driver and go back to ndiswrapper.  You could try following a different guide, like this one [http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html](http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html) .  Also you could try a few different versions of the Windows driver; it's been my experience that sometimes ndiswrapper doesn't work simply because it doesn't like the driver that it's wrapping around, but trying a different one makes it work.  Finally, you could apt-get remove --purge ndiswrapper, compile ndiswrapper from source and try again.  Don't forget to remove ndiswrapper from blacklist and put bcm43xx back in if you go this route.

---

### Post by nugget659 on 2008-05-28
I got the driver to work using ndiswrapper

I used the following driver
[http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

I am connected to wireless now.

Thank you!

---

### Post by stepet on 2008-06-20
I have the exact same problem with the same model (Vostro 1000, dual boot XP/Ubuntu 8, same set of drivers). I tried that driver and many different sets of suggestions, but nothing worked so far. How did you get it to work using ndiswrapper? Did you follow the Dell website instructions again from here? 
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")
They don't seem to cover the 1395 wireless cards.

Or the instructions here?
[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

Any help would be greatly appreciated.

---

### Post by Hatterwr on 2010-02-21
Ok I forgot where i saw this solution but this works for my Dell Vostro 1000 wireless card.

I installed Ubuntu yesterday so now you know my Ubuntu experience so this is an easy fix.

Open A terminal and ran these codes:

sudo apt-get update

sudo apt-get install bcmwl-kernel-source

I have no idea what those do but I do know after I reset, the linksys wireless appeared in my network connections.

Thank you hop this helps.

---

