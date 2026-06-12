---
title: "USB Conflict between two Logitech devices"
date: 2013-09-29
forum: Hardware
---

### Post by goatboy73 on 2013-09-29
Hi, all!  This is probably not an Ubuntu-specific issue, but I'm having trouble finding the right avenue for getting this resolved so I figured I'd post it here first, and hopefully more knowledgeable parties can point me in the right direction.

I have two USB devices which, under certain circumstances, generate conflicts between them. One is a Logitech G700 Gaming mouse, and the other is a Logitech G930 wireless headset. The headset has the particularity that it has an integrated volume control, as well as other buttons that trigger specific acitons (i.e. play, pause, next, mute mic). For reference, I have a second wireless headset from a different vendor that also has an integrated volume control.

The gaming mouse has one particularity in that it can be used in either wired or wireless mode. It is this latter mode that the problems arise in.  Please note that I'm not referring to *RADIO* interference (although this also appears to be an issue).  This is what happens:

1) Positive (i.e. working) Case: G930 is plugged in and sound is working properly, G700 is working in "wired" mode, everyone is happy in Ubuntu-land and everything works as expected.

2) Negative (i.e. failing) Case: G930 is plugged in and sound is working properly, G700 is working in "wireless" mode. This causes several things to happen: if the G930 was plugged in AFTER the G700, then the HID events from both devices appear to get mixed up "somewhere" because clicks will no longer be processed normally.  The pointer still moves normally, though. If the G700 is plugged in AFTER the G930, then everything works "fine for a while", until (and here's where Radio interference kicks in) the G930 is forced to re-set its connection.  At that moment, the device appears to behave as if it had been unplugged-and-replugged, so we're back to things being broken. Evidence indicates that this behavior is not related to radio interference (except s noted), since I have a different wireless headset that also "radio-interferes" with the mouse, but with which there are no HID event mixups (i.e. mouse works fine, and the only hiccup is the occasional disconnect of either device, which self-resolves).

From my limited perspective, this appears to be an issue where some HID events are getting mixed up between two devices. Otherwise, there's no real reason for the mouse clicks to not be detected properly, whilst the mouse movements are flawless.

I'm reluctant to flood this thread with information, but I'm definitely willing to provide as much debugging info as I can (i.e. lsusb -v, etc.), as and if needed.

Help will be appreciated!

---

