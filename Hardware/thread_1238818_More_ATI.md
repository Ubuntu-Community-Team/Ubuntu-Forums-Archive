---
title: "More ATI"
date: 2009-08-12
forum: Hardware
---

### Post by Jerry.S on 2009-08-12
New to Ubuntu. I have installed Ubuntu 9.04 on a older asus mobo with a 2.8 p4 4 gig ram. Be for I got in to ubuntu I bought a ATI card to run under win vista. To put it simply i didn't like it at all. Got a virus and it craped it all, so I changed to Ubuntu after checking the reviews. So enuf of that stuff back to the ATI Card. I have read a lot of other post about the ati support and I'm a lot disappointed, but what to do. It is a ati 3880 (yes it is agp) I have tried the FGLRX driver and all that it does is to slow way down my video refresh. I found a driver at the ati web site but I just dont know how to install it, and would like to know if it is the same one as the FGLRX driver. My next step is to get a new card supported under ubuntu but it will be awile, Any Ideas?:confused:

Thanx
JerryS

---

### Post by markbuntu on 2009-08-13
You should remove the fglrx driver you have and install the one from the ati site using this command. Open a teminal and cd to where you downloaded the driver
most likely

cd Desktop

The type this command

sudo sh /.ati-driver-installer......

just fill in the .... with the rest of the driver name and hit enter. You will be asked for your password and then the installer will start up. choose automatic install.

The driver from the ati site is updated from the one you have now and should support your card better since the 3880 was not even on sale when that driver was released.

---

### Post by Jerry.S on 2009-08-13
Thank you for the info will try it out and report back with results

---

### Post by Jerry.S on 2009-08-13
Sweeeeet it works. Thanks again

JerryS

---

