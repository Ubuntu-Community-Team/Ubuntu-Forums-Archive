---
title: "Hotplug / USB inconsistencies"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by cheuschober on 2006-04-20
Hiya. I posted on this a little while ago and let it gestate for a month or so but no one bit so I thought I'd try again...

I'm having device / driver failures using any non-thumbdrive usb devices with my system (toshiba A45-S130 laptop) after boot. Yes, there are quite a few qualifiers in there.

A usb thumbdrive works after being plugged in, sometimes it takes longer than usual (a few minutes) with a dmesg error about a i/o flag, but eventually it works itself out and mounts.

If I take any usb device (printer, camera, ipod, keyboard, mouse, webcam, etc) and plug it in before boot the devices are recognized by hotplug subsys during boot the drivers are loaded and everything works as expected without a hitch.

But!!! If the system has already started and I attempt to plug any non-thumbdrive device in I get the following:

```
[4728868.949000] hub 1-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
```

Does anyone have any thoughts on this at all? I'm getting somewhat desperate -- I'd like to use my mp3 player before it's totally obselete. :-p

Even if you don't have a solution maybe you might have questions I haven't thought of asking? 

Many thanks!
~Chad

---

### Post by cheuschober on 2006-04-22
*bounce*

Anyone have any thoughts at all? I know it's not just problems with the module or usb ports because it recognizes and configures these devices during startup. So can anyone explain what hotplug (or other services that maybe are interfering) is doing different during startup that it doesn't do once a user session has begun???

Again, any and all help -- even questions without answers -- is welcome. I've been struggling for well nigh over a month for this and it's basically ruining my user experience at this point and I know we (ubuntu, my laptop, and I) can do better. :)

Best regards,
~Chad

---

### Post by cheuschober on 2006-05-01
Okay, so it seems no one has anything to contribute to this particular kind of error so maybe it's better I ask a different question:

Is there a way to restart the whole USB / Hotplug subsystem from terminal without killing my session? It's a pain in the arse but maybe I could just write a script to restart everything and tie it into every hotplug event dealing with the plugging in and unplugging of any usb devices.

Best,
~Chad

---

### Post by duality on 2006-05-03
sorry i do not know any solution to your problem, but you can ask on irc if anyone knows anything about this

server:  irc.freenode.net
#ubuntu
#kubuntu

---

### Post by cheuschober on 2006-05-03
Thanks for the reply duality. :-D 

Unfortunately the IRC channels are somewhat dead to this problem as well. ](*,)

Best,
~Chad

---

