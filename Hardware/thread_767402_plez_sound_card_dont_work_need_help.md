---
title: "plez sound card dont work need help"
date: 2008-04-25
forum: Hardware
---

### Post by tropcky on 2008-04-25
hi 
when i was useing 7.04 and 7.10 i had the same problem that is the sound card dont work  and 2 fix it i do restart  and it wroks 

now i am using ubuntu 8.04 the sound dont wanna work and some times after like 5 restart  its works   just in system sound like log in  but still dont work with midea even after i install the right codacs the song work but no vois 

i have a realu old creative card 32  and i cant change it at thes time 

any help plez

---

### Post by tropcky on 2008-04-26
plez guys i have no sound   and i hate 2 use windows agen

---

### Post by inhalentbroom on 2008-04-26
Have you tried running alsamixer and making sure that your speakers aren't muted?

If that doesn't work, try running

```
lspci
```

and see if Ubuntu detects your soundcard.  Also, if you could post the output of the above command, that might help us figure out what is wrong.

---

### Post by tropcky on 2008-04-27
thank u 
here is is the post of lspci 

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)

---

### Post by tropcky on 2008-04-27
any help guys plez

---

### Post by tropcky on 2008-04-27
any help guys plez

---

### Post by tropcky on 2008-04-29
oky guys i just removed it i gess 7.10 is the best antel now

---

### Post by tropcky on 2008-05-01
i sm sorry but i am just upgrade it to 8.04 agen   plez guys help the same problem

---

