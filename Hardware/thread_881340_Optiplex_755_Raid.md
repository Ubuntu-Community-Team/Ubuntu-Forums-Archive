---
title: "Optiplex 755 Raid"
date: 2008-08-05
forum: Hardware
---

### Post by CyberCowboy on 2008-08-05
How do I get Ubuntu 8.04.1 server edition to work with the on-board RAID built into a Dell Optiplex 755?  I just installed the OS but upon a reboot it had to mirror the drive in the BIOS after the raid is configured.

HOw do I get it to write in real-time?

---

### Post by tamoneya on 2008-08-06
i believe the optiplex would be fake raid.  Look here for details: [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by CyberCowboy on 2008-08-06
> **tamoneya said:**
> i believe the optiplex would be fake raid.  Look here for details: [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

Thanks, I looked at that guide, however it seems to want the livecd, which since I'm doing a server installation doesn't exist.  How, or where in the setup do I interject the DMRAID install?

---

### Post by UtuBoy on 2009-08-14
Hi!

I've come across exactly the same problem with the same Dell Optiplex755, Intel Core 2 Duo @ 3.0GHz, with two SATA HDDs. I would do a Linux Software RAID but it has also refused, all goes well until the last part of installation, it fails to install a boot loader, i've tried with both Grub and LILO

---

