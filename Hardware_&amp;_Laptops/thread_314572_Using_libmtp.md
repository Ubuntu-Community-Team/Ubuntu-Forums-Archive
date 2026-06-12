---
title: "Using libmtp?"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by noamsml on 2006-12-07
Hi,

I have a Sandisk Sansa c240 which uses MTP to transfer media files. Now, using MTP with Linux is a pain, but libmtp should make it possible. When I try using libmtp's CLI tools, however, I get the following message:

```

No MTP devices.
No devices.

```

Under certain conditions, and when I run the tools as root, I will get the following message:

```
Autodetected device with VID=0781 and PID=7450 is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
usb_claim_interface(): Device or resource busy
Connection error.
No devices.

```

I should note that when connected, the player is "mounted", but when I browse the player's FS it doesn't display the music files as it does when I mount it under windows. 

What's the problem? How do I use my Sansa with libmtp?

---

### Post by SZF2001 on 2006-12-10
I think (if you can) you need to go in your player and change the USB settings. I have the e series so I'm not sure if yours is the same... But there should be two options - MTS and MSC (I hope I spelt them right)

---

