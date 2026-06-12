---
title: "My Ubuntu 9.04 install is not recognising my external Hard Disk anymore"
date: 2009-11-13
forum: Hardware
---

### Post by Devakishor on 2009-11-13
Hi,

I use a 320 GB, Seagate SATA external USB HDD. It's NTFS format. I have used it before without any problems.. using NTFS configuration tool of course.

Now, my laptop just doesn't recognise it anymore. I insert the USB and absolutely no response from the laptop. 

I know there's little info for anyone to suggest any solution, but has anyone faced similar probs? Can anyone help?

Thanks.

---

### Post by coffeecat on 2009-11-13
That's fine. That's enough to be going on with.

Let's see if the system is recognising the drive, even if it isn't mounting the partition. Plug the drive in, switch it on, open a terminal and post the output of the following three commands:

```
dmesg | tail
lsusb
sudo fdisk -l
```And a question: do you have Windows and/or another Linux version, and have you tried the drive with them?

> **Devakishor said:**
> . using NTFS configuration tool of course.

Exactly what was the configuration tool, and what did you do with it? Jaunty automounts external NTFS drives and reads/writes them out of the box. Normally you don't have to do any configuration.

Having said that, I've come across the occasional thread where there seems to be a problem in the firmware of some Seagate drives which causes problems with Ubuntu/Linux. Since your drive used to work with Jaunty this is probably not the case here, unless a recent update broke something.

---

