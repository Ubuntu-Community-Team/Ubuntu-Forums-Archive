---
title: "Backup from live cd"
date: 2008-09-29
forum: General Help
---

### Post by reyesncbt on 2008-09-29
Hello,

Well, iam new to the OS, for the moment i like to use the live cd. I have 2 hhd one with windows media center and the other one its just for storage (No OS installed).I was wondering if theres way to save or backup OS, APP,updates/upgrades/ (From CD live mode), inside the HDD im using for storage only? If its possible, how can i restore that backup? Pls provide coding fore backup or save and restoring.

---

### Post by cariboo on 2008-09-29
You could use dd, it is included on the livecd. It is a command line utility so you will have to open a Applications-->Accessories-->Terminal to use it. For example to create an exact image you your windows hard drive type:

```
dd if=/dev/sda1 of=/dev/sdb1/windows.iso
```

To restore the image you just made, in a terminal type:

```
dd if=/dev/sdb1/windows.iso of=/dev/sda1
```

/dev/sda1 and /dev/sdb1 are just examples your partition scheme may be different.

This will create an exact image of the hard drive with windows installed on it including the empty space.

An alternative would be partimage, it at least has a text based interface. I don't think it is included on the livecd, but you can download and install it it ram and use it until you reboot. Partimage is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

