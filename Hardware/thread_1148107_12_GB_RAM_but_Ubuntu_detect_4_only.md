---
title: "12 GB RAM but Ubuntu detect 4 only"
date: 2009-05-04
forum: Hardware
---

### Post by snake_eyes on 2009-05-04
Hello,

I have Siemens server (RX300) with 12 GB RAM, 300 GB HD, I installed Ubuntu 8.04 it detect 4 GB only, although I installed windows in order to check the RAM it detect also 4 GB, but I worked around in windows, I made some change in system32 by adding some parameters, after that it detect 12 RAM.

What I can do with Ubuntu in order to force Ubuntu to read the 12 GB instead of 4?

Cordially,

---

### Post by Svensk023 on 2009-05-04
Either re-install the system with a 64-bit operating system if it is processor compatible, meaning duo-core and above.
Or option two is, if I am not mistaken, changing your kernel to the server kernel, or something around those lines, you can poke around the forums for a HOWTO.

---

### Post by snake_eyes on 2009-05-04
There is no way to do it instead of installing 64 bit?

Do you have any links about HOWTO do it?

Please note that the Server is online since 6 months and it is the mail server which is important to keep it alive... 

Coridally,

---

### Post by onero on 2009-05-04
32 bit systems naturally can detect only 4GB of addressable space, and it is recommended that for systems with more than 4GB of RAM you really should use a 64 bit OS.

For 32 bit, you can use PAE ([http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)) in order to read the extra RAM; this was probably also what you changed in Windows. By default, the Desktop edition does not have this enabled, but the Server Edition kernel does, so you just need to install the Server Edition kernel and boot using it (this will entail a restart since you are changing kernels). This is really easy; there is a guide here: [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by snake_eyes on 2009-05-04
Thank you alot... much appreciated!

---

### Post by snake_eyes on 2009-05-04
Sorry, but in the faq [http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/) they mentioned that there are tow options to do it

Option # 1: Use 64 bit Ubuntu Linux

64 bit Linux kernel will take care of 4G or more memory. Just grab latest 64 bit version and install it.

Option #2: Install PAE enabled kernel

My question is which one is recomended to do it first opetion or second in you minde? although I have zimbra server installed on it 32 bit so I should upgrade also zimbra to 64 or it will work as will?

Cordially,

---

### Post by VladNistor on 2009-05-04
You can do either. 
Installing a 64 bit operating system means losing your settings and needing to back up data, so more of a hassle. The 64bit OS can address the ram natively and may give some applications a performance boost (mysql) and some may run slower.
The fastest solution and the one I recommend is that you use the Server Kernel which gives you access to all your 12 GB of ram with no hassle. the Server Kernel uses PAE to access the extra memory.

Hope this helps!

---

### Post by snake_eyes on 2009-05-04
Thank you again... I will go ahead...

Cordially,

---

### Post by snake_eyes on 2009-11-25
Hello,

Referring to this topic subject I ran this command in order to install the 64 bit kernel
```


sudo sudo apt-get install linux-headers-server linux-image-server linux-server
```

my question is how to disallow the linux-headers-generic to appear in the update-manager? because on each update the 32 kernel appearing in the update-manager and requesting to install the updates although I'm not using it.

Cheers,

---

### Post by adamronchi on 2009-11-25
Hi..
  Thanks for sharing the information which you share and its really good one you share..

---

### Post by snake_eyes on 2009-11-25
> **adamronchi said:**
> Hi..
  Thanks for sharing the information which you share and its really good one you share..

thank you for your kind reply but still I don't know how to disappear the linux-headers-generic from the update-manager :)

Cheers,

---

