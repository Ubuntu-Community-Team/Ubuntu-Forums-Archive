---
title: "Headless installation?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by acranox on 2009-07-09
Hi all,
I'm building myself a little NAS box.  I don't have a monitor, and at the moment, a keyboard neither.
If I used the desktop live CD the thing boots up and gets a IP address from my router, but openssh isn't running, so I can't access the box.  The server CD doesn't seem to boot automatically.
Does anyone have any ideas how I can get this thing to boot in a way that will allow any level of remote access to it?  I've got a USB stick, maybe I could make an image on that.  I'm not 100% that the motherboard supports USB booting though.
Maybe my best bet it to use another distro's live CD which includes ssh access, and then do the ubuntu install from there?

--Peter

---

### Post by earthpigg on 2009-07-09
willing to try BSD instead of Linux?

FreeNAS is designed for exactly this...


...i'm not sure about ssh being enabled by default, though.

[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by acranox on 2009-07-10
> **earthpigg said:**
> willing to try BSD instead of Linux?

FreeNAS is designed for exactly this...


...i'm not sure about ssh being enabled by default, though.

[http://www.freenas.org/](http://www.freenas.org/)


Well, that kind of side-steps the question, but it does look like an interesting distro.  ZFS support caught my eye.
I oversimplified when I said I was building a NAS box.  That's just going to be it's main role.  I also want it to be a router, print server, possible media center, and it needs to support modern hardware (nVidia ION + Intel Atom)  Plus I'm just trying to hone my linux skills.  So I'm not sure BSD is the way to go.

---

### Post by night_fox on 2009-07-10
could you install ssh without the monitor by doing ctrl+alt+F1 on the live cd.

---

### Post by acranox on 2009-07-10
> **night_fox said:**
> could you install ssh without the monitor by doing ctrl+alt+F1 on the live cd.

I could.  But I'll still need a keyboard for that.

---

### Post by acranox on 2009-07-12
I'm trying the method here currently.
[https://help.ubuntu.com/community/Installation/NetworkConsole](https://help.ubuntu.com/community/Installation/NetworkConsole)

---

