---
title: "Data recovery from hit external hard disk"
date: 2012-07-20
forum: Hardware
---

### Post by Friwise on 2012-07-20
Hello everybody!!!

I tried to solve this issue reading other similar posts but I think my problem is quite different. In any case, I apologise if this has already been discussed somewhere in the huge space of the forum and I would happily follow any link there.

I have a Toshiba STOR E 1.5 TB that has fallen after the happy attack of my brother's dog. The machine fell down on the floor and after that whenever I tried to plug it in, in the first seconds it makes that annoying sound that in general means that it is damaged. It does not appear on my desktop at all.


In terminal when I give the command **lsusb** it gives me that

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 006: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 007: ID 0930:0b09 Toshiba Corp. PX1396E-3T01 External hard drive
```Then... using Log File Viewer I get this picture that I attach you

Do you have any idea what shall I do to recover my files and save them somewhere else? 
Thanks in advance!!!

---

### Post by Wim Sturkenboom on 2012-07-20
You can try a data recovery program (like testdisk / photorec). And if successful, you can throw the HD away.

---

### Post by TheFu on 2012-07-20
Grinding noise from a HDD is never a good sign. Every time you try again, it grinds more data off the physical platters.  If you don't think the noise is coming from spinning (which is unlikely), then you might try to rebuild all the drive electronics with by purchasing another HDD of the same model and swapping the controller electronics.  I've never tried this.

There are professional data recovery houses that will disassemble the drive and replace the broken parts. Hopefully, the platters aren't damaged too much. This service is expensive.  I think the going rate is US$2500-3000 and even then, it sounds like this data has been scraped away already.

Once I dropped a spinning USB 1TB HDD off the top of a tower PC. Fortunately, it was 2 days old and didn't have any real data on it. That disk never worked again, I drilled 3 holes through it and tossed it into the garbage. Drilling those holes was fun and ensured that pretty much none of the data would be useful to anyone.

If the HDD isn't making unexpected noises, you might try either **ddrescue** or **dd_rescue**.  I've used both with success in getting data back from failing optical media combined with par2 files to fill in the unrecovered data.  A commercial tool, **spinrite** can get data back due to *lazy bits*. I've used this tool as well, but if the HDD is making bad noises, spinrite will do more damage than good.

It would be much easier if you just restored from that data backup you've been making religiously every week to a new HDD, right?  rdiff-backup or duplicity or duplicati or deja-dup are great programs, BTW.

Sorry to have such bad news.

---

### Post by Friwise on 2012-07-20
I followed some advices and found out the photorec command. 
So... it looks like I can find the files (or at least I hope) since with > sudo photorec it can see the disk.

I want to ask if it is possible to choose what files I want to recover, in order to not need to buy such a huge hard disk to save all the content.

Is it possible to just see, in first place, the content of the hard disk and choose what to save?

Thanks in advance.

---

