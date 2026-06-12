---
title: "GeForce 4 Drivers installation problem"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by rat_poison on 2007-01-20
I own an nVidia Geforce 4 Ti-4200, whose drivers I need to install on an Edgy Eft system

I use 
> 
sudo apt-get install nvidia-glx

Then I want to configure the driver, so I use

> 
sudo nvidia-glx-config enable


But this is what I get in response

> 
****@****:~$ sudo nvidia-glx-config enable
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.


I go to the Synaptic Package Manager and I see that "linux-generic"'s version is 2.6.17.10
while "nvidia-glx"'s version is 1.0.8776 +2.6.17.7-10.1 

Why does this happen and how do I solve?

---

### Post by taurus on 2007-01-20
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by rpalyvoda on 2007-01-20
I've got the same problem with Nvidia Geforce 4 420

---

### Post by rat_poison on 2007-01-20
Query Answered! Thnx

---

