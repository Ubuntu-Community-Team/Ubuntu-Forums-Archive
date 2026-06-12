---
title: "esata problems on 9.10"
date: 2010-02-28
forum: Hardware
---

### Post by lbloy on 2010-02-28
I recently got a acer aspire revo, and a starTech external raid enclosure. I'm having problems using the esata port to connect the 2.

The hardware on the aspire is the nvidia ion motherboard and the raid card in the enclosure is a Silicon Image SIL5744.  

lbloy@Shiota:/media$ lspci
...
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
...

on connecting the esata drive the following appears in dmesg

[141761.257468] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
[141761.257478] ata1: irq_stat 0x00000040, connection status changed
[141761.257487] ata1: SError: { PHYRdyChg CommWake DevExch }
[141761.257501] ata1: hard resetting link
[141762.144035] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[141762.144084] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[141767.150907] ata1: hard resetting link
[141767.644056] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[141767.644120] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[141767.644130] ata1: limiting SATA link speed to 1.5 Gbps
[141772.644030] ata1: hard resetting link
[141773.128035] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[141773.128083] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[141778.128044] ata1: hard resetting link
[141778.612034] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[141778.612060] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[141778.612068] ata1: irq_stat 0x08000000, interface fatal error
[141778.612079] ata1: EH complete


googling around has shown others with this problem but no suggested solutions.

Any help would be greatly appreciated.

-Luke

---

### Post by lbloy on 2010-03-05
I recently tried on the lucid beta live cd and the problem persists.

luke

---

### Post by bluelamp999 on 2010-03-05
I had a similar problem - [http://ubuntuforums.org/showthread.php?t=1088093](http://ubuntuforums.org/showthread.php?t=1088093)

I know it isn't much help but it seems to me that eSATA has been 'broken' since the 8.10 kernel, it used to 'just work' with 8.04.

---

### Post by bazzeruk on 2010-03-23
Has anyone found a solution to this problem ?
 
I have a Startech external raid enclosure and it fails to work with my Acer Revo when connected via eSATA
 
Another eSTATA drive (not raid) works fine with the Revo and the Startech enclosure works fine on eSATA when connected to my workstation.
 
It really is driving me up the wall !!!
 
Thanks
 
Bazzer

---

### Post by AndrewCRMartin on 2010-05-18
I have exactly the same problem on a Revo running Fedora 12 - Startech dual drive RAID1 works fine on another machine but won't work on the Revo. 

Any suggestions gratefully received!

Andrew

---

### Post by NickD-NLUG on 2010-09-21
With apologies to all of you hoping this is a solution... can I just add myself to the list of people with an Acer and an eSATA enclosure and the:

"ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)"

error.

---

### Post by jyeh on 2011-05-09
i too am having the same problem and have an Acer Revo (AR1600-U910H).  I know the eSata enclosure (Sans Digital TR4M) works since it was working when plugged into my Debian Lenny machine (which had no graphics drivers at all).  I think the issue might be related to the nVidia drivers:
[http://ubuntuforums.org/archive/index.php/t-1037819.html](http://ubuntuforums.org/archive/index.php/t-1037819.html)


Strangely enough, I stopped gdm but that doesn't seem to resolve my issue.

Any ideas?

---

