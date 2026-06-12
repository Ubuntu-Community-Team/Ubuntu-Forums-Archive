---
title: "HP 2133 Wireless problems on Jaunty"
date: 2009-05-04
forum: Hardware
---

### Post by jtappin on 2009-05-04
Since I upgraded my HP2133 from Hardy to Jaunty (fresh install), I've been unable to make any headway with wireless.

Before I had it working using ndiswrapper, and was able to control it using wicd. But since installing Jaunty, I've not had a device: i.e. ifconfig just lists eth0 and lo.

The b43 module is loaded, and it pulls in a few others:
```

$ lsmod | grep b43
b43                   131484  0
mac80211              217208  1 b43
input_polldev          11912  1 b43
led_class              12036  2 b43,leds_hp_disk
ssb                    41220  1 b43

```
lspci lists the controller as:
```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

```
The "network management" plasma widget reports wlan0 as unavailable (I have tried switching the controller on/off).

I'm using the the openchrome display drivers from svn, as I've seen reports of a bad interaction between the packaged version and the wireless on this hardware - although in my case the behaviour was the same before & after (though X is better now).

Any suggestions?

---

### Post by igor. on 2009-05-06
Why not use jaunty's chrome drivers? I'm just using plain jaunty and wireless shows up for me. However after a while the connection breaks and I have to reboot.

---

### Post by igor. on 2009-05-06
We are not alone.

Some more info is here: [http://www.hp2133guide.com/forums/viewtopic.php?t=2065](http://www.hp2133guide.com/forums/viewtopic.php?t=2065)

---

### Post by jtappin on 2009-05-07
Turns out that the firmware is not automatically installed,
it is necessary to install the b43-fwcutter package (don't use kpackagekit on Kubuntu as that can't handle requests for user input).

---

### Post by thammyb on 2009-05-19
I think I found a way to fix the buggy wl driver in jaunty. I downloaded the source from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and compiled it according to the README.txt file. After that I replaced the wl.ko located in /lib/modules/2.6.28-11-generic/volatile/ and did the old "rmmod wl.ko" and then a "modprobe wl.ko". If this continues to work it's yet another victory for the wisdom of the ancient geeks: "Use the force -- compile the source".

Cheers,
Thammy

---

### Post by thammyb on 2009-05-19
Sorry about posting the hack before it was more extensively tested. The volatile directory is a tempfs mounted by linux-restricted-modules, [https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules) I suppose the most straight forward way to get your home brewn module mounted is to remove the one loaded by lrm. To do this, edit /etc/default/linux-restricted-modules-common to disable wl and then install the home brewn wl.ko some where in your module directory. I put mine in "/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/". You then have to run "depmod" to remap your modules. After doning this my system works fine. No disconnects yet.

---

