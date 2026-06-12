---
title: "Logitech M185 Wireless Mouse - Suspend Woes"
date: 2020-11-18
forum: Hardware
---

### Post by speartip on 2020-11-18
Running a fully updated 20.04. Just purchased a Logitech M185 Wireless Mouse. Plug & Play works perfectly except if I suspend the computer. Ironically I can use the Mouse to wake the computer from suspend, but the Cursor just remains frozen in the middle of the screen. Any ideas?

---

### Post by tea for one on 2020-11-18
Suspend to Ram or Suspend to Disk?

Change battery in Mouse?
Change USB port for receiver?

I've used a Logitech M185 for 4/5 years and it has never given a problem..........

---

### Post by speartip on 2020-11-18
Hi tea for one.
There is only 1 suspend on my system, so I'm assuming it's suspend to ram??
This is a brand new mouse with new battery. I've tried other ports, same result. 
Works as it should on Windoze 10.
It works fine in every other way. Even taking the receiver out & putting it back in again, brings it to life. Reboot & shut down fine. Just waking from suspend is the issue.

---

### Post by tea for one on 2020-11-18
Sometimes, when waking up the PC, I have to wiggle the mouse and hit the enter key a few times, but this seems a bit unscientific.

Regrettably, I have no more useful suggestions.

---

### Post by speartip on 2020-11-19
Thanks Anyway.
Just a bit more info.
I tried on a Live MX19.3 distro, the result was the same.
What's strange is that the Wireless Mouse wakes the computer from Suspend, so there is a connection there, but then it just freezes. My wired mouse however doesn't have the ability to wake from suspend, only the keyboard does. Whether these things are related I don't know.

---

### Post by oneleded on 2020-11-19
Defective comes to mind, i dont know nothing though. i'm still using a Logitech wireless mouse from 2002, not made for linux. 
i bought a M720, havent even tried it out yet. the 2002 is still kicking. till it quits, i see no reason to change.
[on the side, i dont have windows].

---

### Post by tea for one on 2020-11-19
@speartip

When I mentioned [COLOR="#0000FF"]Suspend to Ram[/COLOR] and [COLOR="#0000FF"]Suspend to Disk[/COLOR], I was playing around with pclinuxos because I noticed your details mentioned Kubuntu Development Release.

Pclinuxos has a KDE flavour but I'm not completely familiar with KDE so my previous comment may well be misleading?

MX19 is a popular distro and there may be something in their forum pages to help.

Logitech is also a member of LVFS [https://fwupd.org/lvfs/search?value=logitech](https://fwupd.org/lvfs/search?value=logitech) - might be useful, might not..........

Cheers

---

### Post by speartip on 2020-11-20
@oneleded - Don't think it's defective, as works perfectly on Windows after suspend.
@tea for one. I'm a distro hopper, My listed Distro isn't always what I'm on. however, I've tried this on Kubuntu, Ubuntu, Linux Mint, & MX19.3, with the same result. I can only conclude that it must be hardware specific to my computer. I'll search on though.

---

### Post by tea for one on 2020-11-20
> **speartip said:**
>  I can only conclude that it must be hardware specific to my computer. I'll search on though.

Yes, you could be right - Is there anything unusual about your PC that leads you to this possibility?

Now, just to pour more oil on troubled waters ;), I'll mention that Logitech Unifying Receivers are not all identical:-

[COLOR="#0000FF"]Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver[/COLOR] - This is the receiver supplied with M185 Mouse (without keyboard) - approx 5 years old

[COLOR="#4B0082"]Bus 001 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver[/COLOR] - This is the receiver supplied with M185 mouse & K270 keyboard combination kit - approx 18 months old

The receivers and mice are not interchangeable, each mouse only functions with the receiver supplied in the pack.

You can find the ID via the terminal with **lsusb**.

I know it's not much help...........but possibly food for thought.

Good luck with your search

---

### Post by speartip on 2020-11-21
lsusb shows:
```
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 009: ID 3151:1002  
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
The Wireless mouse is the 2nd one in the list, that doesn't give a description. The 5th one is my wired HP Mouse.
Don't know if this helps or not.

---

### Post by tea for one on 2020-11-21
The text description **Logitech Inc Unifying Receiver** is missing - perhaps a clue?

Faulty receiver rather than mouse?

If you unplug the receiver, attach it again and run [COLOR="#0000FF"]dmesg[/COLOR] via the terminal, you can collect some more info.

Whether, it yields anything concrete, possibly? 

I'm not savvy enough to decipher all the messages.

---

### Post by speartip on 2020-11-21
> **tea for one said:**
> The text description **Logitech Inc Unifying Receiver** is missing - perhaps a clue?
My thinking as well. However remember that it works flawlessly in windows, so the receiver can't be faulty.

Here's a real bizarre thing, don't know if this is relevant or not, if i run in a terminal after I've resumed from Suspend:
```
[FONT=monospace][COLOR=#000000]sudo modprobe -r usbhid[/COLOR][/FONT]
```
This disables all my USB connections. However if I then plug in my wired Mouse, my wireless Mouse begins working again.
Go figure.

---

