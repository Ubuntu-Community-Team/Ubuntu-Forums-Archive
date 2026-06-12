---
title: "Microsoft Bluetooth Wireless Keyboard 6000 and Ubuntu 9.10"
date: 2010-06-11
forum: Hardware
---

### Post by nadude on 2010-06-11
I'm completely new to linux and ubuntu, just installed it on a new laptop, and have no clue what is going on. 

Tried to install my microsoft bluetooth wireless 6000 keyboard and haven't been successful. It gets discovered, and when the passcode appears on the laptop, no input is taken from the keyboard whatsoever. After a while, ubuntu says its been successfully added, but it doesn't work at all... 

Anybody have any suggestions? Ideas? 

Let me know what other info you may require? 

Thanks!!!

---

### Post by luopio on 2010-06-28
I'm typing with the same keyboard right now. I got it setup with the "set up new device" -routine via the bluetooth icon. Didn't have any problems, except that the keyboard drops the connection every now and then (~ every 5 min), which is quite frustrating.

Dmesg tells me:
> [ 2939.049753] btusb_intr_complete: hci0 urb ffff88003e8716c0 failed to resubmit (19)
[ 2939.049803] btusb_bulk_complete: hci0 urb ffff88003e871180 failed to resubmit (19)
[ 2939.049811] btusb_bulk_complete: hci0 urb ffff88003e871e40 failed to resubmit (19)
[ 2939.050309] btusb_send_frame: hci0 urb ffff88008df00000 submission failed

then the keyboard drops out and once i hack a few keys it reconnects. Thinking of submitting a bug report. My bluetooth mouse also drops out, but everything works ok if I don't use the keyboard..

Anyhow long story short: "should work out of the box". I'm using 10.04 64 bit.

---

### Post by nadude on 2010-06-28
hey, thanks for the reply. I was using a really cheap external bluetooth adapter, which is probably causing the problem, as I connected out of the box with an older ubuntu computer with a built in bluetooth adapter too. Not sure what kind of bluetooth usb dongle I need. 

I use the keyboard on windows too, and it works excellently, but also sleeps after a while, and need to hit buttons repeatedly for it to come back. i think its just a built in standby feature in the keyboard from microsoft... unfortunately they've provided us with no documentation whatsoever describing battery use, life and best use...

---

