---
title: "trouble with mythtv and pvrusb2"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by ppoppe on 2007-10-27
I could use some help with my Hauppauge wintv pvr usb2 setup. I am using the Ubuntu 7.10 distro with all the updates and everything. I followed Isley's walkthrough for loading the firmware (I put them in  /lib/firmware/2.6.22-14-generic/. I am pretty sure my drivers/firmware is setup correctly 'cause I can see one channel if I do "mplayer /dev/video0".
However, when I load the MythTV setup, I cannot add the card as a "PVR-X50." It shows up as an entry for the V4L, but when I try to add it as the PVR-X50, it just says that the device "failed to open." Does anyone have some advice?? Thanks.

---

### Post by pezmanlou on 2008-01-03
I am having the same problem; hopefully someone knows what to do.

---

### Post by martin ö-h on 2008-04-01
I'm had  the exact problem! 

Then I found this:

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2)

Seems like you have to specify MPEG2 Encoder as the card type

If it says Failed to open card, just specify /dev/video0 (if thats where your card is at)

Now I'm having problems with actually decoding the MPEG2 stream encoded by my pvr-usb2.

When I throw mplayer at /dev/video0

it tells me that
[...]
MPEG-PS file format detected.
VIDEO:  MPEG2  480x480  (aspect 2)  25.000 fps  6000.0 kbps (750.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Xv: could not grab port 355
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 480 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
[...]

do I need to install some codecs?

I hope someone can help me on this one.

Best regards

Martin.

---

