---
title: "Broadcom Wireless 4312 b/g card not working on HP laptop - Karmic Koala"
date: 2009-10-30
forum: Hardware
---

### Post by ubunt22rock on 2009-10-30
Hi I just downloaded Karmic. Everything's perfect except that I cant use wifi. My broadcaom STA driver's active but "not in use".

I tried some things mentioned in other threads. but no improvements. 

I am a bit frustrated cos I havent been using linux for past 6 months cos my jaunty was kinda stupid and most drivers dint work. And now this.

Would be grateful if any of you could help

---

### Post by stevenw66 on 2009-10-30
> **ubunt22rock said:**
> Hi I just downloaded Karmic. Everything's perfect except that I cant use wifi. My broadcaom STA driver's active but "not in use".

I tried some things mentioned in other threads. but no improvements. 

I am a bit frustrated cos I havent been using linux for past 6 months cos my jaunty was kinda stupid and most drivers dint work. And now this.

Would be grateful if any of you could help
Me too on HP1000 with broadcom chipset. Tried reinstalling bcmwl-kernel-source, no joy!

Everytime I upgrade something else breaks. 9.04 had no mutimedia. Now 9.10 has multimedia but no wi-fi.

---

### Post by fooman on 2009-10-31
> **stevenw66 said:**
> Me too on HP1000 with broadcom chipset. Tried reinstalling bcmwl-kernel-source, no joy!

Everytime I upgrade something else breaks. 9.04 had no mutimedia. Now 9.10 has multimedia but no wi-fi.

have you tried rebooting after reinstalling the bcmwl-kernel-source package?

i have the bcm4312 wireless controller in my hp-mini netbook and after installing karmic...i had no wireless.  even though it was enabled in hardware drivers,  it showed as "not in use".

the bcmwl-kernel-source was already installed by default,  but reinstalling it did the trick.  however it didn't work until AFTER i rebooted.

** to the original poster...if the bcmwl-kernel-source package is not installed....try installing it.  open a terminal and type or copy/paste the following:

```
sudo apt-get install bcmwl-kernel-source 
```then reboot and you should be good to go.

if it is already installed,  try reinstalling with this command:

```
sudo apt-get install --reinstall bcmwl-kernel-source
```then reboot.

hope that helps.

---

### Post by ubunt22rock on 2009-10-31
bcwml-kernel-source reinstallation trick, I tried prior to posting this. And yes, I rebooted.

So is there another solution to this?

---

### Post by gonefortheday on 2009-11-02
> **stevenw66 said:**
> Me too on HP1000 with broadcom chipset. Tried reinstalling bcmwl-kernel-source, no joy!

Everytime I upgrade something else breaks. 9.04 had no mutimedia. Now 9.10 has multimedia but no wi-fi.

Same trouble here on the same netbook series (HP Mini 1033)! :'(

They fix the excessive hard drive kerchunking (10-second spindown time!) and the video drivers only to break something even more essential than those!

---

### Post by any.linux12 on 2009-11-02
If the driver is installed but not in use do this:

echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf

then

gksudo gedit /etc/rc.local

and write:

modprobe wl 

before the exit 0

tell me if it works

---

### Post by howcanireachthesekids on 2009-11-02
this is relevant to my interests

bump

Someone please tell a guide how to get **Broadcom Wireless 4312 b/g card**
to work without having access to internet by any other means on the computer !
( hence no update etc etc...)

---

### Post by any.linux12 on 2009-11-02
> **howcanireachthesekids said:**
> this is relevant to my interests

bump

Someone please tell a guide how to get **Broadcom Wireless 4312 b/g card**
to work without having access to internet by any other means on the computer !
( hence no update etc etc...)

did you try my help?? after you run the commands you must restart

---

### Post by howcanireachthesekids on 2009-11-02
> **any.linux12 said:**
> did you try my help?? after you run the commands you must restart
i will try that right now and report back

---

### Post by ubunt22rock on 2009-11-02
@any.linux:
It dint work for me

---

