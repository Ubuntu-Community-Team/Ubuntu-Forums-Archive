---
title: "8800 GTX will not allow Compiz"
date: 2008-07-08
forum: Hardware
---

### Post by Jarrex on 2008-07-08
It tells me 

"Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity "

so i typed "sudo apt-get install xserver-xgl"

and i got:
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I can not update restricted drivers or else it will reduce my max resolution to 640x480.


Any suggestions?

---

### Post by Gondee on 2008-07-08
That exact same thing happend to me. And i have the same graphics card. 

What i did was just back up my info on a flash drive and re install ubuntu..

---

### Post by chalewa on 2008-07-08
i don't have that card..

but did you try to whitelist your driver?

---

### Post by Jarrex on 2008-07-09
> **chalewa said:**
> i don't have that card..

but did you try to whitelist your driver?

edit: read below.

---

### Post by Jarrex on 2008-07-09
okay so i got it to stop say thing. now it says:


~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by chalewa on 2008-07-10
try commenting out or remove that value or something?

---

### Post by Gondee on 2008-08-22
I tried everything. The Fresh install is the only way _i_ could get it working.

---

