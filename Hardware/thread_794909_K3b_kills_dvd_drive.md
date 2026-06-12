---
title: "K3b kills dvd drive"
date: 2008-05-15
forum: Hardware
---

### Post by markkiteflyer on 2008-05-15
Recently upgraded to Kubuntu Hardy.  Now K3B kills my CD/DVD drive so bad that I need to power cycle the machine to get it working again.  Soft-reset/reboot doesn't work.

This worked fine under Feisty.

I think this is the same bug as reported here:
[http://sidux.com/PNphpBB2-viewtopic-t-9201.html](http://sidux.com/PNphpBB2-viewtopic-t-9201.html)

System details are:
Kubuntu 8.04 x86_64
HP xw4400 workstation
Drive: CD/DVDW TS H653L
> 
~$ uname -a
Linux hostname 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
~$ k3b -v
Qt: 3.3.8b
KDE: 3.5.9
K3b: 1.0.4


Any suggestions?  Thanks in advance.

When I run K3b dmesg reports the following:

> May 15 16:45:05 h-mhb-md-kub kernel: [  482.056883]          cdb ac 00 00 00 00 00 00 00  00 01 03 00 00 00 00 00
May 15 16:45:05 h-mhb-md-kub kernel: [  482.056885]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
May 15 16:45:05 h-mhb-md-kub kernel: [  482.367489] ata4: soft resetting link
May 15 16:45:06 h-mhb-md-kub kernel: [  482.531083] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 15 16:45:36 h-mhb-md-kub kernel: [  512.609565] ata4.00: qc timeout (cmd 0xa1)
May 15 16:45:36 h-mhb-md-kub kernel: [  512.609577] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x5)
May 15 16:45:36 h-mhb-md-kub kernel: [  512.609585] ata4: failed to recover some devices, retrying in 5 secs
May 15 16:45:41 h-mhb-md-kub kernel: [  517.600696] ata4: hard resetting link
May 15 16:45:46 h-mhb-md-kub kernel: [  523.102502] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:45:51 h-mhb-md-kub kernel: [  527.626866] ata4: hard resetting link
May 15 16:45:56 h-mhb-md-kub kernel: [  533.128681] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:46:01 h-mhb-md-kub kernel: [  537.653028] ata4: hard resetting link
May 15 16:46:06 h-mhb-md-kub kernel: [  543.154830] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:46:36 h-mhb-md-kub kernel: [  572.583486] ata4: limiting SATA link speed to 1.5 Gbps
May 15 16:46:36 h-mhb-md-kub kernel: [  572.583488] ata4: hard resetting link
May 15 16:46:41 h-mhb-md-kub kernel: [  577.582607] ata4.00: disabled
May 15 16:46:41 h-mhb-md-kub kernel: [  577.582633] ata4: hard resetting link
May 15 16:46:47 h-mhb-md-kub kernel: [  583.487378] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:46:01 h-mhb-md-kub kernel: [  537.653028] ata4: hard resetting link
May 15 16:46:06 h-mhb-md-kub kernel: [  543.154830] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:46:36 h-mhb-md-kub kernel: [  572.583486] ata4: limiting SATA link speed to 1.5 Gbps
May 15 16:46:36 h-mhb-md-kub kernel: [  572.583488] ata4: hard resetting link
May 15 16:46:41 h-mhb-md-kub kernel: [  577.582607] ata4.00: disabled
May 15 16:46:41 h-mhb-md-kub kernel: [  577.582633] ata4: hard resetting link
May 15 16:46:47 h-mhb-md-kub kernel: [  583.487378] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:46:51 h-mhb-md-kub kernel: [  587.568865] ata4: hard resetting link
May 15 16:46:57 h-mhb-md-kub kernel: [  593.473639] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:47:01 h-mhb-md-kub kernel: [  597.551148] ata4: hard resetting link
May 15 16:47:07 h-mhb-md-kub kernel: [  603.455910] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:46:51 h-mhb-md-kub kernel: [  587.568865] ata4: hard resetting link
May 15 16:46:57 h-mhb-md-kub kernel: [  593.473639] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:47:01 h-mhb-md-kub kernel: [  597.551148] ata4: hard resetting link
May 15 16:47:07 h-mhb-md-kub kernel: [  603.455910] ata4: port is slow to respond, please be patient (Status 0x80)
May 15 16:47:36 h-mhb-md-kub kernel: [  632.465159] ata4: limiting SATA link speed to 1.5 Gbps
May 15 16:47:36 h-mhb-md-kub kernel: [  632.465161] ata4: hard resetting link
May 15 16:47:41 h-mhb-md-kub kernel: [  637.476256] ata4: EH complete
May 15 16:47:41 h-mhb-md-kub kernel: [  637.479731] ata4.00: detaching (SCSI 3:0:0:0)



---

