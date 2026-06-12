---
title: "Samsung P2 not showing up"
date: 2008-07-17
forum: General Help
---

### Post by dethredic on 2008-07-17
So, I just plugged my new samsung P2 in, and nothing happens. I was expecting it to show up as a USB device, but that is not the case. It works fine in windows. It says "USB Connected" on the screen. Any ideas?

---

### Post by alxlabs on 2008-07-17
Do you see it as a disk drive on your Win machine? I don't have this device so I don't know for sure but I expect it to have some sort of the comm mode where it looks like an external USB drive to the host system. Is this the case? Can you mount it as drive? I don't know if it will be helpful but I have a Sony device which is recognized by ubuntu as player etc but it does not automount it as drive however I can mount it manually...

---

### Post by dethredic on 2008-07-18
Ok, I found out I need to change the firmware type of the device.

---

### Post by the_hardy_kid on 2008-07-18
Dude, run
```
ls /dev/disk/by-label -lah
```
in terminal and post the results here

---

### Post by dethredic on 2008-07-18
> phil@phil:~$ ls /dev/disk/by-label -lah
ls: cannot access /dev/disk/by-label: No such file or directory
phil@phil:~$ 

odd.

---

### Post by dethredic on 2008-07-20
Yes, I just had to change the firmware and now it is working fine. I guess it is just like checking the enable disk mode one the iPods.

---

