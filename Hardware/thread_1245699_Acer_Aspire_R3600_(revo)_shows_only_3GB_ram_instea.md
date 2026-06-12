---
title: "Acer Aspire R3600 (revo) shows only 3GB ram instead the 4 i have installed"
date: 2009-08-20
forum: Hardware
---

### Post by nandelbosc on 2009-08-20
Good night,

I'm using ubuntu 9.04 on an Acer Aspire Revo R3600. I upgraded it with 4GB of RAM.

After update to the latest bios version, I can see 4GB of memory in the BIOS menus, but not in ubuntu.

I tried to install this packages ([http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html):](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html):)
```

sudo apt-get install linux-restricted-modules-server

sudo apt-get install linux-headers-server

sudo apt-get install linux-image-server linux-server
```

after reboot I still see only 3GB...

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3023        603       2420          0         33        281
-/+ buffers/cache:        288       2735
Swap:         1027          0       1027
```

what i'm doing wrong?

thank's!

---

### Post by nandelbosc on 2009-08-23
I'm sure, i'm using the server kernel...

```
$ uname -r
2.6.28-15-server
```

with PAE...

```
$ cat /usr/src/linux-headers-2.6.28-15-server/.config  | grep -i pae
CONFIG_X86_PAE=y
```


any ideas?

thank's!

---

### Post by nandelbosc on 2009-08-24
No answer?

Can somebody guide me to a correct point (other forums, mailing list,...) to try to solve this pproblem?

---

### Post by philcamlin on 2009-08-24
you know how when you install 1gb of mem you end up with like 950mb ...
your machine is showing 3023 mb so its obviously seeing more then 3gb or else you would have some number in the 2GB range

so its not that its not seeing the memory its just i think one of those things that its lower then its suposed to be 

EX: my 2gb shows up as 1.7GB 
my dads 512mb shows up as 501mb

just a thought can anyone else help?

---

### Post by nandelbosc on 2009-08-25
thank's philcamlin, but I think you are a little bit exaggerated... ;)

If we are talking in GB, I can accepted to see 3,5 or 3,4 GB instead the 4GB, but see that...

```
marc@michael:~$ free
             total       used       free     shared    buffers     cached
Mem:       3096500     469824    2626676          0      34068     213372
-/+ buffers/cache:     222384    2874116
Swap:      1052248          0    1052248
marc@michael:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3023        460       2563          0         33        208
-/+ buffers/cache:        219       2804
Swap:         1027          0       1027
marc@michael:~$ free -g
             total       used       free     shared    buffers     cached
