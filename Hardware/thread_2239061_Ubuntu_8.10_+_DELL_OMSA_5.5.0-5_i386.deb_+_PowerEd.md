---
title: "Ubuntu 8.10 + DELL OMSA 5.5.0-5 i386.deb + PowerEdge 1750 No Controllers Found Issue"
date: 2014-08-11
forum: Hardware
---

### Post by KentC13 on 2014-08-11
Hello All,
 
_**PROBLEM:**_


 root@ubuntu:~# omreport storage controller
No controllers found
 *Please note the WEBGUI shows everything else EXCEPT the PERC*
 *EVERYTHING ELSE IS SHOWING UP ON SERVER WHEN I LOG*
 [B][U]
Loading via CLI:[/U][/B]


 /etc/init.d/dataeng restart
 /etc/init.d/dsm_om_connsvc restart
 /etc/init.d/snmpd restart
  I've installed the DELL OMSA from this LINK manually:
 [ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-i386/](ftp://ftp.sara.nl/pub/sara-omsa/dists/dell/sara/binary-i386/)
 dellomsa_5.5.0-5_i386.deb



  [B][U]SPECS:

[/U][/B]

 root@ubuntu:~# uname -a
Linux ubuntu 2.6.27-17-server #1 SMP Fri Mar 12 04:04:33 UTC 2010 i686 GNU/Linux
 root@ubuntu:~# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
 *-storage
          description: RAID bus controller
          product: PowerEdge Expandable RAID controller 4/Di
          vendor: Dell
          physical id: 3
          bus info: pci@0000:04:03.0
          logical name: scsi2
          version: 02
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi pcix bus_master cap_list
          configuration: driver=megaraid latency=32 mingnt=128 module=megaraid_mbox
 *-disk
             description: SCSI Disk
             product: LD 0 RAID5  279G
             vendor: MegaRAID
             physical id: 2.0.0
             bus info: scsi@2:2.0.0
             logical name: /dev/sda
             version: 412W
             size: 273GiB (293GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=2 signature=f362db24
 root@ubuntu:~# lspci | grep -i raid
04:03.0 RAID bus controller: Dell PowerEdge Expandable RAID controller 4/Di (rev 02)


 [B]TROUBLESHOOTING DONE:

[/B]

 root@ubuntu:~# omreport storage controller
No controllers found

root@ubuntu:~# lsmod | grep -i ipmi
ipmi_devintf           15112  2 
ipmi_si                46252  1 
ipmi_msghandler        42712  2 ipmi_devintf,ipmi_si
root@ubuntu:~# lsmod -i mpt
Usage: lsmod
root@ubuntu:~# lsmod | grep -i mpt
mptctl                 35972  0 
mptbase                86756  1 mptctl
scsi_mod              155468  6 mptctl,sd_mod,sr_mod,sg,megaraid_mbox,libata
root@ubuntu:~# modprobe mptctl
root@ubuntu:~# echo $?
0
root@ubuntu:~# modprobe mptbase
root@ubuntu:~# modprobe scsi_mod

 root@ubuntu:~# dmesg | grep -i mpt
[12313.810414] Fusion MPT base driver 3.04.07
[12313.816546] Fusion MPT misc device (ioctl) driver 3.04.07
[12313.816741] mptctl: Registered with Fusion MPT base driver
[12313.816748] mptctl: /dev/mptctl @ (major,minor=10,220)


  _**QUESTION:**_

 __Does anyone know how to configure the remaining portion of the DELL OMSA so the PERC shows up in the GU or OMREPORT?


 Also, I want to upgrade the FIRMWARE, will this be ok [I can load Windows XP Mini to do this task]
 FW UPDATE: [http://alturl.com/nnob8](http://alturl.com/nnob8)

---

### Post by mörgæs on 2014-08-12
8.10 has been obsolete for many years. Your best option is to begin with a fresh install of a supported version like 14.04.1.

About the root account:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

