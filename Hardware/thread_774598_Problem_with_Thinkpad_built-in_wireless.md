---
title: "Problem with Thinkpad built-in wireless"
date: 2008-04-29
forum: Hardware
---

### Post by ExquisiteDeadGuy on 2008-04-29
Hey everyone,

Just got a used Thinkpad R40 with built in wireless. I installed 8.04, everything works great, except I can't connect to my wireless network.

Encryption/MAC filtering/etc is turned off on the router. I entered the essid into the network applet and it just sits there and spins for a couple minutes, then goes back to the problem icon.

I checked my syslog, it shows something like the following:

Activation (ath0) started
Stage 1 scheduled
Stage 1 started
Stage 2 scheduled
Stage 1 complete
Stage 2 starting
SUP: sending command 'INERFACE_ADD ath0 madwifi /var/run/wpa_supplicant0
SUP: response was 'OK'
SUP: sending command 'AP_SCAN 1'
SUP: response was 'OK'
sending command 'ADD_NETWORK'
SUP: response was '0'
SUP: sending command 'SET_NETWORK 0 ssid xxxxxxxxxxxx'
SUP: response was 'OK'
SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
SUP: response was 'OK'
SUP: sending command 'ENABLE_NETWORK 0'
SUP: response was 'OK'
Activation Stage 2 of 5 complete
Old device ath0 activation, won't change.
last message repeated 7 times
Activation (ath0/wireless): association took too long (>120s), failing activation
Activation (ath0) failure scheduled
Activation (ath0) failed for access point (xxxxxxxx)
Activation (ath0) failed.
Deactivation device ath0


Does anybody have any idea what could be happening? My router logs don't show anything. Also, the laptop is sitting 3 feet from the router.

Thanks!

---

### Post by Whiffle on 2008-04-29
Looks like its tryingto use encryption of some sort.  What happens when you do

iwconfig ath0 essid <essid of access point>

and then

dhclient ath0

---

### Post by ExquisiteDeadGuy on 2008-04-29
> **Whiffle said:**
> Looks like its tryingto use encryption of some sort.  What happens when you do

iwconfig ath0 essid <essid of access point>

and then

dhclient ath0

Thanks so much for the reply!

I entered those commands, it still wasn't connected, but then I clicked the network manager icon and clicked the network and it connected this time.

Should I just run those commands each time I boot before using the network manager?

Thanks!

---

### Post by Whiffle on 2008-04-29
Well, those commands don't really change anything that networkmanager wouldn't change.  I think I'd just watch it a bit and see what it does, networkmanager might have been confused for some reason the first time  you tried it.

---

### Post by ExquisiteDeadGuy on 2008-04-29
> **Whiffle said:**
> Well, those commands don't really change anything that networkmanager wouldn't change.  I think I'd just watch it a bit and see what it does, networkmanager might have been confused for some reason the first time  you tried it.

OK, thanks. I'll keep the forums posted if anything further develops.

Thanks again

---

