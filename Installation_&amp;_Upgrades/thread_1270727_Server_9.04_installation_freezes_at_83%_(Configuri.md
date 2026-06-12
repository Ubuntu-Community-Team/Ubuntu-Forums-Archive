---
title: "Server 9.04 installation freezes at 83% (Configuring linux-server)"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by webjawns on 2009-09-19
Hi all,

This is my first install of Ubuntu and I've encountered a problem.  I can't seem to get past 83% during installation of Ubuntu Server 9.04.  It stalls on "Configuring linux-server," but I can't seem to figure out why.

System Specs:
1.8GHz Pentium IV
400MHz FSB
640MB DDR RAM
40GB/20GB HDDs

I've performed every test known to man... tried installing from different CDs, via mirror, etc.  Nada.

Please help!  It's been two whole days of going through this.

-Chris

---

### Post by dragonwars on 2009-11-28
> **webjawns said:**
> Hi all,

This is my first install of Ubuntu and I've encountered a problem.  I can't seem to get past 83% during installation of Ubuntu Server 9.04.  It stalls on "Configuring linux-server," but I can't seem to figure out why.

System Specs:
1.8GHz Pentium IV
400MHz FSB
640MB DDR RAM
40GB/20GB HDDs

I've performed every test known to man... tried installing from different CDs, via mirror, etc.  Nada.

Please help!  It's been two whole days of going through this.

-Chris

I have the exact same problem

---

### Post by Marlonsm on 2009-11-28
I don't know about the server version. But I remember some of my installs also freezing at around 80% because at that point it was downloading some packages from the internet, which is much slower than loading from the CD. After some time it would resume the install.

---

### Post by phillw on 2009-11-28
Hi,

Also - cleaning the optical drive on the machine you are installing onto, with a cd/dvd drive cleaner disk can help.

Regards,

Phill.

---

### Post by Marlonsm on 2009-11-28
> **phillw said:**
> Hi,

Also - cleaning the optical drive on the machine you are installing onto, with a cd/dvd drive cleaner disk can help.

Regards,

Phill.

Right. Also use the "Check disc" option before installing, to make sure it has no errors.

---

### Post by PCHome on 2013-02-08
I'm having the same issue at 83% in Server 12.10 after downloads during:

Configuring Linux-image-extra-3.5.0-17-generic

4GB RAM
Pentium Dual-Code E5300 2.6GHz
400GB drive

---

### Post by tgalati4 on 2013-02-08
This is an old thread, and will probably get shut down.  But look in /var/log/installer for debug files.  Look near the end since that is where the installer stopped.  While still installing, you may be able to Control-Alt-F1 to get to a terminal to

```
cd /var/log/installer
less syslog
```

Control-Alt-F7 to get back to the graphical installer desktop--assuming your video card doesn't lock up--that's another issue.

---

### Post by MAFoElffen on 2013-02-08
Good tip... except that getting back to the "install screen" is in another tty session as server and it's installer is not "graphical," so not in tty7. I think I remember server installing from tty4, <cntrl><alt><F4>...

It's been over a year since I've had to do that with a server install hang, so don't quote me on that, but it may be anywhere from tty2 to tty6. Easy to adapt to that.

---

### Post by PCHome on 2013-02-09
> **tgalati4 said:**
> This is an old thread, and will probably get shut down.  But look in /var/log/installer for debug files.  Look near the end since that is where the installer stopped.  While still installing, you may be able to Control-Alt-F1 to get to a terminal to

```
cd /var/log/installer
less syslog
```

Control-Alt-F7 to get back to the graphical installer desktop--assuming your video card doesn't lock up--that's another issue.
I saw it was on old post but it appeared to still be open and it was the same problem. However, I solved it as it appeared that one of the two memory chips was bad. With the second one removed, the install completed successfully. Thank you.

---

### Post by CharlesA on 2013-02-09
> **PCHome said:**
> I saw it was on old post but it appeared to still be open and it was the same problem. However, I solved it as it appeared that one of the two memory chips was bad. With the second one removed, the install completed successfully. Thank you.
With that, this thread is put back to sleep.

Glad you were able to get it sorted out. :)

---

