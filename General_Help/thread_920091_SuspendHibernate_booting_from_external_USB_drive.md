---
title: "Suspend/Hibernate booting from external USB drive"
date: 2008-09-14
forum: General Help
---

### Post by JaWiB on 2008-09-14
I've set up my Dell Latitude D820 to dual-boot with Windows on my internal hard drive and Ubuntu on an external USB hard drive. Mostly, it seems to be working fine, except Suspend/Hibernate both do not work.

Actually, Suspend seems to work, but I can't resume from it--I get a screen full of errors like:
> 
EXT3-fs error (device sdb1): ext3_find_entry: reading directory #(...) offset 0

Where the ... is a string of numbers

After some searching, I thought maybe I needed to enable USB persist on the drive, so I try (after finding the correct device using lsusb):
> 
echo 1 > /sys/bus/usb/devices/5-7/power/persist

Which didn't help. Also, when I reboot, I find that persist is again set to 0 (don't know if that's part of the problem).

I'd post logs, but I'm a newbie to linux so I have no idea what you'd need to see.

Also, Hibernate seems to cause everything except the external drive to power down (which seems weird since other USB devices power down), and I can't resume at all.

Suggestions?

---

