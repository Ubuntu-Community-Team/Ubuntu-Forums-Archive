---
title: "System will not resume from sleep, hibernate seems to work fine"
date: 2009-04-07
forum: Hardware
---

### Post by terigox on 2009-04-07
Hello everyone, I've been doing searching as well as off and on testing on this for a few weeks now and haven't found anyone with the same variation of this problem.

I have a Dell Latitude D830 with an up-to-date 8.10 loaded. I have been trying to sleep this laptop for some time to no avail. I did finnd however that hibernating works just fine; sleeping and resuming.

Here's what is happening:

Close laptop lid, or choose sleep from shutdown menu
Laptop seems to suspend to ram fine
Open lid, laptop power resumes, however a LCD backlit blank screen appears and the keyboard is un-responsive (tried testing by hitting caps lock).
Another thing I noticed is the wireless "light" to signal the wireless radio is on does not light up either.
I end up holding the power down to cut the power and restarting the machine.

I've tried looking at the syslog during the time at which it would resume, however nothing new is displayed in the log after the system was put to sleep.

Other people that seem to have this problem end up having video issues it sounds like, either the video never resumes correctly, but I would think if that was the case, the keyboard would still be responsive? Maybe I'm wrong here. I did try uninstalling the wireless driver I am using completely (which is the Broadcom B43 drivers) it didn't change the result at all.

Is there any other information that would be useful to help figure out what's going on here? I started messing with acpi, but it looks like Ubuntu 8.10 is dbus or something different for controlling sleep now by default?

[Edit]

Here are some of the logs during the events described above:

Syslog:
```
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  Sleeping...
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (eth0): now unmanaged
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (eth0): cleaning up...
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (eth0): taking down device.
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (wlan0): now unmanaged
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 30234
Apr  7 15:35:29 jason-laptop kernel: [66037.037924] wlan0: disassociating by local choice (reason=3)
Apr  7 15:35:29 jason-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess
Apr  7 15:35:29 jason-laptop avahi-daemon[5013]: Withdrawing address record for 30.248.222.189 on wlan0.
Apr  7 15:35:29 jason-laptop avahi-daemon[5013]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 30.248.222.189.
Apr  7 15:35:29 jason-laptop avahi-daemon[5013]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (wlan0): cleaning up...
Apr  7 15:35:29 jason-laptop NetworkManager: <info>  (wlan0): taking down device.
Apr  7 15:35:29 jason-laptop avahi-daemon[5013]: Withdrawing address record for fe80::21f:3aff:fe12:a85c on wlan0.
Apr  7 15:36:23 jason-laptop syslogd 1.5.0#2ubuntu6: restart.

```

Messages:
```
Apr  7 15:16:12 jason-laptop -- MARK --
Apr  7 15:36:23 jason-laptop syslogd 1.5.0#2ubuntu6: restart.

```



If anyone would like to see any other logs during this time let me know! Thanks for any help or ideas!

---

### Post by sites on 2009-04-08
Try the solutions on this thread.

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

---

### Post by terigox on 2009-04-08
Hey thanks for the response sites!

I see the first couple of steps in this are for nvidia specifically.

I have an Intel Corporation Mobile GM965/GL960 integrated video in this machine. I looked through the rest of the document and did find that

```
POST_VIDEO=false
```

is also set as the document describes in my /etc/default/acpi-support

I think I tried messing with some of these settings a while back but never saw any changes (I thought because my suspend methods didnt include acpi-support)

```
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"
```

I went through this file line-by-line comparing to a co-worker who is using Ubuntu 8.10 and has no issues suspending/resuming.

---

### Post by terigox on 2009-04-10
Selfish bump on this...

I'm thinking about upgrading to the beta this weekend to see if it by any chance resolves my issue.

Does anyone have any ideas as to what else might cause something like this?

---

### Post by linuxgr on 2009-04-11
We may have the same problem. Do you have an Nvidia card? Did you recently upgrade to the latest nvidia-glx driver? I posted a bug here with a workaround:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359401](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359401)

---

### Post by carnagex420x on 2009-09-08
Thanks, works perfect now! Damn BETA driver...

---

### Post by terigox on 2009-09-08
As being the OP, I don't have an Nvidia card in my D830 laptop. It's 
```
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

What I *DID* do though, because I have a colleage at work using the same exact laptop without problems on Ubuntu 32bit, I "downgraded" from 64 bit to 32 bit and everything has been working fine. There's a lot of variables here still to nail it to one thing, but it is in fact working fine on the same machine now.

I re-installed a fresh copy of 64-bit to test things out, and out of the box the system did not sleep correctly. So either I have some RAM problems, or 64 bit Ubuntu has some issues. I then switched to 32bit the next day, and what do ya know... it's been sleeping fine now for a couple of weeks.

All of this is on Ubuntu 9.04, all updates applied.

---

### Post by carnagex420x on 2009-09-28
I lied, switching from the BETA driver seemed to work at first but it didnt. I was getting a black screen with the 180 driver, then after switching back to the 177 driver, my screen would respond but my keyboard and mouse wouldn't. I had to make a small script to reload them but all is good now. I don't know who else is getting this but hope it helps...
[http://ubuntuforums.org/showthread.php?t=1047284&page=5](http://ubuntuforums.org/showthread.php?t=1047284&page=5)

---

