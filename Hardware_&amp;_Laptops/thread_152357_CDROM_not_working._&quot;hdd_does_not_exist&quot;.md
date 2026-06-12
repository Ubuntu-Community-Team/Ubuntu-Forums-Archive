---
title: "CDROM not working. &quot;hdd does not exist&quot;"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by weasel fierce on 2006-03-29
I have 2 CDROM drives. For reasons I cant figure out, one of them (the burner) no longer works. If I put in a CD, it doesnt do anything. 
If I go to Places and My Computer, there's an icon, but clicking on it gives this error:
> mount: special device /dev/hdd does not exist

Trying to mount it using the terminal doesnt do anything either.

What did I do, and (more importantly) what can I do to fix things ?

---

### Post by roachk71 on 2006-03-29
Which IDE bus are you installing the drive on, and do you have the jumpers set appropriately (ie. on the secondary IDE bus, these drives should be jumpered as secondary master and secondary slave.)

If, however, you have one of these drives on your primary IDE channel, that one should be configured as the slave, and the other drive (on the secondary bus) should be set as master.

Also, a note of caution: If you have one of these drives on the primary IDE channel with your boot hard disk, the bus will be limited by the slowest command queue.

---

### Post by weasel fierce on 2006-03-29
They're set up on the secondary one. I'll check the jumpers, if they may have been nudged, when I had the computer open recently, though both drives had been working fine untill not too long ago.

---

