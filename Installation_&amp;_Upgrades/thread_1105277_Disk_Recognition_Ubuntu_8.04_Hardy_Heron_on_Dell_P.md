---
title: "Disk Recognition Ubuntu 8.04 Hardy Heron on Dell PowerEdge 400SC"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by alfrz on 2009-03-24
I have found an unusual problem trying to install ubuntu on a Dell PowerEdge 400SC, I cannot access the hard drives. I've tried to find them using fdisk -l , but I simply don't get anything displayed for my local hard drives, just like if they weren't even connected.

By default the system has installed Windows Server 2003

---

### Post by chrisinspace on 2009-03-24
Do you mean you can't see the hard drives when you've booted into the Live Desktop?

---

### Post by alfrz on 2009-03-24
Exactly... also, when i run the partition editor it doesn't find anything.
Does it has to do with RAID support???
At startup (before it starts the OS) shows:```
CERC ATA100/4ch RAID ...
```
And I don't have any problems starting Windows Server 2003

---

### Post by chrisinspace on 2009-03-24
Yeah, but when you install Win2k3, you normally have to provide a driver for your RAID controller during the installation.  I don't have a lot of experience with RAID in Linux because I really only use it for PC's at the moment.

Are your HDD's SATA?

---

### Post by alfrz on 2009-03-24
yes.
Win2k3 was already installed on the computer when it was bought.

---

### Post by chrisinspace on 2009-03-25
[This]("http://ubuntuforums.org/showthread.php?t=1010118") worked for me in 8.04 and 8.10, but I'm trying to put 9.04 on a test box and it doesn't seem to help.  Give it a shot.

---

### Post by alfrz on 2009-03-26
Hey! sorry, I want to make a clarification, drives aren't SATA, just ATA.

I've tried the all_generic_ide trick with no success, one of my problems is that I don't have much access to the server due to it's use, but this weekend I need everything set in place to install ubuntu in it with the same settings as they are right now on windows.

I found a "datasheet" of this computer [www.dell.com/downloads/global/products/pedge/en/400sc_specs.pdf](www.dell.com/downloads/global/products/pedge/en/400sc_specs.pdf) If it's of any help.

Thanks

---

