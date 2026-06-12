---
title: "Need to unplug/plug in USB dongle each boot"
date: 2008-10-11
forum: Hardware
---

### Post by locoloic on 2008-10-11
Hi all,
quite a small but annoying problem I'm having with Ubuntu Hardy Heron. I've got a Logitech bluetooth keyboard and mouse and it works a treat - the only issue is that I need to unplug and plug in the bluetooth dongle each time I get to the login screen before it recognises it. Is there something I can do in startup to work around this?

as always, many thanks in advance for your help.

Loic.

---

### Post by locoloic on 2008-10-14
any ideas?

Thanks.

---

### Post by sparky-steve on 2008-10-16
Hiya

I'm at work at the moment so cant try it, but I just found this:

[http://ubuntuforums.org/showthread.php?t=432013](http://ubuntuforums.org/showthread.php?t=432013)

The thread was last used 6 days ago with Hardy, and seems to be working. I'll be trying it tonight & will report back if you havent already done so.

Hope it helps

SS

---

### Post by locoloic on 2008-10-19
Hello,

I have followed the guide, but just can't get it to work!

Previously, I believe I wasn't settig up the dongle corretcly - you need to press the button as you plug it in for it to go into true bluetooth mode - before I wasn't seeing the BT icon in the gnome bar.

So, got that going, I have found the MAC addresses of the devices (they're printed on them, but double checked by finding the devices in Terminal), and added the line in the /etc/default/bluetooth file as per the guide. Further, I changed the two areas in the init.d/bluetooth file.

However, it simply will not pair up! Going into the bluetooth preferences, I have added the keyboard and mouse as trusted devices, but these do not appear as connected when I log in.

As a test, I went to Bluetooth icon -> Preferences -> Browse Devices then selected my keyboard/mouse and selected connect. It returned the error:

Couldn't Display "obex://[00:07:61:3C:DD:23]/" 
Error: Host down

It just seems that the only way I can get my devices to work is to either  unplug/replug in the dongle to get it into emulation mode, or to log in with a wired keyboard, then put the devices in discoverable mode and search for them again. Very frustrating.

I have tried the other two lines listed in the Tutorial but to no avail. 
Any ideas as to where to go from here would be very much appreciated!

-Loic

UPDATE: OK, have been able to get the keyboard to connect automatically, but the mouse still isn't playing ball. I've triple checked the BT address and it is correct.

---

