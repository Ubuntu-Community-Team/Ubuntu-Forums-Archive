---
title: "Envy, ATI and Google Earth problem"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by Mega_slayer on 2007-02-20
I am having a problem getting Google earth working. I have used Envy to install ati drivers for a radeon 9000, the fglrx version is 8.28.8. I hear that version 8.30.8 works with Google earth, however I am not too sure how to install it properly. If anyone has any ideas I would greatly appreciate it. Thanks in advance.

---

### Post by ashmew2 on 2007-02-20
Hi , if u just want to install google earth ,(I installed it flawlessly on Edgy) , visit this link [http://earth.google.com/tour/thanks-linux4.html](http://earth.google.com/tour/thanks-linux4.html)
Download the linux setup (it will be  a .bin file)
Save it to your desktop

Open a terminal

```
cd ~/Desktop
chmod a+x GoogleEarthLinux(or whatever the file name).bin
./GoogleEarthLinux.bin(or whatever file name)
```

It SHOULD install google earth 
PLease let me know if that works

---

### Post by Mega_slayer on 2007-02-21
> **ashmew2 said:**
> Hi , if u just want to install google earth ,(I installed it flawlessly on Edgy) , visit this link [http://earth.google.com/tour/thanks-linux4.html](http://earth.google.com/tour/thanks-linux4.html)
Download the linux setup (it will be  a .bin file)
Save it to your desktop

Open a terminal

```
cd ~/Desktop
chmod a+x GoogleEarthLinux(or whatever the file name).bin
./GoogleEarthLinux.bin(or whatever file name)
```

It SHOULD install google earth 
PLease let me know if that works

Thanks for the reply ashmew2, sorry, I actually installed Google earth fine, however it`s the ati drivers that I`m not too sure about. I think that there are 4 packages that I have to install:

- source 
- driver
- kernel
- modules

Or something like that, I will have to check out what envy does in console mode.

---

### Post by ashmew2 on 2007-02-21
okiez :) Let me know if i can be of any help :D

---

### Post by Mega_slayer on 2007-02-24
The problem was actually the famous libGL.so.1.2 file. I had to download one from anoher version and copy it over the libGL.1 file in the google-earth directory. Now it works fine! Thanks for you help.

---

### Post by whistlerspa on 2007-03-05
I have the same problem on my laptop or desktop. One has an ATI radeon chipset , the other intel chipset. Where did you get this  lib~ file - other version of what?

---

### Post by eppoh on 2007-03-07
As popular as it is, I wish someone would package it and solve the dependencies for Ubuntu, so we could install it with Adept.

---

### Post by bluesscream on 2007-03-08
hallo,
there is the file
[http://files.covertprestige.info/important/libGL.so.1.2](http://files.covertprestige.info/important/libGL.so.1.2)

as root just backup the original  /usr/lib/libGL.so.1.2 
copy the new downloaded to this place
update the link file
> sudo rm /usr/lib/libGL.so.1
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

Google Earth runs fine on edgy eft and my radeon 9000 with the 8.28.8 driver, higher versions do not support this card.

---

### Post by malocite on 2007-07-26
Hi, I saw your message on the ubuntu forums regarding your radeon 9000 and how you installed the drivers with envy.

I have been trying to install the ati drivers 8.28.8 then I discovered the envy program, but still nothing works.  When I try to install the drivers using envy I get 

"ATI's legacy driver does not support your operative systen"

How did you get the drivers installed?

---

### Post by bluesscream on 2007-07-27
I updated my stationary machine with the radeon 9000 to feisty 7.04, and google earth was running out of the box, Did no longer need envy or prop legacy drivers from ati website.
But now I have problems with a hp notebook with  nv go 7200 graphics. so linux will not stop to give me  intellectual provocation.

---

### Post by w4ett on 2007-07-27
FYI the Proprietary ATI driver 8.28.8 WORKS ONLY WITH 9500 SERIES AND ABOVE...you must use the xorg-driver-ati, which is contained in the Feisty Fawn release.

---

