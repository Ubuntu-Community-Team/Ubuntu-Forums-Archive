---
title: "Install Ubuntu on old PIII laptop"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by a4su_skyhawk on 2009-10-02
Hi All

I want to install Ubuntu on a PIII laptop, which version of Ubuntu should I use?
Desktop or Remix version?

Thank you.

---

### Post by SoftwareExplorer on 2009-10-02
I would use the desktop version. Remix is for netbooks.

---

### Post by a4su_skyhawk on 2009-10-02
Thanks. But the problem with this laptop is, it does not come with an optical drive and the BIOS does not support USB boot. The laptop is currently installed with Windows XP and I am wondering whether is it possible to copy the contents of Ubuntu CD into a USB pendrive and install via Windows. Or are there other ways to install for such machine?

By the way, this laptop has only 256MB RAM.

Thank you very much.

---

### Post by tgalati4 on 2009-10-02
linux mint xfce.  256 MB is minimal, but see if you can upgrade to 512.

You should be able to install using wubi.

---

### Post by SoftwareExplorer on 2009-10-03
> **a4su_skyhawk said:**
> Thanks. But the problem with this laptop is, it does not come with an optical drive and the BIOS does not support USB boot. The laptop is currently installed with Windows XP and I am wondering whether is it possible to copy the contents of Ubuntu CD into a USB pendrive and install via Windows. Or are there other ways to install for such machine?

By the way, this laptop has only 256MB RAM.

Thank you very much.

Use can use this -> [http://www.ubuntu.com/getubuntu/downloadmirrors#wubi]("http://www.ubuntu.com/getubuntu/downloadmirrors#wubi") . It will let you install ubuntu or even Xubuntu IIRC. Xubuntu is a little different from ubuntu because it uses a lighter desktop environment, so that it will run better on older hardware.

---

### Post by ackley on 2009-10-03
This is what I would do. If the P3 supports cd roms, which I'm sure it does. I'd take my drive from another computer, throw it in that for the install & use crunchbang. It runs the OpenBox WM & is super fast on minimal machines.

---

### Post by snowpine on 2009-10-03
256mb is borderline for either Ubuntu or Xubuntu. Crunchbang is a pretty good choice. If you can't get a CD-Rom drive working, you can use Unetbootin to install from the .iso image on your hard drive.

---

### Post by raymondh on 2009-10-03
> **snowpine said:**
> 256mb is borderline for either Ubuntu or Xubuntu. Crunchbang is a pretty good choice. If you can't get a CD-Rom drive working, you can use Unetbootin to install from the .iso image on your hard drive.

ditto on crunchbang

---

### Post by a4su_skyhawk on 2009-10-20
Thank you all for the your valuable suggestions.
Managed to get Ubuntu installed into the laptop.
Got an old external cd-rom and install via Wubi. The Wubi that come with the Live CD has issue and alway stuck at the 'Formatting swap space......" screen. Solved the problem with Wubi r134.
After that I just moved the Wubi installation to the Windows one using this guide
[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by vinutux on 2009-10-20
Xubuntu or Spri linux

---

### Post by a4su_skyhawk on 2009-10-23
Ubuntu. But my hard disk died yesterday!
A bit laggy with 256MB of RAM.

---

