---
title: "partition anger. ANGER!"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by nickstatus on 2007-01-08
ppph. My wife needs windows for school (I know, I know), thus I need to get off the ubuntu train temporarily. my problem lies in trying to save my precious data. I have 17 gigs of stuff I want to keep. I tried to make a FAT32 partition to keep it safe from the destructive windows installation process, but ubuntu for some reason refuses to mount this partition. It gives me a "cannot mount device" type heading, with a "device not removeable" type message. Also, the icon for the drive is a cd-rom type icon, not a hd type icon. Any one have any suggestions? a different partitioner maybe? Im all ears (i guess its all eyes for this internet type stuff). 
](*,)   lol thats cute

oh yeah, this is tha dapper drake!!! I got off that edgy eft nonsense when my box broke///

---

### Post by kj1h234lkj1234 on 2007-01-08
Just so we're all on the same page:

Applications->Accessories->Terminal

And post the output of these 2 commands:

```
sudo fdisk -l
```

```
df -h
```

---

