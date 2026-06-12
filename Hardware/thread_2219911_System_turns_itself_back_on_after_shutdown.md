---
title: "System turns itself back on after shutdown"
date: 2014-04-25
forum: Hardware
---

### Post by paulisdead on 2014-04-25
I've actually got 2 systems exhibiting this behavior.  About 80% of the time or so, when I shut the systems down from the shutdown menu, they shutdown, but several seconds later turn themselves back on.  It's not like a reboot, either, where the system still has power the whole time.  They actually are off for a few seconds.  I've checked the firmware settings, and they're all set to stay off after power loss.  Both are haswell based systems.  One is a Clevo W740SU from linuxcertified.com.  The other is an Intel NUC D54250WYK.  I was looking into installing firmware updates on the laptop to see if that helps, but it requires a pure dos environment (what is this, the middle ages?!), when I got the new NUC and noticed it's having the same problems, which makes me think it's not the firmware.  Both of these systems should be about as Linux compatible as you can get with a full Intel stack in them.  The laptop did this under 13.10 and was upgraded to 14.04 and still does it.  The NUC has never had anything but 14.04 on it.  These are all running Ubuntu Gnome, if it makes any difference.

---

### Post by Jonor on 2014-04-26
How about a Wake On bug between the BIOS and Ubuntu Gnome ?
Mine is a bit buggy but not so much as to bother upgrading it.
No matter what the Wake On settings are, it will occasionally wake on mouse movement
and even if Wake On Mouse is selected, it does not always work.
Perhaps there is a bug such that Wake on LAN or Mouse is being intermittently triggered ?
Try testing with the router switched off to stop LAN activity.

---

### Post by paulisdead on 2014-04-26
I did think it could be waking from touchpad movement on the laptop, and have been careful not to touch it while shutting down, but that doesn't seem to affect it.  Also, the laptop's rarely plugged into ethernet, I'm generally on wifi, so it shouldn't be getting any wake signal.  I'll try shutting down a few times on the NUC with the ethernet unplugged to see if that has any impact.  I'll double check that nothing for waking from mouse/keyboard/ethernet is enabled in the firmware on that system too.

I did finally manage to get the firmware on the laptop updated.  I used unetbootin to install freedos to a thumbdrive.  Had some trouble with that until I remembered to disable UEFI boot on it.  Unfortunately it's still starting up again sometimes after shutdown.

---

### Post by funked up on 2014-04-26
Don't know if that's the case with you but once I think I had the same problem with you.
 I realized that somebody else had used my computer as a "visitor" without logging in.
So I had to "swich user" and shut it down again.

---

### Post by Jonor on 2014-04-26
I don't use wifi to a Ubuntu box but definitely try with it off or unplugged as i would imagine 
it is still considered as LAN so any wifi device that can connect with the password might wake it.

---

### Post by paulisdead on 2014-04-29
Sorry, took me a little while to circle back to this.

I am definitely the only person that's logged in to these systems.

I still haven't gotten to do more testing on the NUC, but on the laptop, it still turns on again a few seconds after a shutdown, even when I disable the wifi.  I don't have a hardware switch on this laptop, so all I can do is select wifi off from menu, so I'm not sure if it's physically fully turned off.  I have managed to isolate it to when I have the power plugged into the laptop, though.  If it's unplugged it's fine.  The laptop's firmware is pretty limiting, so I don't really have any power options I can mess with there.  When I get a chance I'll poke through the firmware in the NUC and see if there's any WOL stuff and see if it still does it with it's network unplugged.

I did manage to get the firmware updated on the laptop, and that didn't help either.  I had forgotten I was using UEFI boot, and needed to turn that off to get freedos to boot from a thumb drive.

---

### Post by fkkroundabout on 2014-05-01
so i suppose it didn't do this, before 13.10 with windows ??

personally i wouldn't fuss over it, and would just press the power button as it's turning on again, to turn it off properly. admittedly more of a practical than a technical solution, but for that reason i'd say: simpler

---

### Post by paulisdead on 2014-05-01
The laptop did it with 13.10.  Windows never has, and never will touch touch these systems, so I can't say if they do it there.  The NUC has only had 14.04 on it.

I really do not consider shutting off the computer from the couch with a wireless keyboard, then going across the room to mash the power button to shut it down again, a solution, since this is not the way it's supposed to work.

---

### Post by fkkroundabout on 2014-05-01
remote controlled power supply ?

---

### Post by paulisdead on 2014-05-15
So this is still going on.  With no network the NUC still turns itself back on.  Most of the time if the laptop's AC power is plugged in, it turns back on, as well.  At least when not on AC power it doesn't happen on the laptop.

I'm also not buying a PDU and setting up another box to run scripts to cut/restore power to the outlets.

---

