---
title: "Disable USB autosuspend entirely for KVM support?"
date: 2012-01-04
forum: Hardware
---

### Post by jlparsons on 2012-01-04
Hi folks,

I've bought a Belkin Switch2 USB/DVI-D/Sound KVM to switch between my laptop and desktop (both 11.10) which seems to work perfectly except for the following... when left for a while the keyboard and mouse stop working completely, ie they're completely powered down, no mouse/caps/numlock lights etc.  No movement/clicks/keystrokes will make them work and nor will restarting the PC, but restarting the KVM will, and immediately.

Some research has lead me to suspect that this is because the kernel disables USB autosuspend for most individual usb devices (as few support this) but enables USB autosuspend for hubs (most of which do support this).  As the KVM has only one USB plug, with the keyboard and mouse each then plugging into the KVM, it seems logical to assume that it is working as a hub.  As both devices are powered down completely in this state it also seems logical to assume that the whole kit and kaboodle has been autosuspended and does not support waking.  Perhaps the machine has sent the "suspend" command to the KVM which powers down and then doesn't respond to any wake-up calls.

So.... how do I disable USB autosuspending for all USB devices, including usb hubs?  Or just this one specifically?  

Also, if anyone has any educated comment on the likelihood of this being the problem, or of any other possible explanation, please do chime in!

---

