---
title: "SD card reader problem on Thinkpad Z60"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by NNxD on 2006-07-12
Hi All.

Sorry if this was already answered somewhere else, I could not find the answer here.

I have a Lenovo Thinkpad Z60 with a built in Ricoh card reader. 

Whenever I start up Ubuntu 6.06 and have a card in the reader it works great and I can use the card reader without problems, but if I start up the computer not having a card in the reader I can't use the reader at all. Means that I can put in the card in the running system but it's not  recognized.

Any suggestions?

Thanks very much.

---

### Post by geos2 on 2006-07-13
My x60s does the same thing, it may just be that fstab needs to have an entry for the card-reader device.  I was pleased to find that it actually works!  I'll later today when I have access to the machine...

---

### Post by geos2 on 2006-07-14
I think there is some kind of bug here, when you insert the sd disk (after booting) on my x60s you get the following message in syslog

Jul 14 08:06:06 localhost kernel: [17181004.392000] mmcblk0: mmc0:4b84 S016B 14560KiB <NULL>
Jul 14 08:06:06 localhost kernel: [17181004.492000] generic_make_request: Trying to access nonexistent block-device mmcblk0 (28928)

when you boot, you can check mtab, it sets the device as:

/dev/mmcblk0p1

i don't know why this doesn't work afterwards...

---

### Post by NNxD on 2006-07-17
I had to re-install Ubuntu and now the error is a little different. 
If I start up with a SD card inside, it's recognized but when I take it out when the machine is running and put it back on again, it's not recognized anymore. 
Basically I have to have a SD card in during startup in order to use it. It's sucks....
:-?

---

### Post by geos2 on 2006-07-17
This is what happens with my x60s.. I assume the sd device is the same.  I have reported this as a bug... see what happens.

[https://launchpad.net/distros/ubuntu/+bug/53268](https://launchpad.net/distros/ubuntu/+bug/53268)

---

### Post by geos2 on 2006-07-17
if you remove and reload the relevant kernel modules it will actually work!

put in the sd card then try:

$sudo su

then:

$modprobe -r sdhci
$modprobe -r mmc_core
$modprobe mmc_core
$modprobe sdhci

the SD disk may automount if it doesn't try:

mount /dev/mmcblk0p1  

this worked for me...

---

### Post by kumpf on 2006-08-06
thanks for the modprobe info.  It makes my built-in multi-card SD card reader (Ricoh) work on an e1405 Dell Inspiron laptop.  Is there anyway to have it do this automatically so modprobe commands don't need to be entered every time the card is used?

Thanks!

---

### Post by richrosa on 2006-08-17
After a suspend my SD Card reader would not be identified when I put in the card but the kernel module removal and reloading solution posted here worked like a charm. Thanks!!

---

### Post by geckomind on 2006-09-05
> **geos2 said:**
> 
put in the sd card then try:

$sudo su

then:

$modprobe -r sdhci
$modprobe -r mmc_core
$modprobe mmc_core
$modprobe sdhci


This actually made the elusive on-board SD-cardreader in my Dell XPS Gen2 work like a charm! Thank you very, very much!! :-D :KS 

Is there a way to automate this?

---

