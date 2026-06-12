---
title: "high cpu usage after plugging out external hard drive"
date: 2013-03-23
forum: Hardware
---

### Post by malakar.subhendu on 2013-03-23
I bought a new external hard disk drive (seagate 1tb backup plus). After using it for some time, whenever i'm plugging it out, the cpu usage gets too much high. Using system activity i saw that the culprit is the rsyslogd (using ~35%) and kworker (using ~ 25%) of the cpu usage. It happened 3 times and the machine had shut down due to overheating. What are these processes and why are they acting like this? this happens only when i plug the device out and not when i unmount it. What's the cure for it?

---

### Post by malakar.subhendu on 2013-03-23
now the hard disk is not able to mount also.
dmesg output is:

> [ 3791.677885] usb 1-1.1: >new high-speed USB device number 5 using ehci_hcd[ 3791.831989] usb 1-1.1: >New USB device found, idVendor=0bc2, idProduct=a013
[ 3791.831995] usb 1-1.1: >New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 3791.831998] usb 1-1.1: >Product: Backup+ BK
[ 3791.832001] usb 1-1.1: >Manufacturer: Seagate
[ 3791.832003] usb 1-1.1: >SerialNumber: NA533ZTL
[ 3791.832846] scsi7 : uas
[ 3791.834099] scsi 7:0:0:0: >Direct-Access     Seagate  Backup+ BK       0410 PQ: 0 ANSI: 6
[ 3791.834843] sd 7:0:0:0: >Attached scsi generic sg3 type 0
[ 3791.835062] sd 7:0:0:0: >[sdc] Spinning up disk...
[ 3792.835724] ....ready
[ 3795.843334] sd 7:0:0:0: >[sdc] 1953525167 512-byte logical blocks: (1.00 TB/931 GiB)
[ 3796.014772] sd 7:0:0:0: >[sdc] Write Protect is off
[ 3796.014783] sd 7:0:0:0: >[sdc] Mode Sense: 4f 00 00 00
[ 3796.015652] sd 7:0:0:0: >[sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3796.026527]  sdc: sdc1
[ 3796.029091] sd 7:0:0:0: >[sdc] Attached SCSI disk
[ 3826.329960] sd 7:0:0:0: >uas_eh_abort_handler tag 0
[ 3826.329973] sd 7:0:0:0: >uas_eh_device_reset_handler tag 0
[ 3826.329981] sd 7:0:0:0: >uas_eh_target_reset_handler tag 0
[ 3826.329985] sd 7:0:0:0: >uas_eh_bus_reset_handler tag 0
[ 3826.333953] usb 1-1.1: >URB BAD STATUS -71
[ 3826.402029] usb 1-1.1: >reset high-speed USB device number 5 using ehci_hcd
[ 3826.555545] sd 7:0:0:0: >Device offlined - not ready after error recovery


I was able to detect and write data into it in the morning (wrote around 200 gb of data) , and now i is not able to mount.

---

### Post by krishna.988 on 2013-03-23
How does it work on Win 7?

---

### Post by malakar.subhendu on 2013-03-23
it's working fine on windows 7.
I tried again and found out that if the drive is plugged in during boot time there is no problem. 
But if i'm trying to plug it in afterwards(if not plugged in during boot time) it's having those problem of not mounting.
This is the workaround for me as of now.

---

### Post by malakar.subhendu on 2013-03-23
seeing the output of dmesg, i think that that the ehci is causing the problem.

[http://manpages.ubuntu.com/manpages/precise/en/man4/ehci.4freebsd.html](http://manpages.ubuntu.com/manpages/precise/en/man4/ehci.4freebsd.html)

It tells that: 

 The driver is not finished and is quite buggy.

---

### Post by malakar.subhendu on 2013-04-16
blacklisting the uas module was not so good.
tried this: 
sudo rmmod uas
and it works for that session.
after restarting it , it again loads the uas module.
how to stop that?

---

### Post by zrdc28 on 2013-04-16
go to **sudu nano** ** /etc/modprobe.d/blacklist.conf**  and **blacklist uas** after you add it ctrl x and save.

---

### Post by malakar.subhendu on 2013-04-20
done that. but not working.

lsmod | grep "uas"

still gives the output as:

uas                    17844  0

---

### Post by malakar.subhendu on 2013-04-30
ok, it worked after some days, don't know why. i had to do this everytime:

sudo rmmod uas

but now it works.

can anybody tell me how to mark this as solved. i don't know how to mark it in the new format.

---

### Post by cortman on 2013-04-30
Just edit the first post and add the word [SOLVED] to the title.

---

