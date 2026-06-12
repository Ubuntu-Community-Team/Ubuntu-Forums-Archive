---
title: "ndiswrapper issues on WMP54GS"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by loureiro on 2006-03-27
Hello,

I seem to be having difficulties trying to install the drivers for my WMP54GS. I downloaded the ndiswrapper package but I recently figured out that the module comes pre-installed in Breezy. I'm new to Ubuntu and fairly new to Linux and I would just like to be able to stop dual booting and just use Ubuntu for everything. Especially the internet. Can anyone help me out? Does anyone know of a guide to help me through installing the ndiswrapper-utils? Please help!

---

### Post by mikedtemple on 2006-03-27
There's a fantastic HOWTO: out there- It's for Hoary- but it totally works on Breezy (Ubuntu 5.10).

[http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+HOWTO)

I had problems with the 

```
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
```

So what I did was beore running that block of code that begins with the "for" statement, I ran a 

```
sudo -i
```
to get a root terminal, otherwise, I was getting errors.  

By the way, the bcmwl5.inf and bcmwl5.sys drivers can be download from the Linksys Website, you'll just have to extract the files from the Driver directory in the .ZIP file.

I hope this helps, and Welcome to Ubuntu!!!


[QUOTE=loureiro]Hello,

I seem to be having difficulties trying to install the drivers for my WMP54GS. I downloaded the ndiswrapper package but I recently figured out that the module comes pre-installed in Breezy. I'm new to Ubuntu and fairly new to Linux and I would just like to be able to stop dual booting and just use Ubuntu for everything. Especially the internet. Can anyone help me out? Does anyone know of a guide to help me through installing the ndiswrapper-utils? Please help![/QUOTE]

---

