---
title: "USB photo camera: problem with multiple users"
date: 2010-12-05
forum: Hardware
---

### Post by KeesM on 2010-12-05
Hi all,

Trying to move away from Windows in a family environment (thus multi-user), and transition is not as smooth as I hoped...

My current problem: when connecting my Canon A710 camera via USB while another user is logged in (but not active), it seems the camera is not (always) recognised. As long as only one user is logged in, things work fine (get file manager window, question to start F-spot, etc) but if another user is logged in before me, many times this does not happen. Don't see anything using 'mount'.

Or, if I plug it in while logged in and working as userA, I get no access, when I next switch to (previously logged in) userB, there it is... As if it connects the camera to a random user.

Is this a known problem, and is there an easy fix so the camera shows up for the user actually at the computer (usable for all family members, so no xterm/sudo/... solutions for actual use; for one-time fixing it is OK)?

Thanks in advance, Kees.

Btw: camera is identified in F-Spot import as "Canon PowerShot A710 IS (PTP mode"); running Ubuntu 10.04 in 64-bit mode on a fairly standard desktop system

---

### Post by KeesM on 2010-12-24
Anyone? Help?

---

### Post by Coolhand_EL on 2011-01-15
I have the same problem running 10.10 x64. All our USB devices behave like this - music players, cameras, flash drives etc. We always leave our accounts logged in and the device more often than not gets mounted by the "wrong" user. Is there a way to define who gets control when USB devices get plugged in?

---

### Post by Fishnuts on 2011-03-11
I have the same problem with every camera I've ever tried. As long as I log out of all other accounts just leaving one active then cameras connect just fine.

I've never had any trouble with usb drives cd/dvd or anything like that. It always mounts to the user that is currently active even if others are logged in.

I'm running 10.10 x64 and I've had the same behaviour as far back as I can remember. 6.06 maybe?

---

