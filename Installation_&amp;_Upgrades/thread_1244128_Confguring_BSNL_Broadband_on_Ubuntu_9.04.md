---
title: "Confguring BSNL Broadband on Ubuntu 9.04"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by aditya.gnu on 2009-08-19
Hi All Ubuntu Geeks,
Ive recently installed the latest distribution of Ubuntu 9.04 and I am trying to configure the BSNL Broadband Internet connection onto it, But I am unable to do so. 
Some of my attempts were by installing using **rp-pppoe.tar.gz** package, but it was of no use.
And when I executed the command** "mii-tool"** its result is failing by displaying my ethernet card is not been detected.
And for your information my PC is MSI Motherboard 754 Socket and AMD Athlon 64" Processor with 1.2GB of RAM and it's 3 yrs old one.
Is it because my PC is outdated or if there is some thing else, Kindly let me know.**ASAP**.
[B]And also the steps for configuring BSNL Broadband on Ubuntu 9.04.(Screen shots if possible).
[/B]
Thanks in Advance.
Regards,
Aditya.

---

### Post by zvacet on 2009-08-19
Right click on network manager applet (upper right)>edit connections>select wired or dsl.If you don´t know all informations you need then go to the applications>accessories<terminal and type

```
ifconfig
```

You can also see if your network card is recognized by typing in terminal

```
sudo pppoeconf
```

---

