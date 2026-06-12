---
title: "What is this Restricted Driver Manager?"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by got-e on 2008-03-16
Hello, I am new to Ubuntu but not Linux. I am very familar with other distro's. Here is my problem, I have an Acer Aspire 5520 (great for the price) that I've installed Ubuntu 7.1 on. I downloaded and installed the 2.6.24 kernel with the latest madwifi patch to get the Atheros 5007eg wifi card to work. It works great, everything is working great except sound. The kernel recognizes an Nvidia MCP671 or something like that but I was getting this message about Restricted drivers or something not found and I found another post about this same laptop indicating that there was something to 'enable' in the 'restricted drivers'. My problem is that I compiled my own kernel and now i get this message "you need to install the package linux-restricted-modules-2.6.24 for this program to work." ... since I made my own kernel nothing like this exists ... and I'm not even sure what this is all about, this is something specific to Ubuntu.

As a side note, is there a way i can set up the system to log in as 'root'? I'm really tired of using 'sudo' for everything.

thanks

---

### Post by Ub1476 on 2008-03-16
You can post "su" in the terminal, then write root password, and you are 100% root (you might need to set a root password in User Management). 

I have never compiled my own kernel, but you would have to compile that driver yourself, I believe. In other words, compiling your own kernel is only recommended if you are a very advanced user. Did you check that ndiswrapper maybe can support your wifi?

---

### Post by got-e on 2008-03-16
Yes unfortunately using ndiswrapper (sucks) works but it only works about 10% of the time ... the majority of the time with ndiswrapper I can't authenticate a wpa2 connection, but that is not my problem, like I said my wifi works great with my new kernel and madwifi patch so no problem there ... the problem is my sound, the driver is loaded however I believe this 'restricted driver manager' has something to do with why I don't have sound ... could elaborate why it exists and how it works ... other distro's dont have this (thank God)

---

