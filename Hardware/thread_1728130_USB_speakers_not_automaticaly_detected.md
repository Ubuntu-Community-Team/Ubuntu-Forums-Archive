---
title: "USB speakers not automaticaly detected"
date: 2011-04-13
forum: Hardware
---

### Post by finnj6 on 2011-04-13
Hi

I've bose usb speakers, they work with ubuntu if they are connected to my laptop when I turn it on but if I plug them in when the machine is already on they arn't picked up.

I tried restarting pulse audio with 
 ```
pulseaudio --kill && pulseaudio --start
```
but it doesn't work.

Also the sound can be a bit scratchy sometimes any ideas why?

Thanks

---

### Post by samacaster on 2011-04-13
Most USB speakers are iffy at best no matter the OS. Win7 on my desktop acts the same way. Even stopping and restarting drivers fails to work, but a reboot solves it. If they work from start up I would roll with that.

---

