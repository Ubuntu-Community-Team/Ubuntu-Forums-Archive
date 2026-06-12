---
title: "No network on Dell Inspiron 11z"
date: 2010-04-16
forum: Hardware
---

### Post by pinkunicorn on 2010-04-16
I just got a Dell Inspiron 11z. I'm trying to install Lucid Lynx beta2 on it, but fail. On the other hand, Karmic and Jaunty fail as well.

I have a PXE netboot system set up. When I try to install Lucid, it loads the kernel and initrd, asks a couple of install questions (keyboard, country) and then fails to detect the network card and the installation of course can't continue. 

If I boot from a rescuecd image I have (I'm not sure exactly where it comes from, but it presents itself as "Linux sysresccd 2.6.31.00-std130-amd64"), the machine comes up OK. After booting, I can use the net-setup tool in the rescuecd image to set up the wired interface without problems, and it works fine. It claims to use the driver atl1c. So, the card works, and it works with Linux.

lshw presents the network card as "Atheros AR8132 / L1c Gigabit Ethernet Adapter".

I checked my desktop machine (running Karmic), and it has atl1c.ko installed. I took the initrd.gz from my Karmic netboot, unpacked it, inserted atl1c.ko (do I need to do more than just copy the file?), repacked, and tried to netboot from that, but that still doesn't help (still no network). However, the initrc from Karmic netboot claims to be 2.6.31-14-generic while the kernel actually installed with Karmic is 2.6.32-19-generic. I suppose this could be a problem.

I've also tried to use unetbootin to install Lucid from a USB stick, but this doesn't work either. After a few installer questions, it wants to set up a mirror to get packets from, and when it can't reach that the installation fails.

Ideas, anyone?

---

### Post by pinkunicorn on 2010-05-04
This is still a problem in the real Lucid release.

---

### Post by KenSharp on 2010-06-17
Have you filed a bug?

---

### Post by pinkunicorn on 2010-06-21
Yes, but I've seen no reactions there either: [https://bugs.launchpad.net/ubuntu/+bug/566673](https://bugs.launchpad.net/ubuntu/+bug/566673)

---

### Post by KenSharp on 2010-06-21
That's fairly normal, but at least it's logged.

---

