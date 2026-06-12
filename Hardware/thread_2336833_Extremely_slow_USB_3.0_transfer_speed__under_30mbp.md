---
title: "Extremely slow USB 3.0 transfer speed ? under 30mbps ?"
date: 2016-09-11
forum: Hardware
---

### Post by saad_khan2 on 2016-09-11
Im transferring data on Ubuntu 16.04 to my external via USB 3.0....on Windows ive had transfers crossing 200mbs plus/s. Right now its transferring at 27-30mbps/s.....why so slow ? I have updated all drivers (or that i thought)

Im using a intel celeron bay trail system...which had faster speeds under Ubuntu 14.04....

---

### Post by Remson_Felipa on 2016-09-12
Same here too, some times its transfer @25mbps speed

---

### Post by sudodus on 2016-09-12
My 16.04.1 LTS system can transfer data via USB 3 with decent speed in an up to date Ubuntu 16.04.1 installed system. I wrote the file ubuntu-16.04.1-desktop-amd64.iso (1.5 GB), renamed it and read it. I did it in a [Toshiba laptop from 2013](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/), and both the internal and the external partitions have ext4 file systems.

```
root@tester-SATELLITE-PRO-C850-19W:~# time pv ubuntu-16.04.1-desktop-amd64.iso > /media/tester/trusty-3.13.0-x/t22;time sync
1,41GiB 0:00:09 [ 152MiB/s] [=========================================================>] 100%            

real	0m15.180s
user	0m0.020s
sys	0m2.272s

real	0m1.013s
user	0m0.000s
sys	0m0.012s
root@tester-SATELLITE-PRO-C850-19W:~# time pv /media/tester/trusty-3.13.0-x/t4 > t33-to-here;time sync
1,41GiB 0:00:10 [ 140MiB/s] [=========================================================>] 100%            

real	0m15.110s
user	0m0.024s
sys	0m2.728s

real	0m0.906s
user	0m0.000s
sys	0m0.004s
root@tester-SATELLITE-PRO-C850-19W:~# 
```

As you can see, the output from pv does not tell the whole truth, there are 5 more seconds in that process and one more second for syncing (flushing the buffers to the drives).

So 1.5 GB / 16 s ~ 90 -100 MB/s.

[hr][/hr]
Your transfer speeds look like USB 2 speed.

- Did you plug it into a USB 3 port on the computer? No question is too dumb to be asked ;-)

- Were you transferring a lot of small files? The overhead of starting and finishing makes the transfer speed much slower for many small files of the same total size as one big file.

- Was it a USB 3 pendrive? They always have flash memory hardware that is slower than the USB 3 system, sometimes even slower than the USB 2 system. See this link:

[FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

- There might be a mismatch between the driver/firmware and the USB 3 hardware in your computer, so that it defaults to USB 2.

- Are you transferring from or to a partition with another file system, for example NTFS? Maybe the linux driver for that file system is not efficient.

---

### Post by saad_khan2 on 2016-09-13
> **sudodus said:**
> My 16.04.1 LTS system can transfer data via USB 3 with decent speed in an up to date Ubuntu 16.04.1 installed system. I wrote the file ubuntu-16.04.1-desktop-amd64.iso (1.5 GB), renamed it and read it. I did it in a [Toshiba laptop from 2013]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/"), and both the internal and the external partitions have ext4 file systems.

```
root@tester-SATELLITE-PRO-C850-19W:~# time pv ubuntu-16.04.1-desktop-amd64.iso > /media/tester/trusty-3.13.0-x/t22;time sync
1,41GiB 0:00:09 [ 152MiB/s] [=========================================================>] 100%            

real    0m15.180s
user    0m0.020s
sys    0m2.272s

real    0m1.013s
user    0m0.000s
sys    0m0.012s
root@tester-SATELLITE-PRO-C850-19W:~# time pv /media/tester/trusty-3.13.0-x/t4 > t33-to-here;time sync
1,41GiB 0:00:10 [ 140MiB/s] [=========================================================>] 100%            

real    0m15.110s
user    0m0.024s
sys    0m2.728s

real    0m0.906s
user    0m0.000s
sys    0m0.004s
root@tester-SATELLITE-PRO-C850-19W:~# 
```

As you can see, the output from pv does not tell the whole truth, there are 5 more seconds in that process and one more second for syncing (flushing the buffers to the drives).

So 1.5 GB / 16 s ~ 90 -100 MB/s.

[HR][/HR]
Your transfer speeds look like USB 2 speed.

- Did you plug it into a USB 3 port on the computer? No question is too dumb to be asked ;-)

- Were you transferring a lot of small files? The overhead of starting and finishing makes the transfer speed much slower for many small files of the same total size as one big file.

- Was it a USB 3 pendrive? They always have flash memory hardware that is slower than the USB 3 system, sometimes even slower than the USB 2 system. See this link:

[FromUSBStick#Notes_about_speed]("https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed")

- There might be a mismatch between the driver/firmware and the USB 3 hardware in your computer, so that it defaults to USB 2.

- Are you transferring from or to a partition with another file system, for example NTFS? Maybe the linux driver for that file system is not efficient.


Yup, Blue USB to Blue USB, Transferring 700GB from a degraded array. Using a 3TB Seagate external. There could be a firmware or driver issue..that did not exist with Ubuntu 14...
transfer is from ext4 to NTFS i believe. 

I cant figure out how to set a USB 3.0 driver

---

### Post by saad_khan2 on 2016-09-13
some info below
> 

[sudo] password for saad:
root@NAS:~# lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 5000M
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=uas, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 480M
    |__ Port 2: Dev 3, If 0, Class=Hub, Driver=hub/4p, 480M
root@NAS:~# grep -i xhci /boot/config-$(uname -r)
CONFIG_USB_XHCI_HCD=y
CONFIG_USB_XHCI_PCI=y
CONFIG_USB_XHCI_PLATFORM=m




---

### Post by sudodus on 2016-09-13
I know very little about configuring USB 3 drivers. If ***you***, who are reading this, know more about it, please chip in and help us :-)

-o-

Do you get 'full' speed again, if you boot Ubuntu 14.04.1 LTS live (from a CD or USB drive)? In that case I suggest that you should consider re-installing it. *After all, Ubuntu 14.04 (with the trusty kernel, 3.13 series) is supported until April 2019*, while the corresponding community flavours (Kubuntu, Lubuntu, ... Xubuntu) are only supported until April 2017.

---

