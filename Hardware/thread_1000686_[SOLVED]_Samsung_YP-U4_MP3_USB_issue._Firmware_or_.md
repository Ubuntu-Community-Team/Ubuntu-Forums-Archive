---
title: "[SOLVED] Samsung YP-U4 MP3 USB issue. Firmware or better driver?"
date: 2008-12-03
forum: Hardware
---

### Post by steevc on 2008-12-03
I thought I was being clever in buying a device that explicitly supports OGG Vorbis, but I've hit a snag.

It uses MTP rather than the better supported UMS protocol.

It does actually appear as a USB Imaging Interface, but I can't seem to copy files to it. There are some text files in the root that say something about it using a PTP2 driver that is a couple of years old.

I've seen mention of libmts, but that doesn't seem to recognise it. Hardy has 0.2.6.1 of that, but they are now on 0.3.4. I'll look at installing that. Anyone tried it?

Alternatively I may be able to get firmware for the player that will support UMS. I think this is only available from Samsung in Asia, but they do not make explicit mention of UMS on the download page. To be able to install it I'll have to take the player to work where I can use Windows and then need to bring it home again to test on Linux. Can anyone confirm what firmware I need to save having to repeat that process?

EDIT: I have a possible solution in the form of gnomad2 that detects the device and lets me transfer files across. Unfortunately the version in the reps doesn't do ogg tags, but the latest one should

EDIT2: Okay, found what looks like the ideal solution. Amarok supports MTP devices. I think I'll be using that. I hope this helps someone.

EDIT3: I've since found out that the U4 has a settings option to make it act as a UMS device, but I'm sticking with MTP and Amarok for now

---

### Post by el_chupacabra on 2008-12-27
Thanks a lot gnomad2 works like a charm. :)

Windows XP recognizes the Samsung U4 as a camera and won't allow copying files to the device. I can delete things, but can't copy/paste anything onto it.

Linux doesn't even recognize it as a USB device, but gnomad2 enabled me to copy MP3 files to it.

---

### Post by steevc on 2009-01-07
In the settings there is an option

System > PC Connection

that lets the U4 act as a USB storage device. I just tested that and it seems to work. I only found that out from this review

[http://www.reghardware.co.uk/2009/01/06/review_mp3_player_samsung_u4_sony_b/](http://www.reghardware.co.uk/2009/01/06/review_mp3_player_samsung_u4_sony_b/)

Steve

---

