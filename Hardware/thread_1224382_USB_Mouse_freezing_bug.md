---
title: "USB Mouse freezing bug"
date: 2009-07-27
forum: Hardware
---

### Post by rapt0rjezuz on 2009-07-27
My USB mouse will freeze up and entirely stop working, usually when I have firefox or multiple applications running.  I've been looking for a solution to this for 4 days now and still havn't found one. All I know is that the USB port seems to be dying.. I don't know if its all the USB ports or just the one my mouse is plugged into because my keyboard is an old 6-pin and I have nothing else plugged into my USB ports.

I would really appreciate any help!

---

### Post by moss718 on 2009-08-01
I also have this problem. I had 9.04 32 bit installed on a P4 intel board with no problems. Now I have an P4 with an Asus board and 9.04 64 bit and my mouse freezes with any remotely high CPU usage (like over 15%), requiring a restart. I thought it was my logitech wireless setup, but my bare-bones Microsoft mouse does the same thing. I've been looking for a solution, I'll let you know what I can find. Good Luck.

---

### Post by Rytron on 2010-06-16
My USB mouse also freezes up. :confused:

I am using a PS2 keyboard. I don't know if that has anything to do with it!

I have also noticed that another USB mouse connected at the time dies. As well as that, USB game controllers don't register (this is rare but it still should not happen).

---

### Post by RS232C on 2010-07-01
This is also happening to me, I can however get my system and state back by cntrl-ALT-Del then alt-tab to the shutdown menu and choose hybernate, which saves the state on HD, and then reboots from it.   Also It gives a error about not being able to read USB (I know duh?) when I choose reboot it becomes visable for a second I am using 10.04, and have a AMD 2400+ I run ubuntu also on my 5000+ X2 and it has no problems at all. I forget what Mobo I have in the one thats having a problem or i'd mention that as well. I ran sudo aptitude purge irqbalance, while the mouse was dead and it ran through whatever it was doing, and didn't solve the problem. ...not sure what the problem is, but I'll try to help as much as possible and tell you I think it has something to do with not reading the USB ports....... :-)

---

### Post by teachop on 2010-07-18
I am running Lucid and something like this happens.  Rarely.  The whole USB hub goes down, keyboard, mouse, hub.  There are no removal messages in dmesg either.  The keyboard on the laptop and trackpad still work at these times.  I just had it happen again, within a few seconds of starting a download in chrome - don't know if that is related.  I purchased a new hub and it did not fix anything.

---

### Post by RS232C on 2010-08-13
I think one of the last two updates solved this problem, for me anyways........I haven't had a lockup in 2 days. can anyone else verify they are ok now? Or anyone know what specifically the last two updates worked with?

---

### Post by Rytron on 2010-08-13
# Remove irqbalance

```
sudo aptitude purge irqbalance
```

---

