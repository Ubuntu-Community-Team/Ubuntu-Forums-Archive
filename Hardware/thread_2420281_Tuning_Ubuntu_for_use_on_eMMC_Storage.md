---
title: "Tuning Ubuntu for use on eMMC Storage"
date: 2019-06-02
forum: Hardware
---

### Post by seb101 on 2019-06-02
Does anyone know of a good guide/tutorial for running Ubuntu from eMMC storage?  I'm building an NVR using an Intel NUC device with eMMC on board. 

eMMC is a flash type memory device similar to SD cards that is embedded in many current IOT targetted devices.   As with all memory of this type, it has limited write cycle life.  A 'good' ubuntu system running on this type of storage would minimize any writing to the disk.  Ideally the aim would be to have a system that *almost *read-only from the boot disk, except for apt installs and updates.  Everyting else (all ephemeral and app data) would go onto the attached HDD. 

In particular - you'd want to avoid the continual writing of log files to the disk.  Platforms like OpenWRT instead log to RAM and only write to disk if specifically commanded to.  How can this be done on Unbuntu?

Secondly, I'd want to try and identify any processes that are consistently writing to disk and have them use the secondry HDD attached.  Any guides on how to do this?

Thanks!

---

### Post by LwIh%*7 on 2019-06-02
Could this be what you are looking for?

 [https://askubuntu.com/questions/1135878/installing-ubuntu-on-an-emmc-how-can-it-be-so-hard](https://askubuntu.com/questions/1135878/installing-ubuntu-on-an-emmc-how-can-it-be-so-hard)
[https://askubuntu.com/questions/708156/how-to-install-ubuntu-14-04-3-on-built-in-emmc-flash](https://askubuntu.com/questions/708156/how-to-install-ubuntu-14-04-3-on-built-in-emmc-flash)

---

### Post by TheFu on 2019-06-02
The *Linux File System Hierarchy Standards* document would be where I started. Google finds it easily at TLDP.
It lays out which file systems/directories can be read-only, which can be remote, which must be local and writable.

---

