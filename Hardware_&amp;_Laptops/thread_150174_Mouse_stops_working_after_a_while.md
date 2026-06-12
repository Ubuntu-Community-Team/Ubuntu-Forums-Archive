---
title: "Mouse stops working after a while"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by [Nirvana] on 2006-03-25
So here I'd be, having fun in Kubuntu, maybe compiling a package for personal/a friends use, maybe sufing KubuntuForums.net... maybe checking email... and I'd be using the mouse... and then, it suddenly cuts out. It is a LED/laser (optical is the word?) mouse, going in thru a USB port. The mouse doesn't get disconnected (it lights up when plugged in, and when it stops working, it still glows), it just stops working... I'd like to check in /var/logs, but I don't know the command to grep (I know it's like cat /path/to/log | grep xxx, but I don't know what to grep for) very well, nor do I know what to look for. I thought it was the double clock speed problem, so I tried those 7 things out, and my laptop wouldn't boot with any of them, except noapic acpi=off, but that didn't fix the problem. Maybe I need a driver? (I don't for Windows, I just plug it in my classroom computer, and it works... yes, we actually have to bring our own mouse in business class).

Anyone know what I can do.

Also, when I shutdown via the K Menu > log Out > shut down option, it hangs, but only when the mouse stops working. If I were to freshly start Kubuntu, and then shutdown, it would work. But if I start Kubuntu > use the mouse until it stops responding > try to shutdown, it hangs, and I have to press my power button to shut it down (not hold, just press, and it goes into shutdown mode, but I can't see the verbose output, all I see is a black screen with an unfunctional mouse.)

I can't restart the X server, because if I press ctrl alt backspace, I get a black screen with an unfunctional mouse. I'll take a mini-movie to show what I'm talking about, since I have nothing better to do today.

Also, if there is a fix for this in Dapper, please do tell, because I've been wanting to upgrade to Dapper anyways.

---

### Post by [Nirvana] on 2006-03-25
Anyone?

---

### Post by [Nirvana] on 2006-03-31
*resurrection*

---

### Post by Corn on 2006-04-04
Im working on dapper and i have the same problem... and no one want to help me too :/ i have toshiba laptop, and you?

---

### Post by cuban on 2006-04-05
I also have this problem on dapper flight 5 after an update.

Mouse is present in the device maanager and at the boot the optical is active but no movement. If i unplug and replug i dont even get a optical light although the mouse still is detected correctly in device manager.

Due to it being a laptop and also containing a trackpad i tried disabling the trackpad but that has no effect, may also be worth noting that the trackpad isn't very sensetive even with the mouse settings to max for sensetivity and acceleration.


System:
Toshiba A40
Mouse : Microsoft Optical Notebook mouse (But have tried others)


Could really do with this being looked into as i'lll have to stall my plans to migrate from windows. Im gonna give flight 6 a try and see how that goes.

---

### Post by cuban on 2006-04-05
Ok i have a solution.

Dont ask me why this works i was just playing aroudn but my god im happy :D

If you have a toshiba like me try these settings in the bios, if you dont have a toshiba but have a similar problem try similar settings in your bios:-

> Find the setting that says "Device Config", On my A40 this is on the second out of 2 pages under the "Configuration" section. The value is probably "All Devices", change it to "Setup By OS"

This also fixes the sensitivity of the trackpad.

Have fun!

---

### Post by cuban on 2006-04-07
Well whatever that did its now not working again, althought the trackpad's sensitivity is better. And i have no idea whats changed cause its basically been on since i posted that last post, i did reboot a few times to check it though, may be another update has changed it

---

### Post by [Nirvana] on 2006-04-14
I'll try your fix Cuban. I do have a Toshiba Satellite M70 SR2 ( I think )

---

### Post by [Nirvana] on 2006-04-22
nope, although, it seems to be lasting longer. I'm gonna upgrade to Dapper tonight, so we'll see if it's fixed. The exact error is this I believe:
```
[4298743.409000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
```

---

### Post by el_escorpion on 2006-09-02
I have same problem, and actualy same comp as Norvana, and while looking through the forum i realised one thing. the one thing in common with people who have this problem with the mouse is this
ATI Xpress 200 video card and only with fglrx.
If you use ati drivers everything works. So as one one said in another thread for now, you can either play games, or have a 100% working mouse. So far no permament solution has been found.

---

