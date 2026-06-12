---
title: "CD/DVD drive in a bit of a state"
date: 2011-05-19
forum: Hardware
---

### Post by michaelA1330 on 2011-05-19
( i am not sure if im posting in the write section , if im not redirect me please )

well the problem is my CD/DVD drive dousnt work at all , it cant read disks , or play them at all , ive had this problem with ubuntu since i switched from windows (8.10) 
its not a problem with the drive , physical its fine , but it will not work at all all on ubuntu 
i cant find any drivers for it on the hardware drivers , and i have no clue how to fix it 

running - 10.04 
laptop - emachine E625 
i really need to solve this quick because i have work of university that i need to burn to disks , 
any help would be a godsend

---

### Post by gordintoronto on 2011-05-19
What makes you believe the drive works? Can you boot from a Live CD? It sounds possible that a cable is disconnected.

---

### Post by Yellow Pasque on 2011-05-19
Post output of:
```
sudo lshw -C disk
```

---

### Post by michaelA1330 on 2011-05-20
> **Temüjin said:**
> Post output of:
```
sudo lshw -C disk
```
  
 *-disk                  
       description: ATA Disk
       product: ST9160310AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 0303
       serial: 5SV63WQC
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002ae6b
  *-cdrom
       description: DVD-RAM writer
       product: DVD A  DS8A3S
       vendor: Slimtype
       physical id: 1
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HA17
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by gordintoronto on 2011-05-20
OK, it's not a loose cable.

Oh, interesting, Windows 7 has a problem with that DVD drive:
[http://news.softpedia.com/news/Windows-7-RTM-Can-t-Recognize-TSST-TS-L633B-and-PLDS-DS-8A3S-DVD-Drives-133165.shtml](http://news.softpedia.com/news/Windows-7-RTM-Can-t-Recognize-TSST-TS-L633B-and-PLDS-DS-8A3S-DVD-Drives-133165.shtml)

Something called ALPM is used to reduce power consumption, but it renders that drive non-functional. Could you open Accessories/Terminal and enter this command:
cat /sys/class/scsi_host/host0/link_power_management_policy

If it says anything except max_performance, you might try changing it:
gksudo gedit /sys/class/scsi_host/host0/link_power_management_policy

Might need to reboot to see if it helps.

---

### Post by michaelA1330 on 2011-05-22
> **gordintoronto said:**
> OK, it's not a loose cable.

Oh, interesting, Windows 7 has a problem with that DVD drive:
[http://news.softpedia.com/news/Windows-7-RTM-Can-t-Recognize-TSST-TS-L633B-and-PLDS-DS-8A3S-DVD-Drives-133165.shtml](http://news.softpedia.com/news/Windows-7-RTM-Can-t-Recognize-TSST-TS-L633B-and-PLDS-DS-8A3S-DVD-Drives-133165.shtml)

Something called ALPM is used to reduce power consumption, but it renders that drive non-functional. Could you open Accessories/Terminal and enter this command:
cat /sys/class/scsi_host/host0/link_power_management_policy

If it says anything except max_performance, you might try changing it:
gksudo gedit /sys/class/scsi_host/host0/link_power_management_policy

Might need to reboot to see if it helps.

it aint doing jack , but thanks for the help man ,
is there anyway i could manually disable the ALPM or delete it entirely ?

---

### Post by gordintoronto on 2011-05-22
max_performance
is supposed to manually disable it. I think ALPM is built into the kernel.

---

### Post by michaelA1330 on 2011-05-24
> **gordintoronto said:**
> max_performance
is supposed to manually disable it. I think ALPM is built into the kernel.

is there no other way to get around this ?

---

### Post by gordintoronto on 2011-05-24
I'm sorry, I'm completely out of suggestions.

You could try playing with Power Management, but I would be surprised if it helped. The other possibility is Google. I think I started with:
DS8A3S linux

---

