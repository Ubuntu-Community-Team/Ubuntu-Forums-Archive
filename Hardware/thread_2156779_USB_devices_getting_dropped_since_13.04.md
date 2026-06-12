---
title: "USB devices getting dropped since 13.04"
date: 2013-06-23
forum: Hardware
---

### Post by WSabey on 2013-06-23
Hi, I'm having a problem with my USB devices, mostly (but not only) my mouse. It'll work fine for a while after booting (highly variable, from under a minute to multiple hours, possibly days) but it will suddenly lose communication with the computer entirely. It will stop moving, the computer won't receive a key-up for the mouse buttons if I happen to have one down at the time. I've searched the web, but all I can find is people who have their mouse hanging temporarily, while mine doesn't recover until I reboot. I say *mostly* the mouse, because a couple of times I've had the same issue with the keyboard, where it will suddenly stop accepting input, hanging mid-keystroke. One other strange thing is that when the mouse goes down, the indicator lights on it remain on, but if I unplug it and plug it back in they don't light up again. Also, if I unplug the keyboard and plug it in again after the mouse has frozen, it stops working too. I've checked the system and kernel logs when the problem occurs (at least that's what I presume I'm looking at at /var/log/kern.log and /var/log/syslog) but there's no entries around the time it happens at all.

[LIST]
[*]USB devices lose touch with computer while being used 
[*]Doesn't seem to happen when idle; I can leave the computer for hours and it's never frozen when I return 
[*]It's always the device that I'm using; the mouse never goes down while I'm typing or vice-versa 
[*]No entries at all in system or kernel logs at time of failure 
[*]After failure, new USB devices not connecting 
[*]New in 13.04 + not affecting windows dual-boot; not a hardware issue 
[/LIST]
If anyone knows what this could be, I would really appreciate any help they can provide. I'm tempted to back up and revert to 12.04, but I thought I'd check if anyone knows what it is or any other log files I could be checking first.

---

### Post by dino99 on 2013-06-23
if its a logitech one, then its the worst choice as that brand badly support linux (in fact no support by now mainly)
otherwise it can be a glib2/gtk3 issue in case you have installed some packages from ppa(s) (the bleeding edge ones)

most of the time unplugging/plugging it resolve the problem (till the next time)

---

### Post by WSabey on 2013-06-23
Yeah, it's a Logitech G500 (I knew I'd forgotten *something* when I  posted this), but it's always worked perfectly for me up until 13.04.
Unplugging/plugging doesn't do anything except turn off the DPI indicator lights, it doesn't reconnect afterwards.

---

