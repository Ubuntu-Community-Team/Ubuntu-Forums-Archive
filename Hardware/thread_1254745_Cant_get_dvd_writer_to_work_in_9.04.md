---
title: "Cant get dvd writer to work in 9.04"
date: 2009-08-31
forum: Hardware
---

### Post by scimitar123 on 2009-08-31
Ok, I'm quite new to Ubuntu and I've had several teething problems, but all of them  so far I've sorted without any help. However, this one has me stumped! Basically I have 2 dvd drives (one just a reader and one a writer). The reader is a Pioneer and the Writer a plextor. The Pioneer works fine, no problems. The Plextor is visible but doesn't work. If i put anything in the drive it spins but i can't open the media. I get messages about no media in drive etc. In the Pioneer its all fine!

If I try to burn a CD or DVD this doesn't work either. I installed the OS from this drive and it works fine in windows, so I wondered if anyone could shed any light on why this is not working and how I can get it to work?!

Thanks for your time.

Alan

---

### Post by scimitar123 on 2009-09-01
*bump*

---

### Post by scimitar123 on 2009-09-05
For the benefit of anyone having teh same problem. For what ever reason the cd drive was not in FSTAB:

```
   Status: Open => Answered

actionparsnip proposed the following answer:
run:

sudo mkdir /media/cdrom1

then run:

gksudo gedit /etc/fstab

and add this line:

/dev/scd0 /media/cdrom1 iso9660,udf user,noauto,exec,utf8 0 0

save the new file and reboot


```

---

### Post by stinger30au on 2009-09-05
i had a similar fault last week with an old LG drive

i tried it in another pc and it was knackered so i replaced it and everything is all good now

---

