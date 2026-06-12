---
title: "Delay on Logitech MX Master 2 bluetooth"
date: 2019-11-03
forum: Hardware
---

### Post by amiga3000 on 2019-11-03
Hello
My bluetooth mouse has an annoying lag, every time I start the system. By that I mean I move the mouse and it takes a moment for the device to wake up and start moving. It's clear that it is being put to sleep, if not used for a few seconds.

I've partially fixed this by add "USB_BLACKLIST="[USB ADAPTER ID]" to /etc/default/tlp. However, I have to take out the USB adapter and reinsert it, before this kicks in. After that, it's fine until the next boot up.

I've also tried USB_AUTOSUSPEND=0 but this didn't work. It also broke my above fix.
Also tried USB_BLACKLIST_BTUSB=1 and this didn't work either.

I dual boot with Windows 10 and that has no such issue.

Is there a command I can run, on desktop launch, that will simulate taking out the adapter and reinserting? Or a config I can add that will solve this issue?

I'm running 18.04 LTS with 5.1.16-050116-generic kernel.

TIA.

---

