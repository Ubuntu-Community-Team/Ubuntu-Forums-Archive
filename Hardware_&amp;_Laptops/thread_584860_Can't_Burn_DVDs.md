---
title: "Can't Burn DVDs"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by janko on 2007-10-21
Hi all, has anyone a solution for my problem? I cannot burn DVDs. In windows it works so i don't think it is a hardware problem. Does anyone know what should I do?

Janko

---

### Post by Perpetual on 2007-10-21
Which Version of Ubuntu?  What app are you using to burn with?  What happens?  Anything?

---

### Post by janko on 2007-10-21
I use gutsy but it has been a long time that I use ubuntu and  I always had this problem.
I've tried Gnomebaker and Brasero, in both cases I am able to burn, it takes some time but at the end I can't mount the DVD.
It happens only with DVD burning, CDs works well.

---

### Post by cpauquez on 2007-10-22
I had the same trouble. I have a Dell Inspiron 8600, with a NEC N6500-A optical drive. 
I googled about this and I found that may be firmware trouble. 

I downloaded NEC official firmware update, but it's built for MS-Windows. Then, I visit this link [http://binflash.cdfreaks.com/#download](http://binflash.cdfreaks.com/#download)... and I read docs, and I applied the new firmware.

The steps:

1. Probe your DVD hardware:
```
cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: HTS726060M9AT00  Rev: MH4O
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: [COLOR="Red"]_NEC[/COLOR]     Model: [COLOR="Red"]DVD+-RW ND-6500A Rev: 202C[/COLOR]
  Type:   CD-ROM                           ANSI  SCSI revision: 05

```

2. Go to [http://binflash.cdfreaks.com/#download](http://binflash.cdfreaks.com/#download)  

3. If you are on Linux (I'm Ubuntu Gutsy), Select the "Linux (i386)" link. A popup window will opened in your internet browser. Click over download link. You must decompress that tar.gz file.

4. Visit [http://liggydee.cdfreaks.com/page/en/](http://liggydee.cdfreaks.com/page/en/) and select & click a link for your DVD drive model. A popup window will appear again. Click over download link. You must decompress that zip file.

5. Finally, go to your download directories:
```
 sudo ./necflash -flash 224_orig/224_orig.bin /dev/sg1
```

224_orig.bin it's for my NEC DVD drive, yours may be different.

These steps resolve my trouble. I hope yours too...

Regards.

PS: Excuse my english.

---