Mem:             2          0          2          0          0          0
-/+ buffers/cache:          0          2
Swap:            1          0          1
```

From 3096500KB (2GB with free -g!!!) to 4GB I think is too far...

PD: I used 2 modules of 2GB ddr2 kingston RAM.

---

### Post by ChAoS.ct on 2009-09-24
I have a Revo and it uses shared memory for the GPU. This means that the bios can take up to 1/4 of the RAM memory to the GPU.

In your case 1/4 of 4GB is 1GB ;)

You can tweak these settings in the BIOS Setup.

---

### Post by Revo1 on 2009-11-25
I have this exact model - Acer Aspire Revo R3600 Atom 330 with 2GB of RAM. I have been trying to find out what the exact brand of RAM it takes to upgrade to 4GB of RAM. Can you tell me how you upgraded? Do you know specifically what RAM brand will be compatible aside from it being PC2-6400? Thanks much.

---

### Post by warden976 on 2009-11-27
have a look at [http://techie-buzz.com/linux-tips/how-to-lift-ubuntu-linux-ram-limit.html](http://techie-buzz.com/linux-tips/how-to-lift-ubuntu-linux-ram-limit.html) - i've just run it and gone from 2.9 GB to 3.7 GB 

:p

---

### Post by nandelbosc on 2009-11-27
Revo1, I *buyed* more RAM apart... Two modules of Kingston KTH-ZD8000B/2G (equiv. HP/COMPAQ P/N: EM995AA)

Thank's warden976, but after install PAE I've got the same amount of RAM...

```
$ uname -a
Linux michael 2.6.31-15-generic-pae #50-Ubuntu SMP Tue Nov 10 16:12:10 UTC 2009 i686 GNU/Linux

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3023        929       2094          0         72        538
-/+ buffers/cache:        318       2705
Swap:         1027          0       1027
```

---

### Post by jrwu on 2009-11-28
I got my Revo R3600, and upgrade it to 4gb ram three days ago.
It shows there are 4GB in BIOS but 3GB in Ubuntu server 9.10.
No matter x86-pae version or amd64 versions, 'free' just reports 3023MB.

Since there are so many computer using ATOM 330, and only Revo's users encounter this problem, I guess that may be it's because of a bad design of Revo's motherboard.

There are a lot Revo with Windows 7 installed around.
Can anyone tells us whether Windows 7 sees 4GB ram in REVO?

---

### Post by jrwu on 2009-11-30
I really want to get some answer. So, today I bought a new hard disk and had my friend install 64-bit Windows 7 professional on my Aspire R3600. 
And Windows 7 says :
 
RAM : 4.00GB (3.00GB available)
 
 
There are only 3GB can be used and the other 1GB are only for decoration ?!!

---

### Post by grmmog on 2009-12-03
How much are you allocating to video?  That takes away from available memory.  UMA Frame Buffer Size under Advanced Chipset Features in the BIOS.

---

### Post by nandelbosc on 2009-12-03
> **grmmog said:**
> How much are you allocating to video?  That takes away from available memory.  UMA Frame Buffer Size under Advanced Chipset Features in the BIOS.

see attached image

---

### Post by St4ckHOu5e on 2010-01-16
I have the Revo 1600 which I upgraded to 4GB or Ram. Like the rest of you it shows 4GB in the Bios but only 3GB in Ubuntu 9.10 32-bit or 64-bit

---

### Post by nandelbosc on 2010-01-17
I'm sure is not an Ubuntu problem...

> I really want to get some answer. So, today I bought a new hard disk and had my friend install 64-bit Windows 7 professional on my Aspire R3600. 
And Windows 7 says :

RAM : 4.00GB (3.00GB available)

A future system bios firmware uptade can solve that?

In the acer website we can find that ([http://www.acer.es/acer/service.do?LanguageISOCtxParam=es&miu10einu24.current.attN2B2F2EEF=484&sp=page15e&ctx2.c2att1=14&miu10ekcond13.attN2B2F2EEF=484&CountryISOCtxParam=ES&ctx1.att21k=1&CRC=2178154640](http://www.acer.es/acer/service.do?LanguageISOCtxParam=es&miu10einu24.current.attN2B2F2EEF=484&sp=page15e&ctx2.c2att1=14&miu10ekcond13.attN2B2F2EEF=484&CountryISOCtxParam=ES&ctx1.att21k=1&CRC=2178154640))...

```
	BIOS	Acer	BIOS for Linux & FreeDOS	R01.A2L	1.2 MB	2009/08/03
