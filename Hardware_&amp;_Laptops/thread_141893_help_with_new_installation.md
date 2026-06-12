---
title: "help with new installation"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by dsimpson on 2006-03-09
I have been trying to get my modem to work so that I can connect to the internet. I have totally switched to Ubuntu and can only transfer software through another computer to mine. My problem is that my cd, floppy and dvd all fail to function properly so I cannot place information on a floppy or cd to transfer the needed information to find the software for my modem. I receive a "given UDI is not a mountable volume" error message when I attempt to save information on any of the devices. They all read info, the cd will play music and I can view pictures etc., and the floppy can carry information to my computer but will not save any to transfer from my computer to another. If anyone has any ideas which can help I would appreciate it.

---

### Post by taurus on 2006-03-09
First of, what is the spec of your machine and your modem (external/internal/USB).  Then, the problem you can't save or write anything to CD or floppy because perhaps they are mounted as root and user won't allow to write to them.  So, try saving your stuff using the sudo command then...

---

### Post by dsimpson on 2006-03-09
I keep getting my reply cut or lost, hope this is posted. My computer is an AMD, 900 Mhz, cdr/rw, dvd/rom drives, 1.44 floppy drive, with internal modem on a com port. The modem appears to not be listed with the PCI devices so may be a non standard or ISA bridge, and cannot be identified by scan modem. You are probably right about the devices being mounted as root and I am not able to write to them. That being the case, how would I go about saving using the sudo command? I am a novice at Linux and Ubuntu, so will need to be walked through the processes using explicit instructions. Thank you for your reply.

---

