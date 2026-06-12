---
title: "Connection drops with TP-LINK TL-wn821n v3"
date: 2012-07-16
forum: Hardware
---

### Post by Hirs on 2012-07-16
Hi,

After several minutes of starting a download at about 300KB/s the connection drops, generating this kernel output message:

[http://pastebin.com/aXfMD7g1](http://pastebin.com/aXfMD7g1)

I'm on ubuntu 12.4, but I have tried kernel 3.4.5 as well

There are some suggestions like:
[http://askubuntu.com/questions/70271/tp-link-tl-wn821n-automatically-disconnects](http://askubuntu.com/questions/70271/tp-link-tl-wn821n-automatically-disconnects)

None of the suggestions tried worked :(

What I have tried so far:
- Stop network-manager and manually start wpa_supplicant
- Disable hardware encryption (nohwcrypt in ath9k_htc module)
- Tested on kernel 3.2.0 and 3.4.5

lsusb outputs this:

```
Bus 001 Device 005: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]

```

Unpluging the dongle and plugin it again makes it work again, but of course temporarily. Replugin it for a third time won't work, forcing me to reboot to get connection again. Some times I have to reboot after the first failure.

If I limit the downloads at 50KB/s it can last several hours, but at some point crashes as well.

Any help will be apreciated!

Thanks.

---

### Post by chessmani on 2012-09-11
Hi,

Just wanted to drop by to say that I'm experiencing the same issue. The wireless dongle completely hangs after downloading a few MB (~400MB) straight away.

I've tested running KTorrent, and I've also tried compat-wireless 3.4.

Does anyone know what can be done about it? If this is not the correct place to report the bug, where can we report it?

Cheers.

---

### Post by gaothfanai on 2012-11-30
My system exhibits almost the same behavior.  I have the same lsusb output, and have never had a problem booting and acquiring a local wireless network.

I do not, however, get any syslog or kern log entries for when the USB card locks up.  The light on the device simply goes solid or turns off (seems random as to which it does), and access is no longer possible until I remove/reinsert the device.  When I tried to restart networking, I still had to manually pull the device out to get the restart to occur - it hangs during the retart until I do so.   After re-insterting the device, everything works as normal, until the next hang.  

I get the identical output as the thread originator, however lines 1-69 happen after the timeout (120 secs) I only get lines 70+ when I remove the card.

The potential for hanging seems directly proportional to amount of data pushed through the device, and much more likely when sending large amounts of data (in this case, audio files being transferred to another machine on my local net) as opposed to downloading (webpages, mail, etc.).

---

### Post by Hirs on 2012-11-30
There are a couple of bugs open on this matter:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049383)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971728)

I have tried on archlinux as well, same results.

I still have to try reducing the power as explained here:
[https://bbs.archlinux.org/viewtopic.php?id=136928](https://bbs.archlinux.org/viewtopic.php?id=136928)

---

### Post by kerryhall on 2013-05-14
I have the same problem, but I have a:
```

sudo lsusb | grep Atheros
Bus 003 Device 002: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]
```

So v2 vs v3. Different driver or same do you think?

---

