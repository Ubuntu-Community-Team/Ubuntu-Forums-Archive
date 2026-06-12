---
title: "Hard Disk identification"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by ianmillington on 2006-08-29
Hi

Dell Inspiron 630m running dapper (kubuntu).

My hard drive partitions are all shown as /sda which I read somewhere (although I can't remember where) is wrong.

Is this correct please and, if so, how do I fix it?

Thanks

Ian

---

### Post by Omnios on 2006-08-29
Can you be a bit more specific. What do you mean named, as in the name in my computer. With gnome the drive name shows as the same name where you are monting the partition. So say I have a document drive named documents because the folder it is mounted to is named documents

---

### Post by atomkarinca on 2006-08-29
no, sda just means it's a scsi drive (first scsi drive actually). hdx's are ide drives, that's all.

---

### Post by ianmillington on 2006-08-30
Hi

Thanks for the replies. Basically the laptop is pretty new (3 months old). On my previous machine, the partitions (Windows, data, and linux & swap partitions) were all prefixed with hda. I believe the drive was an ide drive so from what you say hda was right for that machine.

The one in the Dell is a SATA drive. I recall I gotthe quick one, running at 7200rpm. Is sda the right designation for the partitions in this case? Also, will the default setup in dapper tend to be correct for this machine, as I am a bit nervous messing about with hdparm settings!

Thanks for the replies

Ian

---

### Post by atomkarinca on 2006-08-30
the sata doesn't play a role in designation AFAIK. sda just means that it's a scsi disc. i'm sure dapper will install with no problem :)

---

