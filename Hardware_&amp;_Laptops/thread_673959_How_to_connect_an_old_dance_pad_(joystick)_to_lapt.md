---
title: "How to connect an old dance pad (joystick) to laptop?"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by dt.in.th on 2008-01-21
I have an old dance pad which is still working. It is so old so it uses LPT port.

I got it working on Window$ by using a program called PPjoy, but I did it on a PC, not on laptop. StepMania worked very well on Linux, but not on Window$.

My laptop, which is running Ubuntu 7.10, does not have LPT port, but it has USB ports (of course) and I have an adapter for LPT ports. Say, I can connect my pad to that thing and at another end is USB.

After connecting it to my laptop here is what dmesg gives me:

```
[ 3561.876000] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 3562.028000] usb 3-2: configuration #1 chosen from 1 choice
[ 3562.068000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x4348 pid 0x5584
```

I want to connect a joystick, not a printer. And GNOME says that it has detected a printer. I found 2 files on /dev:

/dev/usblp0
/dev/usb/lp0

I tried this:

```
sudo xxd /dev/usblp0
```

and press something on the pad, but it doesn't give any response.

Are there any way of making this work? I tried searching but have no luck.

---

