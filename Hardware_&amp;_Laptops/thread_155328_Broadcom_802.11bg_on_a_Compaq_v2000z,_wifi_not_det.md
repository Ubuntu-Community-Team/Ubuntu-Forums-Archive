---
title: "Broadcom 802.11b/g on a Compaq v2000z, wifi not detected"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by sauced on 2006-04-04
Hello, just got a new laptop so I thought its a good time to try the ubuntu distro everyone's talking about.  I like it a lot so far.  I'm having trouble getting my WiFi to work.  It seems that the device is not detected?  The keyboard light is lit up, so I know the device is on.  ubuntu's Device Manager shows it under USB devices and syslog shows activity of a USB device going up/down as I toggle the keyboard wifi button.

I have read these threads:

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)
[http://www.ubuntuforums.org/archive/index.php/t-84082.html](http://www.ubuntuforums.org/archive/index.php/t-84082.html)

And one thing I notice is no one mentions their card having bluetooth.  I ordered the "Broadcom 802.11b/g + Bluetooth Combo."  I know this wifi adapter may be a little different, but I know for a fact it uses the same exact driver file (tested on a winxp partition, and works!), so I'm not sure why I'm having this problem.

I used the Synaptics Package Manager to install ndiswrapper-utils.  I followed all the instructions, but I am unable to get the device detected.

```

sean@diegolnx:~$ uname -a
Linux diegolnx 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux
sean@diegolnx:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
sean@diegolnx:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
[b]sean@diegolnx:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present[/b]

```
 
Note that the proper output should be:
bcmwl5 driver present, **hardware present**

Anyone have any ideas?

---

### Post by sauced on 2006-04-04
I found this error in dmesg

[4295133.255000] APIC error on CPU0: 40(40)

It happens when I make the device go up/down by pressing the wifi button.  I searched the forum and someone suggested to pass the "noapci" option at boot but is that smart to do on a laptop?

---

### Post by sauced on 2006-04-04
I decided to try and see if disabling APIC would fix the problem.

According to this thread:
[http://www.ubuntuforums.org/showthread.php?t=148761](http://www.ubuntuforums.org/showthread.php?t=148761)

I first passed the option: "noapic nolapic" which fixed the APIC errors in dmesg, but my wifi was still not recognized.

I then tried "noapic acpi=noirq" which also fixed the APIC errors but my wifi was still not recognized and now the keyboard button doesn't work.

I'm gonna give up here, and I'll wait for someone to reply...

In my googling I have found a recent post in a forum about linux drivers for this chipset.. they seem to be very beta and are unsupported but I'm going to keep an eye on it...

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by sauced on 2006-04-05
bump.  i thought this was a popular laptop?

---

### Post by sauced on 2006-04-05
I found the problem!

HP had 2 different drivers for the Broadcom 802.11b/g chipset.  Unfortunately, both filenames were the same, so I didn't immediately notice I was using the old one (from 2005).  I downloaded the Revision 4.00 driver and it started right up!  The old driver didn't work with ndiswrapper!

Now I have to figure out how to connect to my AP...

---

