---
title: "hibernation kills wireless on Acer Aspire in edgy"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by crazybilly on 2007-02-17
I've got an Acer Aspire 3003Wlci, one of the 3000 models.  After much head and heartache and nearly giving up on Linux altogether, I FINALLY got ndiswrapper working reliably with my Broadcom wireless card on Edgy (I complied ndiswrapper from source and blacklisted bcm43xx, btw).  Anyways, I'm now Ubuntu-ing it up.  The only thing that keeps me from making U my always-on OS (I'm dual-booting w/ xp) is the fact that hibernate and standby effectivly disable my wireless.  After doing either, my wireless just won't connect--I get symptoms very similar to when it wasn't working (the indicator led comes on, but wifi-radar says 'device does not support scanning).

I THINK what's happening is that somehow my power management isnt working right (gnome's power manager won't read my battery status as anything but 0% or 100%), and the wireless gets turned off and stays off, at least as far as the motherboard is concerned.

But I'm too much of a newb to know how to troubleshoot it.  I'd try the new kernel that just came out (I need to double check to see if it sees my battery better), but ndiswrapper isn't complied for it, and I'm afraid that if I start trying to get it working, I'll screw up my previous install somehow (any advice about how that all works?  I don't get where any of that information is stored or how it's stored and if I can screw anything up doing that).  

So, my questions are these:

1.  if recomplie ndiswrapper for the new kernel, am I going to screw up my old ndis install?
2.  any suggestions about the hibernation/wireless thing?

Thanks!

---

### Post by maxamillion on 2007-02-17
```
sudo ifup wlan0
sudo dhclient
```

Run that in the terminal when it comes back from hibernation (note: "wlan0" is just generally what wireless cards are called, yours might be different and if so, alter the command accordingly). I think what happens is that when it goes into hibernation it puts the interface in the "down" state and when it comes back it might not bring the interface back up and if it does then it isn't re-leasing an ip address.

---

### Post by crazybilly on 2007-02-18
Unfortunately, that didn't do it.  My wireless is wlan0, but when I hit ifup after hibernation, I get:

```
Ignoring unknown interface wlan0=wlan0
```

I tried ```
ifconfig wlan0
``` and got:

```
wlan0: error fetching interface information: Device not found
```
 
```
dhclient wlan0
```  gave me:

```
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
```

And clicking on the network monitor applet yielded an error dialog that says:

```
SIOCGIFFLAGS error: No such device
```

Any clues?

---

### Post by azim.manjee on 2007-05-22
I am having similar issues, and im a noob

---

### Post by crazybilly on 2007-05-23
hmmm...that's interesting.  using feisty seemed to have solved some of my problems in this area.  But I've got other (self-induced) power problems now.

I need to do some testing to see where I'm at w/ all this.

---

### Post by H.E. Pennypacker on 2007-05-23
Well, I was going to suggest that you do not upgrade to Feisty, but you've already done so.  My problems multiplied when I upgraded to Feisty.

Anyhow, I have the same issuing.  After returning from suspend or hibernation (neither actually work, but follow me), wireless is entirely gone.  The actual wireless interface disappears.  It's not an issue of being able to connect to the Internet or not.  Like I said, wlan0/eth1 is GONE.

The only way to solve this problem is to reboot.  Magically, wlan0/eth1 reappears.  Hmm...how's that possible, when Ubuntu said it does not exist?  It did exist, it does exist, and hibernating or suspending should not cease its existence.

---

### Post by Adrain on 2007-05-23
I'm having a similar problem in Feisty. I close the lid and put it in standby mode, and when I open it up it won't connect. The nm-applet still acts like it's connected, and it shows the 4-bars icon in the notification area like it's connected, but it's not.

---

### Post by crazybilly on 2007-05-25
I found [this bug report ]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/45696")last night.  It looks like it might apply.  I haven't delved too deeply into it yet to see if the work-around might solve our problem, though.

---

