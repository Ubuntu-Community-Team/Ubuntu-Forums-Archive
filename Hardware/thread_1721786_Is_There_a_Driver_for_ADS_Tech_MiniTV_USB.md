---
title: "Is There a Driver for ADS Tech MiniTV USB?"
date: 2011-04-05
forum: Hardware
---

### Post by Steve Redmond on 2011-04-05
I am using Ubuntu 10.10 on a desktop. I am trying to get my USB TV tuner to work with Ubuntu.  I don't think I have a suitable driver, and after searching around google, linuxTV.org and the like, I am not sure there is a driver for linux.

If anyone can clarify the availability of a driver and player(s) for this device with Ubuntu, I will appreciate the help.

In summary:

The device is an ADS Technologies MiniTV USB PTV-371.  It is an analogue TV tuner.  It comes with Windows XP, VISTA and Win7 drivers, and an application called MediaTV.  It works fine on my Win VISTA 64-bit and WinXP 32-bit machines, to receive broadcast (over the air) NTSC TV signals.  

I have a complete lsusb listing.  The device is recognized by Ubuntu, and some of the highlights are as follows:
  idVendor           0x06e1 ADS Technologies, Inc.
  idProduct          0xa371 
  iManufacturer          16 ADS
  iProduct               32 Mini TV USB
  iSerial                64 2.0

I have cracked the case to peek at the chips used.  These include a Trident TM5600 and Xceive XC202...  I have hi-res pictures of the chips and board, with good detail of the full labeling, if they will help.  

There was not much to suggest an existing driver in my searches, although there was  related TM5600/TM6000/TM6010 DVB-T driver development ongoing on someone's ToDo list.

I have tried to use the tuner, e.g., GNOME MPlayer, but got no useful results.  I also tried TVtime Television Viewer, with no useful results.  I presume these  applications aren't working due to the lack of a proper driver for the tuner device.

What's next?  Where can I turn for assistance with this?  If there is no driver now, is there any active development?

Any leads will be appreciated.  Thanks for your consideration.  Steve

---

### Post by Marcelush on 2011-04-05
For linux i don't have a driver , but if you change your operating sistem i can help you! I've searched the net like crazy for such a driver and after 3 weeks i got one. It's really hard.

---

