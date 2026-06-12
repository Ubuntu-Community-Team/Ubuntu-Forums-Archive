---
title: "ATI Radeon 9600 installation problem"
date: 2012-07-06
forum: Hardware
---

### Post by PriMa77 on 2012-07-06
Im new to Ubuntu system and I have a problem with graphic card driver installation.

I have ATI Radeon 9600 card (I know its old :) ) and I downloaded ATI Catalyst drivers:
ati-driver-installer-9-3-x86.x86_64.run

I run it in Terminal where I got this error message:

[I]Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.2.0-26-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Ea15gF[/I]

Help needed :confused:

---

### Post by mastablasta on 2012-07-06
you can't install ati catalyst drivers. if you checked the drivers requirements you would see that your x.org and a few others are higher and thus not supported. if you managed to install them you would failt to boot (if not damage the hardware).
 
ATI dropped support for this card for linux quite some time ago.
 
you will need to use the opensource drivers provided by default install. if think you need to get development version of opensource drivers for osme reason there is a PPA called xorg edgers PPA.
 
why did you want to install ATI drivers?

---

### Post by PriMa77 on 2012-07-06
I have xorg drivers and I cant set higher display resolution than 1024*768.

---

### Post by mastablasta on 2012-07-06
have you checked here? you might need to configure it manually and create xorg.conf file. i have 9600 XT and works with no issues at all. and at full HD resolution.
 
however in version 10.10 it was wrongly idenftified. 
 
can you post the output of 
```
 
lspci 

``` 
command. just copy it and paste here. this should show how the card is recognised by the OS. 
 
```
 
xrandr 

``` 
command will show you available resolutions for the card.
 
this seems like a similar issue: [http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768?rq=1](http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768?rq=1)

---

### Post by PriMa77 on 2012-07-07
I downgrade to version 8.04, resolution is fine. Im running update now... if it still wont work, I will downgrade to Ubuntu 6. Than it should run OK... hope so :)

---

