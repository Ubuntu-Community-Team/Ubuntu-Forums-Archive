---
title: "partitioning hd on new asus m50vm-b1"
date: 2008-09-13
forum: Hardware
---

### Post by demianlessa on 2008-09-13
Hi,

MACHINE: ASUS M50 Series M50Vm-B1 NoteBook Intel Core 2 Duo T9400(2.53GHz) 15.4" Wide XGA+ 4GB Memory 320GB HDD 5400rpm DVD Super Multi NVIDIA GeForce 9600M GS.

([http://www.newegg.com/Product/Product.aspx?Item=N82E16834220343](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220343))

PROBLEM: Linux installation hangs while partitioning. GParted manages to delete partitions (hence it writes to the partition table successfully). However, it hangs while trying to format *any* filesystem (ext2, ext3, xfs, jfs).

DETAILS: I first tried PC-BSD 7 beta, and it installed successfully using UFS2, but it was dog slow. So I tried current releases of Ubuntu, Mint, CentOS, and Mandriva. Then, I also tried Sabayon 3.4, Ubuntu 7.04, and Adios 3.14 (yes, that desperate!). None of them installed.

After trying to install these distros (and destroying the partition tables in the process), I managed to recover from the provided Vista CD.

I can boot from any live CD of the above distros, so I'm assuming this is a hd, hd controller, or motherboard issue *with linux*.

I did some fair amount of research, but found nothing about this specific notebook, or anyone having a similar problem with partitioning the hd.

I can provide logs, dmesg output etc, if you thing this might help solve my problem.

NOTE: at this time I am not worried about getting the video card, wireless, fingerprint reader, webcam, or sound to work properly. I just want to install the OS to my hard drive!

Thank you all!

Demian

---

### Post by Zealousy on 2008-09-18
I'm having the same issue! If anyone could provide some insight it would be much appreciated.

---

### Post by IntuitiveNipple on 2008-09-18
It sounds as if there might be an issue with the disk controller or configuration.

With the system started using a Live CD, please provide the output of the following commands (so we have an overview of what specific hardware the system has):
```

lspci -nn

lsusb

```
Also, please attach a (compressed) copy of the start-up **dmesg** log:
```

cd /tmp
cat /var/log/dmesg | gzip > dmesg.log.gz

```
The file to attach is "/tmp/dmesg.log.gz" (If gzip is not available attach the uncompressed log-file).

If you can't connect to the Internet using the Live CD copy this file to a safe location (USB memory stick, floppy disk, etc.) and then get it from that storage location when you have Internet access.

---

### Post by demianlessa on 2008-09-18
Hi Zealousy,

I haven't had luck in solving this issue yet. I tried FreeBSD 7.0 but it is having problems with the ethernet nic, so it's a deal breaker for me at this time. 

PCBSD does a good job with the wired and nvidia drivers. I haven't tested bluetooth, firewire, fingerprint, webcam etc though. Hotkeys are not working out of the box, but the misc/hotkeys port can help with that. Also, no default support for reiserfs, so you have to compile that module in src/modules. I currently can't play AVI files, but sound and video are otherwise working. I haven't tested browser plugins either. The graphical interface to configuration tools is either lacking or plain unintuitive. You have to go to the command line. Oh well, there's more if you care to know, but I feel like I'm just rambling now... lol...

Good luck, and keep me posted if you figure out how to solve this!

Demian

---

### Post by demianlessa on 2008-09-21
Anyone who might be interested in the result of this thread, I managed to install 8.04 on my hard drive using the graphic installer by setting the following boot options on the start up screen:

acpi=off pci=noacpi noapic nolapic ide=nodma

Hope I get the rest of the hardware working alright!

Thanks,

Demian

---

