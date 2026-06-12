---
title: "rt2500 in hoary ?"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by dukeinlondon on 2005-03-29
Will serial monkey's rt2x00 drivers make it in hoary ? Does anyone know ?

---

### Post by dukeinlondon on 2005-03-29
Anyway, I compiled and installed the driver myself and it works great.... Just a hint

---

### Post by barbarian on 2005-03-30
I don't think so, since they have only beta for now unfortunately..  :-(

---

### Post by henkvanderes on 2005-04-10
I agree it should work easily since I got it functioning in Fedora Core 3. However I moved to Ubuntu and now I want to install my rt2500 wlan card too with the serial monkey drivers. 

When I compile the Module with "make" then it says I don't have a build directory in /lib/modules/2.6.10-5-386. 

I downloaded and unpacked the source of ubuntu linux-2.6.10 with apt,

what could be the reason I don't have this directory??

with kind regards,

Henk

---

### Post by Panos on 2005-04-11
[QUOTE=dukeinlondon]Anyway, I compiled and installed the driver myself and it works great.... Just a hint[/QUOTE]

Could you please post the relative link and instructions on how I can install it in my system?

Thx in advance

Panos

---

### Post by ludoodul on 2005-04-11
[QUOTE=henkvanderes]I agree it should work easily since I got it functioning in Fedora Core 3. However I moved to Ubuntu and now I want to install my rt2500 wlan card too with the serial monkey drivers. 

When I compile the Module with "make" then it says I don't have a build directory in /lib/modules/2.6.10-5-386. 

I downloaded and unpacked the source of ubuntu linux-2.6.10 with apt,

what could be the reason I don't have this directory??

with kind regards,

Henk[/QUOTE]
 I have exactly the same trouble...
If someone has an idea about the solution... please, send it to me !

thanks a lot..

ludoodul

---

### Post by henkvanderes on 2005-04-14
I found the solution for adding the build directory: just do:

sudo apt-get install build-essential linux-headers-`uname -r`

this will do the job!

good luck

---

### Post by dukeinlondon on 2005-04-16
[QUOTE=henkvanderes]I found the solution for adding the build directory: just do:

sudo apt-get install build-essential linux-headers-`uname -r`

this will do the job!

good luck[/QUOTE]
 Sorry about the delay. Yes the linux-header package is all you need to recompile the driver.

---

### Post by Yaniv on 2005-04-24
The drivers sadly didn't make it into hoary, but until they do, there's a howto for installing them here: [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)

---

