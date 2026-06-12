---
title: "Comprehensive guide on how to install ATI drivers in Lucid Lynx"
date: 2010-06-08
forum: Hardware
---

### Post by jerkface on 2010-06-08
Can someone please provide me with a step-by-step guide on how to install and configure ATI drivers? I have a motherboard-integrated chip (radeon xpress 1150) and I couldn't find a specific article anywhere. I do want my 3D acceleration though. 
There are just too many different guides out there suggesting too many different techniques and it seems that none of them work for me. Any help would be appreciated, thank you in advance! :)

---

### Post by unmole on 2010-06-08
I suggest [this one]("http://ubuntuforums.org/showthread.php?t=1273767&highlight=beginners+guide+ati+linux+drivers") among the most complete IMHO.

---

### Post by Yellow Pasque on 2010-06-08
The only accelerated drivers you can use were pre-installed. ATI dropped support for your card after Catalyst 9-3, and older Catalyst versions won't install on any Ubuntu past 8.10/Intrepid.

If you tried to install some version of Catalyst/fglrx on your current system, follow this to restore the stock driver configuration: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

