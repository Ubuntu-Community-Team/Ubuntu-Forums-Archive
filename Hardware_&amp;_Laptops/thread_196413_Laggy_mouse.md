---
title: "Laggy mouse"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by burgermann on 2006-06-14
Hi. 
Since my shift to Dapper drake (from 5.10) my USB mouse has been lagging bad. I can't use it at all. However my touchpads works flawlessly and so does the keyboad.

So it's only the mouse and it's only Dapper Drake. When I unplug it and replug it, the whole systems decents into a huge 30 second lag and I can't reboot. I need to force the laptop to shut down. Does anyone have a clue how to fix this?

---

### Post by TheSeal on 2006-07-23
I installed Dapper drake today and got the same problem.
I tried the dapper drake flight 06 before and that version worked great.

Anyone know how to solve this problem?

---

### Post by FlyingCheese on 2006-07-24
I, too, have this problem. Also, sometimes it takes forever to do simple things like use checkboxes in the Menu Editor.

---

### Post by TheSeal on 2006-07-24
problem solved.
When i should install the nvidia driver I went to problems again, but this time i had one of my more ubuntuexperienced friends with me. 
He helped me and we googled on the error and found out that I had a IRCconflict between my geForce 6600 Go and the USBdevice.

So by adding "irqpoll" in /boot/grub/meny.lst the problem were solved.

```
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet irqpoll splash
```

I have no ide if this is a good way to solve it, or if we should do it in some other way, but it works :P

---

