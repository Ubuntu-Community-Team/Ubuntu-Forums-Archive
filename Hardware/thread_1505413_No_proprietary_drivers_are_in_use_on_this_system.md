---
title: "No proprietary drivers are in use on this system"
date: 2010-06-09
forum: Hardware
---

### Post by geko6 on 2010-06-09
When I go to System | Administration | Hardware Drivers I get the message "No proprietary drivers are in use on this system".  I noticed on this thread [http://www.uluga.ubuntuforums.org/showthread.php?t=1291058]("http://www.uluga.ubuntuforums.org/showthread.php?t=1291058") that others have solved this problem by installing nvidia-modaliases.  However, I already have installed (at least it shows in Synaptic Package Manager) nvidia-173-modaliases.  But I still get the "No proprietary drivers" message.

I'm runnning Ubuntu 10.4 (64 bit) on an Acer Aspire 5720.  I believe it has the Intel GM965 chipset.

---

### Post by TechnikAlsace on 2010-06-09
If you have an Intel graphics chipset, the drivers/modules are intgrated in the kernel. So there is NO need for aliases and proprietary drivers and you can be happy.

Proprietary drivers are only required where the "community drivers" are not sufficient or if the vendor of a component made drivers especially for linux. 

As long as you have kernel support for all your system components just rejoice!

---

### Post by geko6 on 2010-06-12
Thanks TechnikAlsace.  I understand now that this screen does not show Kernel integrated drivers.  Do you know if there's a way to view ALL drivers (whether integrated in the kernel or not)?

---

### Post by LoloftheRings on 2010-06-13
Go to terminal and enter:
```

lsmod

```
This wil show the drives loaded on the right column.

---

