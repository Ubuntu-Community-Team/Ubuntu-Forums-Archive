---
title: "Harmony Ultimate Connecting as PS3 BD Remote [bluetooth][hid]"
date: 2014-04-11
forum: Hardware
---

### Post by Metheos on 2014-04-11
I am trying to connect my new Logitech Harmony Ultimate as an input device via bluetooth. 
I have it paired with a patched bluez.
I verified I have data being sent when I press buttons using hcidump.

It appears that an input device is not created correctly. I've done some digging and it looks like the kernel doesn't have the hid for the harmony ultimate in its hid-ids.h and hid-core.c files.
Looks like it should have the mapping set up in hid-sony.c as well?

I want to make sure I'm not way off base here, and also want to learn what I need to do to add support to my system for this remote.

Also, if this is the right track, how do we get these added to the kernel for everyone?

Thanks!

Edit: The HID reported by hcidump is ```
Input device ID: bus 0x5 vendor 0x46d product 0xc129 version 0x0
```

---

### Post by fearless-spiff on 2014-05-19
I'm trying the same... Any luck? I tried following without success: [http://alabor.me/articles/use-a-logitech-harmony-hub-with-ubuntu-and-plex-home-theater/](http://alabor.me/articles/use-a-logitech-harmony-hub-with-ubuntu-and-plex-home-theater/)

---

