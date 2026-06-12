---
title: "Cannot enable DMA on Pata drive"
date: 2008-09-07
forum: Hardware
---

### Post by chopsuwe on 2008-09-07
I have installed Heron and after much searching I still cannot enable DMA on my hard drive. Both the drive and board support DMA and function perfectly in WindowsXP. At this point Ubuntu is unusable as it is taking over a minute to switch tabs in Firefox, something Windows does instantly. 

Please explain how to get this working giving as much detail as possible as I am new to Ubuntu.

Specs 
Duron 750MHz
512 Ram
MS-6390 Board with VIA KM266 & VT8235 chipset.
Integrated ProSavage8 graphics.
IDE controller onboard VT8235 chipset supporting Ultra DMA 66/1006133
20GB Seagate Baracuda PATA 

```
xxx@Ubuntu:~$ sudo hdparm -v -d1 /dev/sda
[sudo] password for xxx: 

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 2434/255/63, sectors = 39102336, start = 0
bob@Ubuntu:~$ 

```

---

### Post by chopsuwe on 2008-09-09
Anyone?

---

### Post by amo-ej1 on 2008-09-09
could you paste the output of hdparm -I /dev/sda ?  It should contain a line like:

On my sata laptop:
"	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
"

On my pata desktop:
"
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
"

This lists the supported modes, the one marked with the * is the one which is currently active.

---

### Post by chopsuwe on 2008-09-10
So if it is running in udma5 why is it so slow? Previously I had Ubuntu 7 installed. Rating speed and responsiveness on a scale of 1-10 WinXP is a 10, Ubuntu 7 was 8 and Heron is a 2. What would be causing this?

```

DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns

```

---

### Post by amo-ej1 on 2008-09-10
To measure your disk throughput you could use: 

```

edb@lapedb:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2378 MB in  2.00 seconds = 1189.01 MB/sec
 Timing buffered disk reads:  106 MB in  3.03 seconds =  34.94 MB/sec

```


Which means that on my laptop i can read at a rate of 1189 MB/sec from memory and at a rate of 34.94 MS/sec from disk.

How did you identify your bottleneck to be your disk ? It could as well be the health of your disk which is degrading. 

If you install smartmontools you could read the  S.M.A.R.T. data stored on your disk using 

```

edb@lapedb:~$ sudo smartctl -a -d ata /dev/sda

```

Check if you don't see any odd values there which might indicate a failing disk.

---

### Post by dentharg on 2008-09-10
Can "Inappropriate ioctl for device" suggest that module for motherboard is not loaded?

---

### Post by amo-ej1 on 2008-09-10
He's having rather lot interaction with the device for lacking a driver. It means what it says it means, that the driver doesn't support the ioctl issued.

---

### Post by chopsuwe on 2008-09-16
I don't believe the drive is faulty as it is only Ubuntu 8 that runs this slowly. WindowsXP runs nice and fast and Ubuntu 7 runs a little slower than windows. 

For some reason I could find Smartmontools in package manager but it wouldn't download. 

```

xxx@Ubuntu:~$ sudo hdparm -tT /dev/sda
[sudo] password for xxx: 

/dev/sda:
 Timing cached reads:   360 MB in  2.00 seconds = 179.82 MB/sec
 Timing buffered disk reads:   48 MB in  3.00 seconds =  15.98 MB/sec

```

The reason I suspect it is the hard drive driver is from the message "HDIO_GET_DMA failed: Inappropriate ioctl for device". Also the symptoms are consistent with a missing or bad driver in Windows. 

The symptoms are:
When more than about 3 windows are open it can take over 3 seconds to swap between them. 
In firefox opening a link in either a new tab or new window will lock up the machine for 30 seconds or more. 
General feeling of sluggishness. Programs seem to run fine on their own but it feels like the mouse and monitor are full of treacle.

---

### Post by amo-ej1 on 2008-09-16
Yes, but you can see that it's not only the read from disk which is slow, it's also the cached read which is extremely slow (meaning reading from RAM).

---

### Post by chopsuwe on 2008-09-17
I've run the memory test program on the live cd and the ram checks out fine. 

Would I be right in thinking it must be a problem with the motherboard drivers?

Link to the manufacturer's web site in case it is needed.
[http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=307](http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=307)

---

