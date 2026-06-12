---
title: "Ubuntu hardware problems on HP DV6910"
date: 2008-09-27
forum: Hardware
---

### Post by lash9420 on 2008-09-27
Just went to go install Ubuntu on a fairly new HP DV6910. I installed on a desktop and everything just worked...not so here! Installations went fine, but when I went to go login, it the graphics looked all grainy. Thought once I got it I could just adjust the screen resolution. Helped a little, but not much to make a difference. Also, It would not configure my wireless card in my laptop. Should I reinstall, fix something...or what? any help would be greatly apperciated! Ubuntu is by far the best OS I've used. Thanks!

---

### Post by thePowerworks on 2008-10-07
I am having the same problem. Also the nvidia driver will not take for some odd reason.

The wireless adapter is not recognized.


Any ideas?

---

### Post by sergiom99 on 2008-10-07
you guys didn't post any hardware specs, so check if this guide applies to your hardware. Worked perfect with mine:
[http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)
Credits to dark_stang.

---

### Post by ckung on 2008-11-04
I have the same problem with Nvidia Geforce 7150M video driver issue and atheros 802.11 a/g/b wireless card driver when I installed the latest 8.10

Even those 2 drivers showed up in the hardware devices but it's not working properly.

I found the following link and wonder if others have any success. 

Re: Nvidia 7150m graphics supported?
[http://ubuntuforums.org/showthread.php?t=748857](http://ubuntuforums.org/showthread.php?t=748857)

Re: Atheros Wireless 

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/353009535931/r/352006835931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/353009535931/r/352006835931)

You want to use ath5k. It is included with Ubuntu 8.10.

Check lsmod and see if ath5k is loaded. If you also have ath_pci loaded, unload that. That's a bug. You can blacklist ath_pci in /etc/modprobe.d/. Inconvenient, I know.

By the way, it's not misidentification that makes your radio show up as AR2425. That's the actual part number. AR5007 is a marketing name.

Thanks!

---

### Post by ravl on 2008-11-05
I succeeded in getting my Nvidia GeForce 7150 working with Intrepid.

I used envyng to install the 173 version of the driver **not** the 177.

```
sudo aptitude install envyng-core
sudo envyng -t
```

Follow the prompts to install version 173, that worked on my HP Pavillion dv6810.

I´m still working on getting the Atheros AR242x to work right.

EDIT: I have my Atheros wifi card working now in Intrepid, doing this [http://ubuntuforums.org/showthread.php?t=970717]("http://ubuntuforums.org/showthread.php?t=970717")

---

### Post by ckung on 2008-11-07
Hi Ravl,

Thanks a lot for your help! Both my Nvidia and Atheros Wifi are working great now.

Wonder if you have any luck with bluetooth setup?
The Kdebluetooth 4 shows in the internet app. 

 
I can't get it working even the package is installed.

Thanks again!

---

### Post by ravl on 2008-11-07
Hmm... I hadn't even thought about Bluetooth. I will give it a try once I get home.

I'm glad I could help with the other stuff :)

---

### Post by ravl on 2008-11-07
I tried starting up KBluetooth4 from the K menu. Nothing happened.

I checked the process list, and found this:
```
$ ps -A | grep blue
 5196 ?        00:00:00 bluetoothd
 5704 ?        00:00:00 kblueplugd
 7443 ?        00:00:01 kbluetooth4

```

So I killed all of them and then did this:
```
$ kbluetooth4
kbluetooth4(13138) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "BlueZ"
kbluetooth4(13138) KBlueTray::offlineMode: offline Mode
```

As far as I know, this is not an error. The program started, but the system tray icon didn't appear.
Kbluetooth4 doesn't have a man page, as it's probably not meant to be used from the console, just from the tray icon.
And from the message I get, I think the program defaults to bluetooth off, and you need to turn it on from the missing system tray icon.

Hopefully someone with a better understanding of the new bluetooth platform can explain what's going on.

---

