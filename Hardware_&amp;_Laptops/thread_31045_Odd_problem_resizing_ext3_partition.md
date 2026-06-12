---
title: "Odd problem resizing ext3 partition"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by Spyd on 2005-05-01
So i discovered I had outgrown my partiton that Ubuntu was installed in.... Sooooo I fired up my live Knoppix CD with the noswap option and used QT parted to manage my partitions, this is in a laptop and so there is only one drive, same old limitation of 4 primary partitons. At any rate, I nuked my hda1 windows partiton and then made a new one and made it fat32 but smaller, i then used partimage to back up my ubuntu partition over the network, deleted the ubuntu partition and made a new partion for ubuntu of about 15 gig, then restored my partition data (5g) over the network into my new partiton. 

I then booted ubuntu and fired up diskusage and it showed me the same 599 megs free. WTF? so i fired up qtparted and examined the disk, it showed a 15gig partiton with 5 gig used. so I dropped to a shell and fired up parted and it shows:
```
Minor    Start       End     Type      Filesystem  Flags
1          0.031   4086.848  primary   fat32
2       4086.848  18998.745  primary   ext3
3      28184.348  28937.395  primary   linux-swap
4      28937.395  38146.530  primary   ntfs        boot

```

part 1 is a common file area for both my windows xp gaming partition (part 4) and my Ubuntu Hoary (part 2) 


Further investigation, using cfdisk:
```

cfdisk -P t /dev/hda

         ---Starting---      ----Ending----    Start     Number of
 # Flags Head Sect Cyl   ID  Head Sect Cyl     Sector    Sectors
-- ----- ---- ---- ---- ---- ---- ---- ---- ----------- -----------
 1  0x00    1    1    0 0x0B  254   63  520          63     8369802
 2  0x00    0    1  521 0x83  254   63 1023     8369865    30539565
 3  0x00  254   63 1023 0x82  254   63 1023    57721545     1542240
 4  0x80  254   63 1023 0x07  254   63 1023    59263785    18860310

```

looking in qtparted: it shows I have 4.78 gig used in a 14.56 Gig partition

So now i am unable to use this extra space, How can I fix this, I have been all over the forums and the net but have not found a resoluion.

Thanks for any and all help
Spyd

---

### Post by nad on 2005-05-01
Your image contained a 4.78G file system. This is what you got. Just use QTparted to resize your partition and file system to its' available space.

---

### Post by Spyd on 2005-05-01
Hiya Dan, for some weird reason, I was unable to use the resize function in my QTparted, in either ubuntu or off the live knoppix 2.7 cd, the resize option is greyed out, but catching the drift of your suggestion, I used parted to enlarge the partition by a few megabytes and PRESTO! I have my full 10 gigs of free space :)

so for folks searching for a solution, this thread has the answer: 

resize ext3 partition in ubuntu !

Thanks man!!!!
Spyd

---

