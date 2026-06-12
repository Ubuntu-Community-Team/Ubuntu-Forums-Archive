---
title: "USB keybord does not work"
date: 2021-02-26
forum: Hardware
---

### Post by BigYellowDog on 2021-02-26
Running server 20.04 LTS, I can not get any USB devices to work.  First my keyboard does not work and I can not see a USB flash drive.

The keyboard is good, tested it on another system.  I can get to the systems BIOS with the same keyboard, and I can boot into another distro with a USB drive and the keyboard works.

I plug in a USB drive an tail dmesg, and don't see anything related to the USB drive.


I see the USB ports

```
[robf@ubuntu] ~ $ lspci |grep USB
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
```

---

### Post by Autodave on 2021-02-27
Since no one else has any ideas, let me offer one.  How many drives is this server running when booted?  Is it possible that once the drives are operational that the 5V line is being pulled too low for the wireless board to operate?  Are you using any USB hubs on the server?

---

### Post by BigYellowDog on 2021-02-28
The computer in question is a Dell micro PC.  It's an older model so the power supply in integrated rather than an external laptop type power supply.

No peripherals, just a single 2.5 HDD.  Nothing wireless the keyboard is a wired keyboard.  USB ports are integrated on the mother board.

Keyboard stopped working before I cloned the HDD.  To do this I booted a flash drive and cloned to an external USB HDD.

After the cloning process, the keyboard still did not work.  Since the USB ports worked for the cloning problem, I was not sure if this was a software or a soon to be hardware problem.

I placed an different HDD in, and was going to try to do a new install of Ubuntu as a test.  The installation failed at 

```

[ OK ] Finished Hold until boot process finishes up.
[ OK ] Finished Terminate Plymouth Boot Screen
[ 184.050982] snd_hda_intel 0000:00:0f.0: CORB reset timeout#1, CORBRP = 0

```

Since it just sat there for more than 5 minutes, I assumed I have a HW failure.  I assume a failing power supply or mother board.  Maybe someone can explain the error message.

I moved the HDD to my backup desktop, just changed the network device cause I have a static IP address.  Should be good enough.

---

### Post by Bashing-om on 2021-02-28
BigYellowDog;

A thought -
Might change your USB options in your bios. In my use case I must run "legacy". However your case may differ but can not hurt to see what changing the bios setting will do.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by CelticWarrior on 2021-03-01
The "legacy" mentioned above means "legacy USB support", not Legacy/CSM mode. You want to former enabled and very likely the latter disabled.

---

### Post by BigYellowDog on 2021-03-01
No legacy options in the BIOS.

I've been running server for more that 3 years and the only HW changes have been the HDD.

Tried installing a different ISO.  I was successful installing a desktop, 20.04.  USB Keyboard & USB mouse work.  I did get that same message above, but the installer just kept going.

It's disconnected from network.  Going to wait a day or so before running upgrade.

I gotta wonder was there a update in the past few months, don't remember when I sat at the console, that could have effect the workings of my USB ports?

---

