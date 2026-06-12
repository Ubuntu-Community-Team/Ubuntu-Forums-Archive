---
title: "Wireless Not Working"
date: 2010-03-10
forum: Hardware
---

### Post by GreenRaccoon on 2010-03-10
I just installed Ubuntu 9.10 64 bit onto my Dell Inspiron 1525 laptop, and I'm dual booting with Windows Vista.

I also just installed my wireless driver for my Dell Wireless WLAN 1395 Mini-Card, which was a Broadcom STA Wireless driver.  As I was installing it, I checked what it was compatible with, and "1395" was on there so I'm sure it's the right one.

After this, I left-clicked network connections in the top right corner and connected to my network.  Great!  Next time I booted up my machine, I went to login to the network and nothing was there.  I right-clicked the icon.  It said "Wired connection" and under that "disconnected" (which was true since no ethernet cable was plugged in).  Under that, it said "Wireless connection" and under this it said "Disabled."

I tried everything I could think of to enable it.  I went under my hardware drivers and it said that my driver was activated and the green light was on.  My WiFi light on my laptop is also on (it wasn't before I installed the driver).

What's going on?  Anyone know?

---

### Post by capleton on 2010-03-10
Have you tried any tutorials?  Google suggests [this]("http://www.linux.com/news/enterprise/networking/8259-making-wireless-work-in-ubuntu") and [this]("http://www.linux.com/archive/feed/56946") I haven't read through them, but see if at least you can get a little more info so that I might be able to help!

---

### Post by GreenRaccoon on 2010-03-10
Thanks for those tutorials but they didn't fix it.

I also got this in Terminal (I added underscores where there should be spaces):

dan@ubuntu:~$ iwconfig
lo ______ no wireless extensions.

eth0 ____ no wireless extensions.

eth1 ____ IEEE 802.11  Nickname:""
________ Access Point: Not-Associated   
________ Link Quality:5  Signal level:0  Noise level:0
________ Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0 ___ no wireless extensions.

It didn't look right to me.  I have a WLAN card, so shouldn't there be a "wlan" or a "wlan0"?

---

### Post by capleton on 2010-03-10
Okay, let's start at the beginning.  Open a terminal and run ```
lshw
``` could you post what you get for output in the sections "*-network" it should be toward the end.  for me it's:  

*removed by user*

---

### Post by capleton on 2010-03-10
Also, I know on some dell laptops there's a wireless on-off key switch on the keyboard (either a button or a certain set of key-presses) that disables the hardware directly.  Make sure nothing like that is interfering.

And if I understand correctly, you did have the wireless working originally?

---

### Post by capleton on 2010-03-10
My wireless wasn't working either at first.  I used a tutorial found [here]("http://ohioloco.ubuntuforums.org/showthread.php?t=1394281#5").  See if you can't modify that code and those methods to suit your own hardware.




And finally, if all else fails, try [This.]("http://ubuntuforums.org/showthread.php?t=112526")

---

### Post by GreenRaccoon on 2010-03-10
Here's this:

*-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 01
                serial: 00:24:2b:7e:26:31
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:fe7fc000-fe7fffff

Also, the Wireless/Bluetooth switch on the side of the laptop is turned on.  The Wireless did work one time after I updated the driver, then it stopped working for some reason.  I did not change anything; I just restarted the computer.

I also was going to try using NDISwrapper.  I clicked on the .deb file and after I started installing it, an error came up that said that only one Software Management Tool could be running at one time.  I didn't know what that meant, but I didn't have any other windows running.  I had used a .deb file a couple days before in order to install my first Wireless driver.  Could this be interfering?

---

### Post by capleton on 2010-03-10
> **GreenGuitar1 said:**
> I clicked on the .deb file and after I started installing it, an error came up that said that only one Software Management Tool could be running at one time. I didn't know what that meant, but I didn't have any other windows running.   It means that something else like synaptic package manager is also running.  Open a terminal and run "top" to make sure that synaptic or anything similar isn't running.

Also, make sure you've tried reinstalling the wireless driver and restarting.  you know, "sudo aptitude reinstall <package name>"

---

### Post by GreenRaccoon on 2010-03-11
I tried reinstalling the old driver like you said and it didn't fix it.

I also figured out how to get through the NDISwrapper.  I got until the part where I was supposed to install the driver that I had downloaded.  The driver only had .sys and .dll files, but it needed a .ins file.

---

### Post by capleton on 2010-03-11
Sorry, I have never used NDISwrapper and can't be of any help there.  Goodluck though.  Wish I could've give you more info

---

