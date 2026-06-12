---
title: "Dialup on a DELL computer"
date: 2008-05-28
forum: Hardware
---

### Post by cmarlow on 2008-05-28
Hello Everyone,

I have a Dell Dimiention e521

2 gigs of ram and xp home and ubuntu on another partition.....

Ok heres the thing I have Conexant Dialup modem and I can NOT figure out ofr the life of me to get it to work. The reason I am needing to get it tow ork is doing the whole moving thing soon and so I might NOT be in an area of HSI ( High Speed Internet ) SO I guess its good to be best to get that to work.

SO I went to the linux.dell.com and downloaded the .DEB file for ubuntu 7.10 Conexant driver.. Yes, I am still using ubuntu 7.10 Double clicked on it.... I let it run but it says that as a status something about its the same driver or something like that... So I am wondering if I could get some step by step on how to get it working

Thanks,
Christopher

**EDIT**

I also had GNOME-PPP installed also!


I have done lspci | grep -i modem.. and the modem is seen ( see 1st attachment )

WHEN I tried ... dmesg | grep -i -A 3 -B 3 ttys

nothign happened it just went back to the command prompt ( see screen shot 2 ) 

so... the modem is there but I cant get it to install so I could use it..

I also, I even installed the HSF DRIVERS.... FOR the modem from LINUX.DELL.COM

says on the status: SAME VERSION ALREADY INSTALLED
and it skiped over the I NEED A Cpack installer thing 

and this is where I am at..... So my next step is getting it installed and trying to get it to work

   I am new to linux so any help is appreciated ^_^

Thanks,
Christopher

---

### Post by bwhite82 on 2008-05-28
Few things to try:

-Figure out the actual name of the driver (Google). Utilize the command: lsmod to see if its loaded, if not use: sudo modprobe driverName to load it.

-If I remember correctly, the driver from Dell needs to be configured by a shellscript first, hsfsetup? Something like that.

-Also, make sure Gnome-ppp is setup correctly, if its not detecting the correct modem, use /dev/modem for the device.

---

### Post by cmarlow on 2008-05-28
> **Soldierboy said:**
> Few things to try:

-Figure out the actual name of the driver (Google). Utilize the command: lsmod to see if its loaded, if not use: sudo modprobe driverName to load it.

-If I remember correctly, the driver from Dell needs to be configured by a shellscript first, hsfsetup? Something like that.

-Also, make sure Gnome-ppp is setup correctly, if its not detecting the correct modem, use /dev/modem for the device.


Hey,

Here is the actual name of the driver of the modem when I ran the MODEM TEST a couple days ago  to get the infomation about it I hope this can help you


-Also, make sure Gnome-ppp is setup correctly, if its not detecting the correct modem, use /dev/modem for the device.[/QUOTE]

I tried that but it still says NO MODEM FOUND.

I tried /DEV/SO1 ( I BELIVE is what it was called ) there was like 3 of these and it didnt find the modem on either of these ports I selected

---

### Post by bwhite82 on 2008-05-28
The command: lsmod | grep hsf
Should show a driver, if it does not, try loading it with:

sudo modprobe hsfserial

Also, another setting for Gnome-ppp to try is:

/dev/ttySHSF0

---

### Post by cmarlow on 2008-05-28
> **Soldierboy said:**
> The command: lsmod | grep hsf
Should show a driver, if it does not, try loading it with:

sudo modprobe hsfserial

Also, another setting for Gnome-ppp to try is:

/dev/ttySHSF0


Here you go here is a bunch of screenshots Ijust took. No Go :(

check the next reply for the last 4 pics

---

### Post by cmarlow on 2008-05-28
> **Soldierboy said:**
> The command: lsmod | grep hsf
Should show a driver, if it does not, try loading it with:

sudo modprobe hsfserial

Also, another setting for Gnome-ppp to try is:

/dev/ttySHSF0



HERE is the last 4 screenshots for some reason I could only upload 5 at a time...

---

### Post by bwhite82 on 2008-05-28
Alright, have you tried running (from a terminal):

hsfsetup

---

### Post by cmarlow on 2008-05-28
> **Soldierboy said:**
> Alright, have you tried running (from a terminal):

hsfsetup

Here is your result. ( see attached )

---

### Post by cmarlow on 2008-06-01
> **Soldierboy said:**
> Alright, have you tried running (from a terminal):

hsfsetup

[SIZE="5"]*BUMP*

[SIZE="3"]anyone know what the next step is?[/SIZE][/SIZE]

---

