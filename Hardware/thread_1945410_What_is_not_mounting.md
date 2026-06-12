---
title: "What is not mounting?"
date: 2012-03-23
forum: Hardware
---

### Post by bohemian9485 on 2012-03-23
Hello forums.

Sometimes during booting I will see this message:

```

keys: Continue to wait, or Press S to skip mounting or M for manual recovery

```

As a Linux newbie, I wonder what is being mounted during the booting stage that produced this error. I have a SATA HDD (its partition is NTFS) connected externally to my netbook using SATA/IDE to USB cable. Is that the source? If so, how can I correct the problem?

Thanks in advance for the help.

---

### Post by bohemian9485 on 2012-03-25
Pressing F1 key during boot process showed that it is indeed searching for my external hard drive. I don't have this problem with my desktop system, it treats the hard disk as an ordinary USB device. My netbook seems to think otherwise and consider my hard drive as a regular one, even when it is connected using SATA/IDE to USB cable.

---

### Post by bohemian9485 on 2012-03-28
Looks like no immediate help is coming my way...:( I did what a newbie will do when faced with a problem he cannot tackle: OS re-installation. The good news is, it is not showing anymore after the re-installation. Not a way I'd like to solve the problem though.

---

### Post by hansdown on 2012-03-28
Glad you fixed it, bohemian9485.

---

### Post by Mark Phelps on 2012-03-29
> **bohemian9485 said:**
> Looks like no immediate help is coming my way...

Sorry I did not see this earlier, otherwise, I would have responded...

Anyway, next time this happens, continue to reboot (pressing S to skip), and once into Ubuntu, open your /etc/fstab file (sudo gedit /etc/fstab) and look for the line identifying the external drive.

Remove that line and save the changed file.

When you then reboot, you should no longer be seeing the prompt.

---