BIOS	Acer	BIOS	R01.A2	1.4 MB	2009/07/30
BIOS	Acer	BIOS for Linux	R01.A1L	779.6 KB	2009/06/02
BIOS	Acer	BIOS	R01.A1	805.4 KB	2009/06/02
BIOS	Acer	BIOS	R01.A0	808.1 KB	2009/05/26
```

When I have a couple of hours I try to uptade.

---

### Post by St4ckHOu5e on 2010-01-18
I am running the latest BIOS, version: P01.A4L, listed on the Acer US driver site. That does not seem to have fixed the issue

---

### Post by argosreality on 2010-01-18
This is pretty common and you see the exact same thing on a Windows machine when attempting to run 4Gb (or more) of memory on a 32bit operating system (even with PAE). So, you have 4096Mb of system memory avalible. 

Subtract however much you've allocated to video memory (in the screenshot it showed 256Mb but that can be allocated dynamically as well with the chipset).

As Raymond Chen from Microsoft stated (yes it deals with Linux too)> In the absence of the /PAE switch, the Windows memory manager is limited to a 4 GB physical address space. Most of that address space is filled with RAM, but not all of it. Memory-mapped devices (such as your video card) will use some of that physical address space, as will the BIOS ROMs. After all the non-memory devices have had their say, there will be less than 4GB of address space available for RAM below the 4GB physical address boundary.

---

### Post by nandelbosc on 2010-01-19
> **argosreality said:**
> 
Subtract however much you've allocated to video memory (in the screenshot it showed 256Mb but that can be allocated dynamically as well with the chipset).


Ok, so someone can tell us how to allocote manually (not dynamically) the allocated video memory?

Thank's!

---

### Post by Kevbert on 2010-01-19
> **jrwu said:**
> I got my Revo R3600, and upgrade it to 4gb ram three days ago.
It shows there are 4GB in BIOS but 3GB in Ubuntu server 9.10.
No matter x86-pae version or amd64 versions, 'free' just reports 3023MB.

Since there are so many computer using ATOM 330, and only Revo's users encounter this problem, I guess that may be it's because of a bad design of Revo's motherboard.

There are a lot Revo with Windows 7 installed around.
Can anyone tells us whether Windows 7 sees 4GB ram in REVO?

I have a Revo R3610 supplied with 4Gb of memory. Windows 7 says there's 4Gb physical but only 3Gb available. Ubuntu 9.04 64bit only sees 3Gb.
I've seen on the web a suggestion that certain makes of memory may not fully work on the Revo.
My Revo apparently has 256Mb (separate?) dedicated to the display adapter. There is no option for me in BIOS to check memory readdressing.
I'm currently trying to sort out the problem with Acer (but am currently hitting a brick wall).

---

### Post by St4ckHOu5e on 2010-01-20
> **nandelbosc said:**
> Ok, so someone can tell us how to allocote manually (not dynamically) the allocated video memory?

Thank's!

In the BIOS under the Advanced Chipset Features change the iGPU Frame Buffer Detect from Auto to manual then you can choose the amount of RAM you want to allocate (up to 512MB).

I will have to double check when I get home tonight but when I set the RAM allocation to manual 256 I am pretty sure it still only showed 3GB.

---

### Post by nandelbosc on 2010-01-20
> In the BIOS under the Advanced Chipset Features change the iGPU Frame Buffer Detect from Auto to manual then you can choose the amount of RAM you want to allocate (up to 512MB).

I will have to double check when I get home tonight but when I set the RAM allocation to manual 256 I am pretty sure it still only showed 3GB.

I thought, as I have it...

> **nandelbosc said:**
> see attached image

---

### Post by AqD on 2010-04-02
I got the same problem...... wondering if anyone can confirm R36xx + 4GB RAM working in any OS :sad:

---

### Post by dojon on 2010-04-23
I have the R3610 with 4GB and it shows up at 3GB in Windows 7 64bit.  I got the machine with only 2 GB ram and upgraded with a similar stick and was worried it wasn't identical enough but it sounds like other people are also having this problem.  When I used a different speed memory altogether (so one 667 and one 800) it showed up as only 2.5 GB ram.  At least now with 2x800 it shows as 3, but it would be nice to use all 4!

---

### Post by b_b on 2010-06-23
Hi,

I aslo got an aspire revo r3610 with ubuntu 10.04 64bits and experienced the same problem of available memory (only 3gb dispplayed in ubuntu and 4gb displayed in bios). I've set the amount of memory for the gpu to 256mb in the bios.

It seems that the r3610 simply can't use 4gb ram due to a BIOS limitation on memory remapping or PAE :

[http://www.revouser.com/forum/viewtopic.php?f=8&t=359](http://www.revouser.com/forum/viewtopic.php?f=8&t=359)

Hope that a future BIOS update will fix this problem. It's quite strange to sell a computer that can't user the amount of memory shipped in...

---

### Post by konradson on 2010-06-23
This seems to be an Acer problem, because it happens both in Windows and with Ubuntu... you may have 4, but you can only use 3 gigabytes.
 
When Windows Vista appeared, manufacturers started selling laptops with an extra gigabyte in Flash Memory, because Windows Vista was supposed to be able to use it as extra RAM... okay, an octopus may be a pet...
 
If it is not a case with shared memory, it must be a problem solved with a Bios or firmware upgrade... 
 
As there are several people here with the same problem, I suggest you write to Acer asking them for a sollution. They may send all messages to the bin, but... the no response, you already have it, try for a Yes!!!
 
Or next time, buy an Ubuntu built laptop, like Dell's

---

