---
title: "Eeepc 900 SD Card Reader doesn't work"
date: 2010-01-06
forum: Hardware
---

### Post by Lucaluca on 2010-01-06
Hi guys! I've installed on my eeepc 900 Ubuntu Netbook Remix 9.10. Everything was ok and all hardware components worked immediately but no the SD card reader! When I put a card into, nothing happen! I used the command sudo fdisk-l but if there is a card into my pc it blocks and only if I remove it I can digit another command. I've also tried to use gparted but when it was searching devices and arrive to /dev/sdc it blocks!
 I hope you'll find the solution to my problem.
 

 P.S. I'm sorry for my bad english


):P

---

### Post by chewearn on 2010-01-06
Slot in the card, wait a few seconds, then run:
```

dmesg | tail -n 20

```Post the output.

---

### Post by Lucaluca on 2010-01-06
This is the output:

```
[  173.057461]  sdc: sdc1
[  212.417103] sd 2:0:0:0: [sdc] Device not ready
[  212.417112] sd 2:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  212.417121] sd 2:0:0:0: [sdc] Sense Key : Not Ready [current] 
[  212.417130] sd 2:0:0:0: [sdc] Add. Sense: Medium not present
[  212.417142] end_request: I/O error, dev sdc, sector 3862512
[  212.417153] Buffer I/O error on device sdc, logical block 482814
[  212.430097] sd 2:0:0:0: [sdc] Device not ready
[  212.430104] sd 2:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  212.430112] sd 2:0:0:0: [sdc] Sense Key : Not Ready [current] 
[  212.430121] sd 2:0:0:0: [sdc] Add. Sense: Medium not present
[  212.430133] end_request: I/O error, dev sdc, sector 3862512
[  212.430142] Buffer I/O error on device sdc, logical block 482814
[  212.451119] sdc: detected capacity change from 1977614336 to 0
[  223.024438] sd 2:0:0:0: [sdc] 3862528 512-byte logical blocks: (1.97 GB/1.84 GiB)
[  223.027405] sd 2:0:0:0: [sdc] Write Protect is off
[  223.027412] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  223.027418] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  223.036224] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  223.036238]  sdc: sdc1
```

---

### Post by chewearn on 2010-01-06
As you can see from the output, it complains about I/O errors.  This could mean a few things:

1. SD card is faulty -> try another SD card
2. Card reader is faulty -> try SD card on another reader
3. Contact is dirty or corroded -> trying cleaning the contact on the SD card
4. Something wrong with Ubuntu -> try SD card on another OS
5. Something wrong with PC -> try SD card on another computer

---

### Post by nick268 on 2010-03-24
Exactly the same problem on my eee900. Different cards tried, were working on the original machine setup.

My guess ubuntu problem.

---

### Post by gewitty on 2010-05-14
I just encountered the sane problem after installing karmic remix on my eee PC 4G.

The output I get from dmsg is:

dave@dave-laptop:~$ dmesg | tail -n 20
[  371.660078] sd 2:0:0:0: [sdb] Unhandled sense code
[  371.660085] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  371.660096] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  371.660110] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  371.660125] end_request: I/O error, dev sdb, sector 7864304
[  371.660138] Buffer I/O error on device sdb, logical block 983038
[  551.753061] sd 2:0:0:0: timing out command, waited 180s
[  551.753089] sd 2:0:0:0: [sdb] Unhandled sense code
[  551.753097] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  551.753109] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  551.753123] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  551.753138] end_request: I/O error, dev sdb, sector 7864304
[  551.753151] Buffer I/O error on device sdb, logical block 983038
[  731.792083] sd 2:0:0:0: timing out command, waited 180s
[  731.792113] sd 2:0:0:0: [sdb] Unhandled sense code
[  731.792121] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  731.792132] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  731.792146] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  731.792161] end_request: I/O error, dev sdb, sector 7864304
[  731.792175] Buffer I/O error on device sdb, logical block 983038

The card reader worked fine with EasyPC, so this is definitely an issue with karmic. Anyone have any suggestions?

---

### Post by dranoweb on 2010-06-17
The fix is quite simple,

reboot, 

press f2 for bios menu

change os status to "complete" instead of "start"


(pretty sure it's under the boot tab)
some odd thing asus decided to do for install windows on the eee 900a and 901.

I theorise that this is for using the card reader to emulate the xp cd or something.

---

### Post by gewitty on 2010-06-17
Yep. That was it. Works fine now.

Thanks for the tip.

---

### Post by dranoweb on 2010-06-17
No probs, took me a little detective work to figure it out, but glad I could solve someone else's issues as well.

---

### Post by kgarbutt on 2010-06-17
See if you can turn it on through the BIOS.

---

### Post by dranoweb on 2010-06-17
In my experience, it was turned on in the bios, but there is a setting "os status"
 
this needs to be set to "finished" not "start"
 
this causes the sd reader to appear ad a cd rom in ubuntu.

---

### Post by uBuddhu on 2010-08-17
I was having this problem, too. I was about to post, but a post led me  to wonder about an error when I clicked on Places->Computer (Nautilus  cannot handle computer: Locations)

The recommended course of action for that was:

> sudo mv /usr/local /usr/local.old
> sudo mkdir /usr/local
Reboot.

Lo and behold, after the reboot, my SD was appearing again and my new  MP3 player was also. Hope this fixes someone else's problems, too.

---

### Post by kuh0005 on 2011-05-08
I have this problem,too ... I tried solve it change status Os on finished but it doesn't work ... Do you know about another solution of this problem 


(I have asus eee 900; Ubuntu 10.10.  and SDHC card adata class 10 16gb)

also,.. I tried:

blazej@blazej-900:~$ dmesg | tail -n 20
[27210.497160] sd 2:0:0:0: [sdb] Add. Sense: Medium not present
[27210.497172] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 01 ed f7 f0 00 00 08 00
[27210.497192] end_request: I/O error, dev sdb, sector 32372720
[27210.497202] Buffer I/O error on device sdb, logical block 4046590
[27210.499622] sd 2:0:0:0: [sdb] Device not ready
[27210.499629] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[27210.499638] sd 2:0:0:0: [sdb] Sense Key : Not Ready [current] 
[27210.499647] sd 2:0:0:0: [sdb] Add. Sense: Medium not present
[27210.499659] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
[27210.499678] end_request: I/O error, dev sdb, sector 2048
[27210.499686] Buffer I/O error on device sdb, logical block 256
[27210.505556] sdb: detected capacity change from 16574840832 to 0
[27290.672717] 2:1:1: endpoint lacks sample rate attribute bit, cannot set.
[27293.876702] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[27849.152781] sd 2:0:0:0: [sdb] 32372736 512-byte logical blocks: (16.5 GB/15.4 GiB)
[27849.155880] sd 2:0:0:0: [sdb] Write Protect is off
[27849.155892] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[27849.155899] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[27849.158477] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[27849.158496]  sdb: sdb1

---

