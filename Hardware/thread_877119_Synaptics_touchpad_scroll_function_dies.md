---
title: "Synaptics touchpad scroll function dies"
date: 2008-08-01
forum: Hardware
---

### Post by charles.figura on 2008-08-01
I've got a Dell D620 Latitude running Kubuntu Hardy.  I've got the odd problem that on visiting certain websites, the scroll bar function on my touchpad dies.  Scroll along the right hand side of the touchpad works just fine before hand, and then fails after certain websites open.  Which ones?  It varies, although I suspect it may be connected to plugins/scripts.  It just happened to me after visiting CNN.com.  I don't have a good list of causal websites, but I'm going to try to keep track.

dmesg reports:
[ 8566.168694] psmouse.c: resync failed, issuing reconnect request
[ 8565.289472] input: PS/2 Mouse as /devices/virtual/input/input11
[ 8565.357132] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12

So, a couple questions:
1)  Anyone else see this behavior?
2)  Is there any way to prevent this (other than, as the doctor told the patient, "don't do that")?
3)  Is there any way to *restart* the scroll function?  So far, I've had to reboot if I want the scroll back.  Yuck.  I'll have to check if restarting the X server will suffice, but even that is a nasty thing to have to do with frequency.

I've tried installing gsynaptic and playing around a little with that, but there seems to be no effect.

Thanks!

-C

---

### Post by charles.figura on 2008-08-01
Okay, quick update - restarting the xserver DOES restore scroll function, but restarting firefox (and the 15-odd associated tabs) killed it again.  I did a dmesg -c just before it failed again, and a dmesg immediately after suggests that the wireless card may have been affected as well:

```

cfigura@nightfall:~$ dmesg
[ 9386.065221] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 9386.065237] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0263 ser 0x0000004B
[ 9388.051012] iwl3945: Can't stop Rx DMA.
[ 9388.051074] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 9390.176587] psmouse.c: resync failed, issuing reconnect request
[ 9390.226788] wlan0: authenticate with AP 00:1c:df:c3:6f:ff
[ 9390.228620] wlan0: authenticated
[ 9390.228623] wlan0: associate with AP 00:1c:df:c3:6f:ff
[ 9390.231151] wlan0: RX ReassocResp from 00:1c:df:c3:6f:ff (capab=0x421 status=0 aid=1)
[ 9390.231154] wlan0: associated
[ 9389.318537] input: PS/2 Mouse as /devices/virtual/input/input13
[ 9389.388544] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input14


```

Curiouser and curiouser, said Alice.

---

### Post by ToyKeeper on 2009-08-14
This just happened on my Dell d420, and I found an easier way to get it working again.  Instead of rebooting, go through a suspend and resume cycle.  On my system, this means... press Fn-Esc (Stand by), wait a few seconds, close the notebook lid, wait a few seconds, then open the lid.

Doing a suspend/resume cycle shouldn't be necessary, but at least it works.  It can also reset the wired or wireless NICs if they get wedged such that reloading the driver doesn't help.  However, this is the first time I've ever seen the touchpad spontaneously revert to PS/2 mode.

---

