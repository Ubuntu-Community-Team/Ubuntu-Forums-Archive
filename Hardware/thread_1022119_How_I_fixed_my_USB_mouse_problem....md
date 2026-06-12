---
title: "How I fixed my USB mouse problem... ?"
date: 2008-12-26
forum: Hardware
---

### Post by mgangav on 2008-12-26
Let me start with saying that I am a newbie to Linux and I've been using Ubuntu only for the last six months.

So, I have a Microsoft wireless usb mouse that I sue with my Acer laptop. I use Intrepid with the current linux kernel. So, my problem was that I some times my mouse would just die on me randomly. Not even restarting my computer would restore the mouse functionality. Then, without my knowledge, it would start working again randomly. Well, I looked for solutions to my problem, all methods that I read about failed.

So, anyway, I was experimenting with modprobe and here is what I did to get an instant response from my mouse:

```
sudo modprobe usbmouse
```

Anyway my question is what does this do? Are there any side effects to this?

---

