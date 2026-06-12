---
title: "my graphic card cant install in Ubuntu 10.04"
date: 2010-05-24
forum: Hardware
---

### Post by LEaver on 2010-05-24
Im newbie ubuntu user

im facing when update ubuntu from 9.10 to 10.04

when using 9.10 install graphic card that is working with special effect

but i don no why after update ubuntu to 10.04

that is pop up this message and cant using that special effect

ps:sry for my broken english

[IMG]http://img163.imageshack.us/img163/2613/helpkk.png[/IMG]

---

### Post by dino99 on 2010-05-24
sudo rm -f /etc/X11/xorg.conf

then reboot

you can add this to synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by LEaver on 2010-05-24
> **dino99 said:**
> sudo rm -f /etc/X11/xorg.conf

then reboot

you can add this to synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

still non working!
im using ATI HD RADEON 3450 and i installed graphic card hardware driver on Ubuntu 9.10 (working
just update to 10.04(non working properly) .......(sad)
[[IMG]http://img268.imageshack.us/img268/8007/atia.png[/IMG]](http://img268.imageshack.us/i/atia.png/)

---

### Post by dino99 on 2010-05-24
why are you installing the "catalyst" ? not necessary at all, use the genuine repo packages

---

### Post by LEaver on 2010-05-25
> **dino99 said:**
> why are you installing the "catalyst" ? not necessary at all, use the genuine repo packages

so?
now what i need to do?

---

### Post by masux594 on 2010-05-25
[OT] 
This font looks greeeat!  which font is that? 

Sysc, A
[/OT]

---

### Post by LEaver on 2010-05-25
any pro can help me?

---

### Post by Yellow Pasque on 2010-05-25
Go back to original driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Then, you can try to install the Catalyst/fglrx driver again.

---

