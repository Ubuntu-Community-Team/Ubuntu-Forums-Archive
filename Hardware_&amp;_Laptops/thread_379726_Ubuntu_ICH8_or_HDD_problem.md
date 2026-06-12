---
title: "Ubuntu ICH8 or HDD problem"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by juice99 on 2007-03-08
i had problems installing 6.06/6.10 or alpha 5 ubuntu - they were all failing on first step, when waiting bar was being showed without any message. And my hardware is ok, debian works fine, windows works fine. My CD are fine, i checked them. so... I finally managed to install 6.06 ubuntu using this guide [https://help.ubuntu.com/community/In...n/FromUSBStick](https://help.ubuntu.com/community/In...n/FromUSBStick)

but it has 2.6.15 kernel, and my network card is working only from 2.6.19+ (it is built-in network card)

i have Gigabyte GA-965P-S3 motherboard with 500GB sata2 drive connected to ICH8

so i tried to use 2.6.20 kernel from feisty (upgraded all packages that were needed for linux-image-2.6.20) but the system didnt boot up! failed to mount the root filesystem blah blah blah :/

so i just upgraded with apt-get upgrade and dist-upgrade to 6.10 (with 2.6.17)


So i tried to compile 2.6.20.1 and 2.6.19.7 by myself from the sources, but i get these messages:

[http://cba.pl/sys9/crash/DSC00035.JPG](http://cba.pl/sys9/crash/DSC00035.JPG)

this is my dmesg from working 2.6.17 (ubuntu-made one):
[http://cba.pl/sys9/crash/dmesg](http://cba.pl/sys9/crash/dmesg)

these are two of _MANY_ configs i tried when trying my own kernel:
[http://cba.pl/sys9/crash/conf1](http://cba.pl/sys9/crash/conf1)
[http://cba.pl/sys9/crash/conf2](http://cba.pl/sys9/crash/conf2)

This is my grub menu.lst:
[http://cba.pl/sys9/crash/menu.lst](http://cba.pl/sys9/crash/menu.lst)
Root partition just doesnt want to work what could i forget to compile in ?

I have two options:
- somehow add network card module from 2.6.20 or 2.6.19 to 2.6.17 kernel
- or, make 2.6.19/2.6.20 kernel work on my hard drive/motherboard

i've compiled many kernels before, but this one i can't i spent more than 25 hours trying to solve it. lspci is full of Intel - unknown device messages, but that doesnt matter, as this HDD works on 2.6.17 !!! so there MUST be a way! but why it doesnt work on 2.6.20 where my network card works

---

