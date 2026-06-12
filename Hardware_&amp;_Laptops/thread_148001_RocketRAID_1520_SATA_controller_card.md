---
title: "RocketRAID 1520 SATA controller card"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by videoapelsin on 2006-03-21
Hi

Just bought this controller card (RocketRAID 1520). But I can't get it to work with Ubuntu. Is it possible to get it to work with ubuntu, or should I just return it and order another card?

---

### Post by rattking on 2006-03-21
Hello
i dont think this is supported in ubuntu by default 
but it looks like they do support linux.. there driver page is here
[http://www.highpoint-tech.com/USA/bios_rr1520.htm](http://www.highpoint-tech.com/USA/bios_rr1520.htm)
to compile that driver you will need the linux-kernel-headers installed
sudo apt-get install linux-kernel-headers

---

### Post by videoapelsin on 2006-03-21
okey, I can install the linux-kernel-headers but then I just don't know what to do. (newbie)

---

### Post by al108 on 2006-03-21
[QUOTE=videoapelsin]okey, I can install the linux-kernel-headers but then I just don't know what to do. (newbie)[/QUOTE]

Download drivers, they usually come with some sort of readme which will explain the basic steps on how to install the driver. If it doesn't work for some reason it'll usually tell you what you're missing, then install missing packages and try installing again.

---

### Post by rattking on 2006-03-21
download hpt3xx-opensource-v2.0.tgz from that site to a temp directory 
open a terminal and type
cd tempdir
tar zxvf hpt3xx-opensource-v2.0.tgz
cd hpt3xx-opensource-v2.0
CC=gcc-3.4
export CC
make KERNELDIR=/usr/src/linux-source-2.6.12
if all goes well you should have a file called hpt37x2.o
try to load it...
sudo insmod hpt37x2.o
then type dmesg and look at the bottom to see if there are any errors or warnings
hope it works for ya.. compiling kernel stuff can get tricky

---

### Post by videoapelsin on 2006-03-22
Okey

It all goes well until:

server@server:~/Desktop$ CC=gcc-3.4
server@server:~/Desktop$ export CC
server@server:~/Desktop$ make KERNELDIR=/usr/src/linux-source-2.6.12
bash: make: command not found

](*,)

---

### Post by theanorak on 2006-03-22
GCC et al aren't include in the ubuntu standard install - but
```
sudo apt-get install build-essential
```
and you *should* have everything you need.

---

### Post by al108 on 2006-03-22
You may need to install more stuff for it to work, just use synaptic to install whatever it'll say it's missing. Use search in synaptic if you don't know what section it's under. I think you might have to install "kernel tree" and other source packages in addition to build essential. Make sure you have gcc-3.4 installed too.

---

### Post by pksings on 2006-03-22
I spent about 6 hours attempting to get one of those to work and was not successful and returned it.  I spent quite a bit more and got a 3ware 8500 which worked perfectly. That has since been replaced with an LSI SATA megaraid which also works perfectly.  So my advice is return it and get one that really has support.  The RocketRAID claims it, but it doesn't really support it.

PK

---

### Post by videoapelsin on 2006-03-22
Okey.

pksings: hm, would this card [http://www.dustin.se/dacsaportal/?ProdID=5010059031](http://www.dustin.se/dacsaportal/?ProdID=5010059031) work on an old PII 233MHz machine?

---

### Post by pksings on 2006-03-27
[QUOTE=videoapelsin]Okey.

pksings: hm, would this card [http://www.dustin.se/dacsaportal/?ProdID=5010059031](http://www.dustin.se/dacsaportal/?ProdID=5010059031) work on an old PII 233MHz machine?[/QUOTE]

Yes, should work fine...The driver is already part of the kernel.

---

### Post by tim.n9puz on 2006-03-30
[QUOTE=videoapelsin]Okey.

pksings: hm, would this card [http://www.dustin.se/dacsaportal/?ProdID=5010059031](http://www.dustin.se/dacsaportal/?ProdID=5010059031) work on an old PII 233MHz machine?[/QUOTE]

I wondered if you have now installed this 3Ware 8006-2LP card with Ubuntu and if it was working properly. Any problems or things we should be aware of before doing the same?

Thanks.

---

### Post by Ongers on 2006-12-01
> **pksings said:**
> That has since been replaced with an LSI SATA megaraid which also works perfectly.

Ummm if a complete newbie might throw a question in here...

Did you install onto the LSI RAID or is that in addition to your install disks? If it's the former can you point me to some information on doing that? I'm getting errors trying to install.

---

