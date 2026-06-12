---
title: "Dell D600 wireless problem - ubuntu n00b"
date: 2009-05-10
forum: Hardware
---

### Post by drick on 2009-05-10
hi,

I just installed 9.04 on my Dell D600 and am trying to get the Broadcom drivers up and running.

doing a search here, i saw 2 recommendations, both of which i followed.

sug 1 - make sure wireless is enabled / on in BIOS (A16 if it matters) - done, it is

sug 2 - download current Broadcom drivers and enable in Ubuntu - done they are current, and enabled

after both of those the wireless NIC still isn't appearing on the network tab and wirless is greyed out on that tab.

what should i do next?

---

### Post by drick on 2009-05-10
ok, doing some more reading on this post:

[http://ubuntuforums.org/showthread.php?t=1134948](http://ubuntuforums.org/showthread.php?t=1134948)

it looks like i'm not alone.

when running this command: 

# sudo lshw -C network

 *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


my wireless connection shows disabled right now, and the fn+f2 command is not bringing it back on. looking in the bios i currently have it set it to application + fn/f2. 

i then change this to off, reboot. 

i then go back in, change it back to application + fn/f2 and now it works.

WEIRD!

---

### Post by drick on 2009-05-10
works as in i get a connection for 30s at a time before it drops for 5m, then re-connects for another 30s.

this really sucks, and there doesn't seem to be any clear "fix" just a lot of random suggestions that work for some people.

---

### Post by drick on 2009-05-10
bug #374603 submitted to launchpad

---

