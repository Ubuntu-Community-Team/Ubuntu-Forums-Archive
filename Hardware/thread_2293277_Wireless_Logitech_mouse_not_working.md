---
title: "Wireless Logitech mouse not working"
date: 2015-09-03
forum: Hardware
---

### Post by MachFront on 2015-09-03
Installed Lubuntu 14.04.3 on my gal's laptop (since Windows 7 started to get weird and, well, tried a re-install...guess what I didn't know? That the key on the bottom of the computer is only for manufacturers and so Win saw it as a non-legit install. Yep. Great. Thanks.).

Everything's perfect. But, her Logitech M325 wireless mouse won't work. I've changed the battery, restarted, changed usb ports, turned it on and off, rebooted and various combinations. It worked perfectly before on her laptop when Win7 was installed. I plugged it into my Win7 laptop and it works. Plug it back into the Lubuntu laptop and nothing.

On the specs on the Logitech website it lists Linux kernal 2.something or higher so one would assume it should just plain work.
I've searched here and about the web and the majority of the time folks have issues with wireless mice the thread either has no replies or no solutions.

What's my next step?
Thanks. :)

---

### Post by efflandt on 2015-09-04
Probably difficult to find a solution because Logitech devices usually simply work as long as the Unifying receiver is matched up with the mouse or keyboard. So if it works in Windows it should automatically work in Ubuntu. I use an M185 on my tablet PC with Lubuntu or Ubuntu 12.04 (or along with K400 keyboard with same Unifying receiver in Debian Linux on Raspberry Pi), AnywhereMX on my Ubuntu 14.04 laptop, and MXMaster on my desktop.

See if **lsusb** lists the receiver similar to: Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver

---

### Post by wolfie52 on 2015-09-04
Hello, I had exactly the same problem with the same Logitech Mouse. Exasperated with the device just not working I contacted Logitech who promptly sent me a new one and that works perfectly on both Netbook and Desktop. I should add that I was operating 14.04 from a net book but when I switched to a desk top also running 14.04 the mouse just would not function. Completely inexplicable. This is my story and my resolve. I am a total novice, others on this site who have a far greater understanding of Ubuntu might be able to give a a different and quicker solution.

Geoff

---

### Post by MachFront on 2015-09-04
> **efflandt said:**
> See if **lsusb** lists the receiver similar to: Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver

It's not listed at all.
I'd previously noted nothing was shown under "usb devices" in the system profiler.

Lubuntu just isn't even seeing it as existing at all.

---

### Post by MachFront on 2015-09-05
Also, (as we just discovered) her HDMI out doesn't function. She's used to plugging her laptop to the TV to watch Netflix (so, after I had to screw around installing Chrome), we plug the laptop into the TV and...nothing. Tried another cable. Nothing. Tried each input on the TV. Nothing.
Argh.

---

### Post by efflandt on 2015-09-08
Did you try booting with the HDTV connected and on with that HDMI input selected. X looks for displays when it starts and may not automatically recognize hotplugged video devices. If hotplugging the HDMI, try System Settings > Displays > Detect Displays (button). Or if that does not work, try logging out of X and logging back in. Otherwise what works may depend upon graphics chip and drivers (or X Server Settings for the particular proprietary driver).

---

### Post by MachFront on 2015-09-09
I'll try that. Thanks.

Last night I tried running live CDs on her laptop of both Lubuntu and the newest Mint. Neither her mouse or mine worked in the environments. Nor does hers acknowledge a thumb drive when inserted. I ran the discs on my own laptop and both Lubuntu and Mint recognized both mice and my thumb drive.
Linux just, for some reason, will not 'see' anything plugged in to her usb or HDMI. I'm probably going to reinstall...just to see if it 'takes' next time. Urgh.

---

