---
title: "New HD, more space, more headache..."
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by kristian on 2005-08-05
So here we go again a new harddrive for the system. With the new bigger drive I also got a problem. I want to have somewere to put data between gnu/linux and windows. I want to have about 100Gb "shared" space. BUT as far as I know I'm stuck with FAT32 to make read/write work for both systems, but then again I get clusters that's bigger than whales. Anyone that has a suggestion how to solve this frustrating situation.

---

### Post by Sam on 2005-08-05
Are you using the 100 Go of data both in Windows and Linux ? If not, create only a small FAT32 partition (5-10 Go) only for transferts between the two OS.

---

### Post by kristian on 2005-08-05
[QUOTE=Sam]Are you using the 100 Go of data both in Windows and Linux ? If not, create only a small FAT32 partition (5-10 Go) only for transferts between the two OS.[/QUOTE]

It's 100Gb that's shared between those two. Other than that I also have partitions for /, /home etc... in ext3. Which are the rest of the 200Gb harddrive.

---

### Post by Yagisan on 2005-08-05
[QUOTE=kristian]BUT as far as I know I'm stuck with FAT32 to make read/write work for both systems, but then again I get clusters that's bigger than whales. Anyone that has a suggestion how to solve this frustrating situation.[/QUOTE] Use ext2, see [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/) for a windows driver (I haven't actually tested this, as I don't have Windows anymore)

---

### Post by kristian on 2005-08-05
[QUOTE=Yagisan]Use ext2, see [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/) for a windows driver (I haven't actually tested this, as I don't have Windows anymore)[/QUOTE]
 Yes it seems nice. Though I wonder can it be trusted with writing on ext2/ext3 partitions I saw that this was not the default options under the installer. Anyone that has some experience of ext2fsd with ext2 or ext3?

---

### Post by kristian on 2005-08-05
I found another driver for reading/writing ext2/ext3 partitions that seems to be more promising. If anyone is interessed it's Ext2IFS and can be found [here]("http://fs-driver.org").

---

