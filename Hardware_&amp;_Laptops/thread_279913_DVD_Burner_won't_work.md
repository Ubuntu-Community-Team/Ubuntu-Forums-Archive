---
title: "DVD Burner won't work"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by TorchlightJay on 2006-10-18
Okay so I just assembled a Core 2 Duo notebook and I have Ubuntu 6.06.1 on it. This is my first DVD Burner I've ever had and it's giving me some real problems. A friend informed me that they should work right out of the box but mine doesn't. It recognizes CDs with no problem. It also appears to read DVDs without problem. It can't burn CDs nor can it burn DVDs. I am an avid k3b user and am in Kubuntu if that makes a difference. When I open a blank DVD or CD it says, Malformed URL. It looks like it is mounted as scd0. K3B tells me that CDrecord doesn't have permission to access media. Does anyone know what is wrong?

---

### Post by ixus_123 on 2006-10-18
I'm currently also having this problem.

First thing to check is if DMA is enabled.  Open up a terminal & type

```
sudo hdparm /dev/hdc
```
where hdc is your CD drive - it might be different on your laptop

You should get something back like this
```
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

```

If DMA is off - as it is in my case then you need to type the following command to turn it on.

```
sudo hdparm -d1 /dev/hdc 
```
This will switch DMA on - however on writing out this I noticed that it's not persistant.  Seems my DMA has managed to switch itself back off - not sure how to fix this - perhaps editing a config file somewhewere?

Hoping for someone else to interject now. . .

---

### Post by ixus_123 on 2006-10-19
Anyone?

---

### Post by TorchlightJay on 2006-10-19
Well I am getting somewhere. My device is /dev/scd0. I don't have an hdc in my /dev but I have a dvd and dvdrw. I saw some change in that I didn't get an error message in relation to not finding the drive but it wouldn't burn because of a speed error. it couldn't set speed then like 2 seconds later it said DVD was successful. Also, I cannot open CDs and view their contents in konqueror. It is weird. Data DVDs I can, like I have a SUSE 10.0 DVD lying around that it can read, but asie from that, nothing. Any ideas?

---

