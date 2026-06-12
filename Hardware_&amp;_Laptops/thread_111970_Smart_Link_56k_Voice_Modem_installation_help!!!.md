---
title: "Smart Link 56k Voice Modem installation help!!!"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by linuxfreaks on 2006-01-03
Install. 

If you are going to use AMR/CNR/PCI modem type (as superuser): 

# make install-amr 

, or 

# make install-usb 

if you are going to use USB modem. 



after login in as super user i wrote make install-amr
and got the message that
bash: make: command not found

What should I do !!
I use ubuntu!!

---

### Post by towsonu2003 on 2006-01-13
pop in your install cd and in a terminal
```
sudo apt-get update
sudo apt-get install build-essentials
```
then try again. also, before going on, check out the second link oin my signature.

---

