---
title: "lightscribe HP DVD640i BENQ1625"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by Motomouse on 2005-04-25
Hi, I am interested in the lightscribe technology. A greyscale label is burned by the DVD-Writer on special media CDs and DVDs. 

I sent an email to HP Presales and to my disbelief was informed that HP DVD640i is not compatible with Linux. While I am aware that currently no solution exists to burn labels with this drive under GNU/Linux, i would like to know if the drive really does not work under Linux at all. I think thats not true, anyway a BENQ 1625 DVD-writer is working fine in my Ubuntu Box and I dual boot Windows to burn the labels.

Please post your experiences with the HP DVD640i, thank you very much!

Any Info on a possible lightscribe solution in linux is appreciated (HP sells Linux Notebooks after all, perhaps they change their mind about supporting lightscribe on Unix in the near future?)

Regards 
Ralph

---

### Post by gushy on 2005-08-04
Did you buy the lightscribe drive in the end?

I just got one today, haven't installed it yet but I assume that the normal functions of the drive will work under linux just fine.

Anyone else had experience of this?

---

### Post by selinium on 2005-11-22
The guys at K3B are looking to provide support for Lightscribe.
[http://k3b.plainblack.com/message-board/lightscribe-support-planned/re-lightscribe-support-planned3#o-PC9o9FQ2mb0BECNhcNWg](http://k3b.plainblack.com/message-board/lightscribe-support-planned/re-lightscribe-support-planned3#o-PC9o9FQ2mb0BECNhcNWg)

Hope this is of some use.

---

### Post by gushy on 2005-11-22
I use nothing but K3B so lightscribe support in a future release would be sweet.

---

### Post by Biohazzard on 2005-12-01
Hello all,

   I have a HP DVD640i and I have had no problems with it. it works perfectly except I can't find a label creation software for linux. I know that LightScribe don't work but for reg labels. any ideas

TIA

---

### Post by Biohazzard on 2005-12-03
**UPDATE**

Well as it turns out I was mistaken in my last post I am having a problem with my HP DVD640i drive. it will only burn at 1.9 - 2.0x. I am using K3B and in the options it detects that it will burn at 8x so is there a way I can make this burn work to its maximum speed.

---

### Post by gushy on 2005-12-04
check dma is turned on using hdparm

---

### Post by matthew on 2005-12-13
My wife's computer has a lightscribe dvd that works great for everything except the labelling thing. I hope as the technology ages a little bit that this functionality will be added later.

---

### Post by tanari on 2005-12-14
**HP dvd640i**

> 
andrei@ubuntu:~/stuff/clearlooks-0.6.2$ hdparm /dev/dvdrw

/dev/dvdrw:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
andrei@ubuntu:~/stuff/clearlooks-0.6.2$


How to enable UDMA?

---

### Post by Xsecrets on 2005-12-30
[QUOTE=tanari]**HP dvd640i**



How to enable UDMA?[/QUOTE]

hdparm -d 1 /dev/devicename

other switches
-c 1 = 32 bit disk io
-k 1 = keep settings through reboot, thought this never seems to work.
-m ?? = multicount, not sure exactly what this is, but for harddrives many say set it to 16
-u 1 = umask irq not exactly sure what this does either, but again "they" say to set it to 1 for harddrives.

I believe the only important one for optical drives is -d 1, and possibly -c 1.

---

