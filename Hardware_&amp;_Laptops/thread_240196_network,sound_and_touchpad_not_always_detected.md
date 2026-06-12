---
title: "network,sound and touchpad not always detected"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by david on 2006-08-20
Hi,

my Sony Vaio (VGN-FS395VP) started to behave strangely after updating from Breezy to Dapper. Sometimes the network card/touchpad/sound card (or all of them) is not detected. dmesg, syslog looks fine. Usually a reboot fixes it, but not always. I've gotten the touchpad working by 'modprobe psmouse', so the hardware seems to be working, just not the right modules loaded. 

Has anyone had a similar problem? Any ideas where to start looking for the problem? 

I'm quite lost...:confused:

---

### Post by mkquist on 2006-08-21
I have a similar problem w/my desktop.  Works sometimes, somtimes not after a reboot.  Example, went to bed everything working fine.  Restart, no sound, no network.  Restart in recovery, works. later switched to windows then back, no sound, no network, this time recovery didn't fix.  Typing this in windows. :-k

---

### Post by adMOMistrator on 2006-08-21
My Thinkpad T20 is doing the same sort of thing.  Sometimes it boots just fine, sometimes it looks like it does-but doesn't (network won't work), sometimes it hangs trying to load the desktop.  I'm not having that problem with my desktop.  It goes through the bios differently at different times too-but it did that with XP Pro.

---

### Post by david on 2006-08-21
Have any had the same problem in windows? I usually boot into windows once every other month so can't really say.

---

### Post by david on 2006-08-23
OK. I've been booting to windows every other time and it seems fine. Ubuntu is worse, can't start X. It reports "no devices found". I haven't updated or changed a thing. Rebooted more than 20 times and it still doesn't work :( 
Another strange thing is that 'lsmod | wc -l' gives me anything between 56 to 95 modules between reboots. lspci is the same though. 
Could it be a problem with discover? It started after a upgrade from breezy to dapper, which as I understand changed from hotplug to discover. I'm going to try some livecd's, see if they work. Don't wan't to change distro, but I need to get the laptop working, windows ain't an option.

---

### Post by david on 2006-08-23
Sorry, It seems I cried wolf. I must have made an update (though I can't recall doing it) and gotten the faulty xserver-xorg-core package. 

The original problem still stands and I shouldn't get different modules loaded on each boot, should I? I sucessfully booted a breezy livecd a couple of times, so it's a dapper problem.

---

