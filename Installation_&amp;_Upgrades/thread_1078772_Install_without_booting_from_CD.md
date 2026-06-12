---
title: "Install without booting from CD?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by dbbolton on 2009-02-23
I have tried to boot dozens of Linux CDs on my old laptop (and even tried booting over network, see here [http://ubuntuforums.org/showthread.php?t=1077035](http://ubuntuforums.org/showthread.php?t=1077035) ), and the only think that will boot is Damn Small Linux. I was able to install it to the hard drive and it boots from the hard drive if I add the "nousb" option. It is essentially running Debian woody, which is around 6 years old. My original plan was to upgrade to sarge, then etch, then lenny, but this did not work. There were several pitfalls when I tried to perform a dist-upgrade.

What I would like to have running on this machine is Hardy or Intrepid. Would it be possible to boot Damn Small and then install Ubuntu from a disc?

Specs:

Compaq Presario V2000 series 
AMD Turion 64 1.6 ghz
1 GB ram
ATI Radeon XPress Mobility graphics

---

### Post by mfaust731 on 2009-02-23
unetbootin

---

### Post by Pumalite on 2009-02-23
Post your specs. You might have little memory, an old CPU, etc.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by dbbolton on 2009-02-23
> **mfaust731 said:**
> unetbootin

According to the BIOS, it can only boot from CD, the hard drive, or the network.

> **Pumalite said:**
> Post your specs. You might have little memory, an old CPU, etc.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I have 1GB of memory. I also ran a memtest on it from a live CD, and it passed 100% with 0 errors.

---

### Post by Pumalite on 2009-02-23
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by dbbolton on 2009-02-23
> **Pumalite said:**
> [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)
Forgive me if I misunderstand, but wouldn't this only be helpful if my computer could boot from USB?

---

### Post by Pumalite on 2009-02-23
'If using Linux, make the file executable (using either the command chmod +x ./unetbootin-linux, or going to Properties->Permissions and checking "Execute"), then start the application, you will be prompted for your password to grant the application administrative rights, then the main dialog will appear, where you select a distribution and install target (USB Drive or [COLOR="Red"]Hard Disk[/COLOR]), then reboot when prompted.'

---

