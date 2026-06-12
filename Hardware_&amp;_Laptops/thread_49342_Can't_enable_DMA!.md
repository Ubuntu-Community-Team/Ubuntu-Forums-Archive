---
title: "Can't enable DMA!"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by Blue1k on 2005-07-15
Hi, I am having troubles enabling DMA. I tried adding this to hdparm.conf:

/dev/hdc {
dma = on
}

But when Nero starts it says to enable DMA. 

Then I tried:

karl@home:~$ sudo hdparm -d1 /dev/hdc
Password:

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
karl@home:~$

Help! I have never seen this before.

Thanks!!

---

### Post by Blue1k on 2005-07-16
I figured it out myself by looking through some Ubuntu forum archives. Basically have to add this to module file in /etc first:

Add amd74xx to your /etc/modules file before ide-cd (for Nforce)
Reboot and then do the hdparm command.

 :smile:

---

### Post by Blue1k on 2005-07-19
Here is an interesting question for a smart person:

DMA keeps turning off for my optical drives after every reboot. I hate having to do the hdparm command every time I reboot. Any ideas why this happening and what I can do to get DMA to stay on permamently?

Thanks!

---

### Post by ounn on 2005-07-19
Try puts thise lines at the end of  /etc/hdparm.conf

```
/dev/dvd {
dma = on
}

```

Probably at the boot you get a worning that /dev/dvd dont exists but just ignore him.

ounn

---

### Post by entangled on 2005-07-19
[QUOTE=ounn]Try puts thise lines at the end of  /etc/hdparm.conf

```
/dev/dvd {
dma = on
}

```

Probably at the boot you get a worning that /dev/dvd dont exists but just ignore him.

ounn[/QUOTE]
 Just in case it helps I fixed this one on my system by adding the line
hdparm -d1 /dev/hdc

to the file
/etc/init.d/bootmisc.sh

Then my hdc drive is set to dma during boot.

---

### Post by Blue1k on 2005-07-19
Thanks!! :)

---

