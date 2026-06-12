---
title: "Internal keyboard suddenly dead, even when booting from live usb. Hardware issue?"
date: 2018-05-06
forum: Hardware
---

### Post by L Borealis on 2018-05-06
After a suspend my keyboard stopped working, and it hasn't been working since. I'd like to find out if it's a hardware issue. 

Things tried, without success:
-running sudo apt-get install --reinstall xserver-xorg-input-all and then rebooting
-booting from a live USB instead

When I run grep "" /sys/class/input/*/name the keyboard seems to be listed at least, as "AT Translated Set 2 keyboard". Not sure if that helps though.

The laptop hasn't been dropped or damaged, so it seems odd to suddenly get a hardware issue. It's less than a year old. I carried it in my backpack while it was suspended, but it has a SSD so I don't think that should be any issue either?

Any input on what tests to run etc is welcome. Currently using a usb keyboard. Mousepad works fine.

---

### Post by Autodave on 2018-05-06
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by L Borealis on 2018-05-07
Sorry for taking a while to reply. It worked :)

I couldn't easily remove the battery (new laptop, less easy to open up and doing it might void the warranty). This is why it took me a while to reply, and also why I didn't try this as the very first thing. In the end I just let the battery drain completely, and then connected it again. All is working well now. Thanks for your reply! :)

---

### Post by Autodave on 2018-05-07
Glad that it worked!  Remember to mark this thread as closed.

---

