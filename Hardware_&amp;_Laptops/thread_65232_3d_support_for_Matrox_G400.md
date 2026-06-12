---
title: "3d support for Matrox G400"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by daller on 2005-09-13
According to: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28Matrox%29%7C%28G400%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards?highlight=%28Matrox%29%7C%28G400%29)

the Matrox G400 card is "fully" supported...

The card:

madsen@ubuntu:~$ lspci | grep "Matrox"
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400 AGP (rev 05)

Running glxgears:

madsen@ubuntu:~$ glxgears
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering

What did I do wrong? (not that I did much :))

It says that it works in 16 bit mode - How is that activated?

---

### Post by wvslkr on 2005-09-13
Open your xorg.conf file and find the entry for default depth; change from probably 24 to16.

---

### Post by daller on 2005-09-13
Didn't change anything!

The error-message disapeared magically! (glxgears)

Trying to run a 3d-game still sucks!

---

### Post by chrisle on 2005-09-15
Look at [Matrox dri broken](http://ubuntuforums.org/showthread.php?t=64666&highlight=matrox) 

I have the same problem.

Does someone know how and where to write a bug report.

---

### Post by chrisle on 2005-09-15
The bug is described here:

[matrox dri bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=15528) 

So we can hope it will be fixed.

Can someone please test if switching from gdm to console while logging in kills the X-server. 

Thanxs chris.

---

### Post by chrisle on 2005-09-15
Are you using breezy?

If yes, can you pleae move the thread.

Bye chris.

---

### Post by daller on 2005-09-23
Well, I do use Breezy - but there are no hardware-specific Breezy section yet!!!

If a solution works in Hoary - it should work in Breezy, right???

---

