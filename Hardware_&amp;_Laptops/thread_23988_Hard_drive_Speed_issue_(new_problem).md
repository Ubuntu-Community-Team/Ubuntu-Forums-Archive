---
title: "Hard drive Speed issue (new problem)"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by vnbuddy2002 on 2005-04-04
I am running Hoary 5.04 RC (fresh install). I am experience some issue with file copying. When I try to start to copy a large file, it copy very fast at start, but then the speed dropped down to ~2-3Mb/sec.

Can anyone tell me what went wrong?

I had DMA enabled (HDPARM) for all of the drive.

Output:

```
root@localhost:/home/kenny237/iometer-2004.07.30/src # hdparm -t /dev/hda /dev/hdf

/dev/hda:
 Timing buffered disk reads:   86 MB in  3.06 seconds =  28.13 MB/sec

/dev/hdf:
 Timing buffered disk reads:    6 MB in  4.16 seconds =   1.44 MB/sec
```

---

### Post by vnbuddy2002 on 2005-04-04
Very strange behavior. It runs fast for awhile then slow dow like it runs with DMA turned off.

I had to 

hdparm -d1 /dev/hda
....
....
hdparm -d1 /dev/hdf

every single time. Can you tell me what can possibily caused the problem?

---

### Post by Pse on 2005-04-07
You may want to check some logs, as it looks like your IDE controller is downgrading to PIO due to some error. What chipset do you have? what do your syslogs show? what HD do you have? Are the cables OK?

---

### Post by shakin on 2005-04-08
[QUOTE=vnbuddy2002]
```
root@localhost:/home/kenny237/iometer-2004.07.30/src # hdparm -t /dev/hda /dev/hdf

/dev/hda:
 Timing buffered disk reads:   86 MB in  3.06 seconds =  28.13 MB/sec

/dev/hdf:
 Timing buffered disk reads:    6 MB in  4.16 seconds =   1.44 MB/sec
```[/QUOTE]

Those numbers look slow. What drive reads at 1.44 MB/sec? My SATA drive is 51 MB/sec and your IDE shouldn't be that much slower. What kind of drive is /dev/hdf?

Try this benchmark: $hdparm -tT /dev/hdf
It should show cached reads as well.

What's the output of $hdparm -i /dev/hdf?

---

### Post by vnbuddy2002 on 2005-04-08
It was an error in HDPARM that "time out waiting for /dev/hdf" and it randomly happen. But it occurs more frequent when I try to copy large files. I had to remove HDPARM and enable the UltraDMA mode in the BIOS, which basically giving me the save result as DMA=on ( ~56mb/sec )

Filesystem for /dev/hdf = ReisferFS

---

### Post by valrond on 2005-04-08
I have the very same problem in one of my 3 disks. It woked like a charm under windows XP, but now it is slow as hell, it goes at full speed like 0.1 secs then gets slow, fast again, then slow.

I have tried to enable the dma, but i get the following error:

/dev/hdb1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma    =  0 (off)


I can't turn it on the Bios either (auto or off)
The board is a DFI NF3 Ultra 250GB, and all of the disks are Seagate 7200.7, 200 GB

Can you give me a hand?

---

### Post by vnbuddy2002 on 2005-04-08
I would suggest you remove the HDPARM
-
Let try it with out HDPARM before you remove the hdparm and see if it does anything.

sudo /etc/init.d/hdparm stop


Then try to copy files again and see if you still experience the same problem. If it copies all the files without delays. Then you should remove HDPARM

sudo apt-get remove hdparm

Good luck!

---

### Post by valrond on 2005-04-09
[QUOTE=vnbuddy2002]I would suggest you remove the HDPARM
-
Let try it with out HDPARM before you remove the hdparm and see if it does anything.

sudo /etc/init.d/hdparm stop


Then try to copy files again and see if you still experience the same problem. If it copies all the files without delays. Then you should remove HDPARM

sudo apt-get remove hdparm

Good luck![/QUOTE]

I've done both things, didn't change anything. The thing is that the drives are perfect. I just installed Mepis in that drive and it goes smooth, hdparm informs of 60 MB/s, instead of 3.80 MB/s that I get under ubuntu. If I can't solve this I'd had to say goodbye to ubuntu, it isn't worth using just 1 of the 3 drives.

---

### Post by valrond on 2005-04-09
I have found a solution searching the forums, but it was a dma problem with cd a dvd drivers

The solution is adding:

amd74xx

to /etc/modules

---

### Post by Perfect Storm on 2005-04-14
[QUOTE=shakin]Those numbers look slow. What drive reads at 1.44 MB/sec? My SATA drive is 51 MB/sec and your IDE shouldn't be that much slower. What kind of drive is /dev/hdf?

Try this benchmark: $hdparm -tT /dev/hdf
It should show cached reads as well.

What's the output of $hdparm -i /dev/hdf?[/QUOTE]

Isn't that bit low for SATA?

I'm running ATA133 and get:

Timing cached reads:   2300 MB in  2.00 seconds = 1149.03 MB/sec
 Timing buffered disk reads:  180 MB in  3.01 seconds =  59.81 MB/sec

---

