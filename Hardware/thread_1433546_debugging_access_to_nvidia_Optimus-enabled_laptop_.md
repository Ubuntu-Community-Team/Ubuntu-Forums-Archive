---
title: "debugging access to nvidia Optimus-enabled laptop needed"
date: 2010-03-19
forum: Hardware
---

### Post by avilella on 2010-03-19
Hi,

We are looking for students with basic Linux kernel/graphics notions
interested in applying for the X.org Open Source PRIME multi-gpu
support Google Summer of Code 2010:
[http://wiki.x.org/wiki/SummerOfCodeIdeas](http://wiki.x.org/wiki/SummerOfCodeIdeas)

We are also looking for Linux users with Nvidia Optimus-enabled laptops 
willing to provide debugging information for Open Source PRIME multi-gpu
support features being worked on. Please join the hybrid-graphics-linux 
team ([https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)) and send an email to 
the mailing list specifying your laptop model.

You can check the model, version and graphic card details of you laptop with these commands:
sudo dmidecode -s system-product-name
sudo dmidecode -s system-version
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

---

### Post by Gecko Slayer on 2010-03-21
Hey,

Am very willing to help out.

I've got the Asus N61J with a GT325M and the Intel GMA HD found on the i5.  This laptop also shows when it's using discrete by changing a light on the laptop - so I can tell when it's using the high powered card or not.

Willing to do anything to get some sort of support for Optimus.

Dylan

---

### Post by Nosferax on 2010-05-16
I am also willing to help ! 

I don't have enough free time to enroll in the summer of code, but I will gladly test stuff for you guys. 

My laptop is an asus u30jc and the graphics card connected to the nvidia optimus is a 310M.

Nox

Edit : here is the output of the lspci command 

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a72] (rev a2)

---

### Post by jorny32 on 2010-11-10
I am willing to help test.

Here is my output.

sudo dmidecode -s system-product-name
1015PN

sudo dmidecode -s system-version
x.x

lspci -vnnn |perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

04:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [ION] [10de:0a6f] (rev a2) (prog-if 00 [VGA controller])

---

### Post by krunalpatel on 2011-01-02
Whatever happened to this?


DELL XPS 15 L501X

SYSTEM VERSION: A04

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18) (prog-if 00 [VGA controller])
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df1] (rev a1) (prog-if 00 [VGA controller])

---

### Post by santiagordgz on 2012-02-06
f

---

