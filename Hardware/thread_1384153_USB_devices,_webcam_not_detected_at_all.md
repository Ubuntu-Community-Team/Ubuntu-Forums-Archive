---
title: "USB devices, webcam not detected at all"
date: 2010-01-18
forum: Hardware
---

### Post by OKKARE on 2010-01-18
Using 

```
tail -f /var/logs/messages
```

and plugging in usb drives, pressing webcam toggle key combo shows nothing, except,

```

Jan 18 00:40:56 noah-wind kernel: [  487.253579] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Jan 18 00:40:56 noah-wind kernel: [  487.253599] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
```

which I think is unrelated.

I'm using an MSI Wind and this problem has been intermittent, but I've been restarting repeatedly and can't get the devices working again. The most recent thing I did was installed telepathy-core, added telepathy to my software sources and upgraded. I've since removed the former but I'm not sure how to undo the rest. I'm not sure if it's related cause I had this problem earlier. Tried selecting another kernel at grub, but no difference.

---

### Post by OKKARE on 2010-01-19
I've discovered that USB drives will work, but after I hit the key to power up my webcam, USB devies will cease to be recognized, and neither will the camera work. I've reinstalled Ubuntu and the problem persists. But it did work fine when I first installed  last time.

---

