---
title: "uvcvideo: Failed to query (GET_DEF) uvc control 2 on Unit 1 -32 (exp.1)"
date: 2022-05-13
forum: Hardware
---

### Post by rsteinmetz70112 on 2022-05-13
One of my computers is failing to boot. During the boot process I get the error in the title literally hundreds of times and the computer never gets to a login prompt. Googling this morning I see this type of error can be related to a video camera or microphone. I have a cheap USB web camera on the computer for zoome skype and Microsoft TEams. I will try this evening taking it off to see if that clears is. .

---

### Post by rsteinmetz70112 on 2022-05-20
I found the problem. The root filesystem was completely full and the computer would not complete booting. Once I was able put hands on the computer and boot using live media I was able to clean the filesystem and everything is working again.

What actually happened is for some unknown reason a USB drive I use to remotely backup other computers either did not mount (possibly after a power failure and reboot) or dropped it's mount. I have been mounting the drive from /etc/fstab. 
I've moved most of the mounts from /etc/fstab to autofs, but haven't completely got that working yet, maybe next week since the computer is located in a secondary residence that's often unoccupied.

---

