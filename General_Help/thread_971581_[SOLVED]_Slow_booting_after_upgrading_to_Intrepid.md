---
title: "[SOLVED] Slow booting after upgrading to Intrepid"
date: 2008-11-05
forum: General Help
---

### Post by aard on 2008-11-05
I'm new-ish to linux, so forgive my ignorance.
Since upgrading my system to Intrepid, my boot has been painfully slow. Can anyone tell me what causes it? (bootchart attached)
It seems to be related to networking. Is there any simple way (or less than simple, but with little chance of screwing the system up) to make it boot faster?

Also, is it normal that mount ntfs and networking seem to be loaded up twice? (or am I just reading the chart wrong?)

---

### Post by JamieKitson on 2008-11-05
Looks like a problem with your network setup. I would have a look in /etc/network/interface and remove anything that you don't use. eg, if you use wireless but not wired then remove eth0 references.

---

### Post by aard on 2008-11-05
Yes, I've been toying with the interfaces file for a few hours now. As far as I can see, eth0 doesn't even initialize (my ethernet port seems dead, but I don't use it anyway). But the weird thing is, eth1 (the wireless adapter) isn't even mentioned in the interfaces config :S

---

### Post by aard on 2008-11-05
Success! I seem to have solved the problem.
Maybe it's just some freak accident, but eliminating every adapter in the interface except for the first two lines has solves the problem. DHCP doesn't even run at boot now, but the network manager works and I can connect to the network without problems.
Thanks :)

---

### Post by JamieKitson on 2008-11-05
> eliminating every adapter in the interface except for the first two lines

Could you post a before an after?

> DHCP doesn't even run at boot now

So it runs later?

I am interested because I am disappointed with boot time myself after upgrading to intrepid and starting network is slow and I was happy as it was before, not waiting for it at boot.

---

### Post by aard on 2008-11-05
This was the interfaces list in the beginning:
```
auto lo
iface lo inet loopback

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

iface eth0 inet dhcp

auto eth0

```

now the list looks like this:
```
auto lo
iface lo inet loopback

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#iface eth0 inet dhcp
#auto eth0
```

In essence, leaving only the first two lines active.
I've attached the current bootchart. I don't see dhcp running anywhere during boot. My wireless still works, and I can connect to networks through the network manager.
Note: My ethernet port doesn't work, but it didn't work in heron either. Maybe I could turn it on, but I don't use it and am happy with the way it is. Be careful you don't turn your ethernet off :)

Oh, and, always make a backup of the file before editing (learned that the hard way a few years ago)

---

### Post by dthuk on 2008-11-30
I have just upgraded to Intrepid and had a 60s hang in the boot where nothing happened on my Dell Inspiron 6400. The above fix worked for me! So thank you so much for posting.

My etc/network/interfaces file now looks like:

> auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0

with the last two lines commented out as per the suggestions above.

What I would like to know though, what is going on here?
Everything still seems to work yet these lines caused the boot to hang for 60s, is this a bug?

Thanks again to all.

---

### Post by apoth on 2008-12-04
> **dthuk said:**
> I have just upgraded to Intrepid and had a 60s hang in the boot where nothing happened on my Dell Inspiron 6400. The above fix worked for me! So thank you so much for posting.

My etc/network/interfaces file now looks like:



with the last two lines commented out as per the suggestions above.

What I would like to know though, what is going on here?
Everything still seems to work yet these lines caused the boot to hang for 60s, is this a bug?

Thanks again to all.

Wow, same problem with me on an Inspiron 9400. This has changed my boot time from over a minute to about 15-20 seconds! Awesome!

---

