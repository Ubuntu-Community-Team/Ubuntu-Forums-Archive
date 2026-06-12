---
title: "Dual booting with CDROM?"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by J2R on 2009-04-02
I'm installing Ubuntu onto a machine which has Windows 2000 on it, to allow dual boot. The machine functions as a server, though, and has no keyboard, mouse or monitor (or at least won't have after I've finished the install!). What I want is to have the situation where if a specific CD is in the drive, it boots into one OS, otherwise it boots into the other. This is to make it simple for users - all they have to do is to stick the CD in the drive, reboot and they're in the other OS. How do I go about doing this? How do I configure a boot CD like this?

---

### Post by ronparent on 2009-04-02
If your bios is set to boot first to a cd, if present, then what you want will occur naturally with the ubuntu live cd. Just download the iso image from the ubustu site and burn it to the cd.

---

### Post by J2R on 2009-04-02
Won't this just boot the live CD? That's not what I want. I want the presence of the requisite CD in the drive to ensure that the Ubuntu installation on the second partition on my hard drive boots.

---

### Post by dandnsmith on 2009-04-02
One way would be to build yourself a CD which boots grub, and has a grub configuration to boot the Ubuntu installation.

This is slightly more difficult than a grub boot CD which needs to be hand-driven to tell it what to do.

---

### Post by J2R on 2009-04-02
Thanks, I'll take a look at grub boot CDs. I suppose what would be most flexible is if grub could look at a file on the first partition to determine what to boot - as opposed to burning this info to the CD.

---

### Post by J2R on 2009-04-02
[accidental repeat post removed]

---

