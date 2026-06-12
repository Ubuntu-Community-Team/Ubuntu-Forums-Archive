---
title: "System unresponsive during I/O"
date: 2009-08-16
forum: Hardware
---

### Post by shylent on 2009-08-16
I've run into the following problem while arranging my stuff - whenever there is a long i/o operation going on (copying some videos/music), the system becomes extremely unresponsive - it is impossible to do anything, - menus don't open, buttons don't get pressed, etc. This happens when I try to copy nautilus and via the command line as well (through mc or just cp) - so it is not related to the GUI, apparently.

The system runs on a Core2 Duo cpu. I have 4Gb RAM. So, clearly, it shouldn't lock up like that.

Don't know what info you might need, but here's some:

```
$ uname -a
Linux localhost 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
``````

$df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext3     19G  2.9G   15G  17% /
tmpfs        tmpfs    1.8G     0  1.8G   0% /lib/init/rw
varrun       tmpfs    1.8G   96K  1.8G   1% /var/run
varlock      tmpfs    1.8G     0  1.8G   0% /var/lock
udev         tmpfs    1.8G  160K  1.8G   1% /dev
tmpfs        tmpfs    1.8G  200K  1.8G   1% /dev/shm
lrm          tmpfs    1.8G  2.2M  1.8G   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5     ext3    441M   36M  383M   9% /boot
/dev/sda8     ext3    410G   83G  307G  22% /home

``````
$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by shylent on 2009-08-17
bump

---

### Post by babeliak on 2009-08-17
sorry :-k

---

### Post by shylent on 2009-08-17
Well, thanks a lot for hijacking my thread. There was not much activity in it anyway, eh?

---

### Post by shylent on 2009-08-18
bump

---

### Post by shylent on 2009-08-19
bump

---

### Post by SlugSlug on 2009-08-19
I had this problem, I ended up banging my / and /home on a separate small drive 
now shifting for the other drives don't effect performance...

---

### Post by shylent on 2009-08-22
Well, I DO hope, that there is a solution, that doesn't involve adding more hardware to the system.

---

### Post by shylent on 2009-08-24
bump

---

### Post by shylent on 2009-08-25
bump

---

