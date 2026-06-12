---
title: "I want to upgrade RAM from 2GB to 8 GB in Ubuntu 10.04 (32 Bit)"
date: 2011-08-05
forum: Hardware
---

### Post by arunb on 2011-08-05
Hi,

I am using 2GB RAM in my acer laptop (OS: Ubuntu 10.04 -32 Bit), I would like to upgrade to 4GB and above.

What is the maximum RAM size possible on 32 Bit Ubuntu, my laptop supports upto 8 GB.

Also I do not want to use 64 bit OS.


thanks
a

---

### Post by haqking on 2011-08-05
> **arunb said:**
> Hi,

I am using 2GB RAM in my acer laptop (OS: Ubuntu 10.04 -32 Bit), I would like to upgrade to 4GB and above.

What is the maximum RAM size possible on 32 Bit Ubuntu, my laptop supports upto 8 GB.

Also I do not want to use 64 bit OS.


thanks
a

not much point upgrading if you dont want to use 64 bit., you could enable PAE using 32 bit but to be honest it is better to upgrade to 64 bit.

If you want to stick to 32 bit then you are essentially limited to using 4Gb or below.

see here [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by arunb on 2011-08-05
thank you for the prompt reply.

Instead of 8GB will 4GB be OK ? I checked and found PAE is already installed.

---

### Post by hakermania on 2011-08-05
Actually, what is the real point of using more than 4 GB of RAM?
I understand that some programs may be too large or you have large list of files that you need to access but I, with only 2 GB of RAM have *_never_* see it go up to 1.3GB, it was once that I had 13 tabs open in firefox, 4 in chrome, two of which where playing youtube videos in mute mode, I was hearing music from totem while watching my code in QtCreator and having 4-5 terminals open and a zip compression in progress....

---

### Post by .... on 2011-08-05
Note that the EnablingPAE documentation is out of date (I will correct it later today). The PAE kernel is the server kernel, so you would:
```
sudo apt-get install linux-image-server linux-headers-server
```
However, I highly recommend 64-bit.

---

### Post by .... on 2011-08-05
> **hakermania said:**
> Actually, what is the real point of using more than 4 GB of RAM?
I understand that some programs may be too large or you have large list of files that you need to access but I, with only 2 GB of RAM have *_never_* see it go up to 1.3GB, it was once that I had 13 tabs open in firefox, 4 in chrome, two of which where playing youtube videos in mute mode, I was hearing music from totem while watching my code in QtCreator and having 4-5 terminals open and a zip compression in progress....
Virtual Machines, GIMP, extreme multitasking, etc.

---

### Post by haqking on 2011-08-05
> **arunb said:**
> thank you for the prompt reply.

Instead of 8GB will 4GB be OK ? I checked and found PAE is already installed.

yeah you can use 4gb, if you want to go beyond that then use 64 bit, to be honest there is no real reason not to use 64 bit if you have the hardware.

it might not see the full 4gb though, it might report 3.5 or something similar depedning on the limits of your hardware as the processor might no be able to address it

---

### Post by haqking on 2011-08-05
> **.... said:**
> Virtual Machines, GIMP, extreme multitasking, etc.

+1 you beat me to it.

I use virtualisation alot so memory is important

---

### Post by arunb on 2011-08-05
> Actually, what is the real point of using more than 4 GB of RAM?

programs will visibly run faster on a 4GB system ??

Also will it be necessary to re-install Ubuntu after adding the RAM ??

---

### Post by arunb on 2011-08-05
> Actually, what is the real point of using more than 4 GB of RAM?

programs will visibly run faster on a 4GB system ??

Also will it be necessary to re-install Ubuntu after adding the RAM ??

---

### Post by haqking on 2011-08-05
> **arunb said:**
> programs will visibly run faster on a 4GB system ??

Also will it be necessary to re-install Ubuntu after adding the RAM ??

if you use memory intensive apps such as image manipulation (raw images for example) or virtualisation etc then the more memory the better.

and know you wont need to reinstall, unles of course you are to use 64 bit

---

