---
title: "Ibm/Lenovo T61 Thinkpad and AHCI"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by Barleyman on 2007-10-18
Hi All,

Just installed Gutsy on a new IBM T61.  Once I changed the SATA to "compatibility mode" instead of AHCI in the BIOS, I could install everything with no problems.   (Much easier than Feisty to get all hardware supported).

My problem is when I try to reset the BIOS to AHCI mode, Ubuntu hangs on bootup and eventually drops to a busybox shell.   I would like to be able to run in AHCI mode, because vista seems less stable when running compatibilty mode.

Any help would be greatly appreciated.  

Intel Core Duo 2 T7300 
IBM/Lenovo T61 Thinkpad

---

### Post by nikko_bosatsu on 2007-10-18
Hi All,

I got same problem here for my T61, everything else works perfectly fine ( Except for the wireless led). 
Here the message that i got, before the boot process stop

```

ata3: SATA link up 1.5Gbps (Sstatus 113 Scontrol 300)
ata3.00:qc timeout (cmd 0xec)
ata3.00:failed to IDENTIFY (I/O error, err_mask=0x4)
ata3.00:limiting speed to UDMA7 : PIO5
ata3:port is slow to respond, please be patient (status 0x80)
ata3:COMRESET failed (errno:-16)

```

Thanks .....

---

### Post by jaskah on 2007-10-28
hi
when you write "everything else works perfectly fine" does this also refer to waking the computer from suspend (my t61 will not wake from suspend).
if this works for you, then how did you get it to work?
thanks for your help!

---

### Post by nikko_bosatsu on 2007-10-30
Well I'm not try the suspend thing on my T61, I mean with work perfectly fine, I can my Ubuntu to work on windows environment without having to boot to Windows, as long I can use my Ubuntu at my work place. But I'll try the suspend thing at my T61, and I'll inform the result.

---

### Post by jaskah on 2007-10-31
thanks for your answer and looking forward to hearing if your t61 will wake from suspend.

---

