---
title: "DVD playing problems (SATA)"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by nat on 2005-05-09
I have big problems with playing DVD's on a box with SATA.
When trying to play the dvd, totem/mplayer/xine freezes and the prosess cannot be killed (even not with kill -9). I tried turning off dsub-1 but the same thing happens. I cannot umount the dvd because of the process.

 I have tried different libdvd* libs from marillat, both from stable and testing. 

I think that it could have something to do with the SATA driver, ata-piix. The dvd/cdrom is read as a scsi device, /dev/scd0

Here are som output from dmesg:
```
Buffer I/O error on device sr0, logical block 20700
SCSI error : <0 0 0 0> return code = 0x8000002
Current sr0: sense key Medium Error
Additional sense: L-EC uncorrectable error
end_request: I/O error, dev sr0, sector 82804
Buffer I/O error on device sr0, logical block 20701
SCSI error : <0 0 0 0> return code = 0x8000002
Current sr0: sense key Medium Error
Additional sense: L-EC uncorrectable error
end_request: I/O error, dev sr0, sector 82808
Buffer I/O error on device sr0, logical block 20702
SCSI error : <0 0 0 0> return code = 0x8000002
Current sr0: sense key Medium Error
Additional sense: L-EC uncorrectable error
end_request: I/O error, dev sr0, sector 82812
Buffer I/O error on device sr0, logical block 20703
atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_200211181742', timestamp 2002/11/19 00:35 (1078)
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_200211181742', timestamp 2002/11/19 00:35 (1078)
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD_200211181742', timestamp 2002/11/19 00:35 (1078)
atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'I_ROBOT_SPECIAL_EDITION_DISC_1', timestamp 2004/10/12 03:49 (1078)
ata1(0): WARNING: zero len r/w req

```

Does anyone have any idea what I can try now? I'm stuck. Thanks!

---

### Post by soulestream on 2005-05-09
im having the same problem also. It only crashes on certain DVDs.

I also am on a sata


soule

---

### Post by bubblegum on 2005-05-11
see if you have DMA enabled with hdparm -I

if not try to enable it with hdparm -d1.

if it complains it can't enable it , try moving chipset module at the beginning
in /etc/modules before (ide-*) module (for me the chipset module was piix), and retry hdparm -d1

You'r problem might not be at all related to DMA though

---

### Post by soulestream on 2005-05-14
i didnt think you could enable DMA on a SATA drive. 

Ill do some research


soule

---

### Post by c0rderr0y on 2005-08-22
I'm in the same boat ever get this working?

---

### Post by flip on 2005-09-20
I'm having the same problem with my DVD's on sata as well. DMA isn't an issue here (though I wish it was). This thread's pretty old so if anyone is monitoring and has had success in this area plz reply.

I've tried Totem as well as Ogle, both hang with 80% of my DVD collection and cannot be killed. The drive even quits and won't respond to eject commands or even the manual button on the front of the drive which probably is a bad thing.

Thanks,

- flip

---

### Post by c0rderr0y on 2005-09-21
I had the same problem before but i fixed it. Not sure if this was the excat commands because I'm not at home right now but here goes.

sudo apt-get install regionset
(or was it setregion)

then run "regionset" or the latter.

---

