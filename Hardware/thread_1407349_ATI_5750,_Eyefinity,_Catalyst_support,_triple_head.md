---
title: "ATI 5750, Eyefinity, Catalyst support, triple head"
date: 2010-02-15
forum: Hardware
---

### Post by jon.mithe on 2010-02-15
Hello,

I am trying to find out whether a 3 monitor setup in ubuntu is possible without great pain or expense.

From what I've read the ATI 5750 should be capable of outputting 3 monitors at 1920x1200 using Eyefinity and apparently this may be supported in the 10.1 catalyst release, which should be availiable in ubuntu 9.10 (lots of should and mays in there :P :/)

Just wandering if anyone can confirm this or has managed to get something like this working.  Or perhaps a 3 headed nvidia card may be easier?

Any help would be great thanks, its actually to get some more screen real-estate for my job, but would like to figure out if its possible.

I'm running the latest standard 9.10 Ubuntu with a standard dell core i7 PC. Unfortunatly the mobo in this pc has only 1 PCIe slot. Only odd thing here is I am running 64bit ubuntu.  

Thanks, 
Jon

---

### Post by jon.mithe on 2010-02-15
posted this over at the ATI driver forum as well (see link at bottom).


I have not found out whether it would all "work" in the latest ubuntu.  However, I have found out that the DisplayPort nonsense may be big issue,I have read somewhere simple little passive / cheap display port adapters I saw would not cut it and I would need some sort of active one. Could only find one for £80 at some random website -- or get a monitor with a display port built in already... either way its a bit too much of a punt to see if the drivers are actually capable of running 3 monitors... :/

[http://phoronix.com/forums/showthread.php?p=112533#post112533](http://phoronix.com/forums/showthread.php?p=112533#post112533)

---

### Post by evenstranger on 2010-02-24
My setup with 10.2 ati drivers and ubuntu 9.10 it will only allow 2 heads to function third head is always disabled.. Triple head eyefinity works fine in windows. As far as I know the ati drivers on linux aren't supporting it yet.

---

### Post by jon.mithe on 2010-03-03
Thanks for the reply.  Yeah I bought 2 nvidia quadro NVS195's and some cheap passive display port adapters.  Aside from removing the ATI drivers and getting linux to boot, it took me a handful of minutes to configure it in the nvidia-settings and it all magically worked, teh awesomes.

cheers,
jon.

---

### Post by sirkuttin on 2010-07-22
i am wondering how you resolved this issue

---

### Post by javahollic on 2010-09-24
Um, yea, ho did you get this working, I have 2 DVI connected 1600x1200's and a HDMI(or could be DisplayPort) connected 1920x1200.  I can only get one of the 1600x1200 and central 1920x1200 connected, the 3rd is always disabled.  

Im missing a trick, hopefully...

---

### Post by LloydSev on 2010-11-11
> **javahollic said:**
> Um, yea, ho did you get this working, I have 2 DVI connected 1600x1200's and a HDMI(or could be DisplayPort) connected 1920x1200.  I can only get one of the 1600x1200 and central 1920x1200 connected, the 3rd is always disabled.  

Im missing a trick, hopefully...

ATI/AMD driver support for Linux is severely lacking. My guess is that this is a "feature" and not a bug with the drivers. When it comes to newer ATI/AMD Graphics chips, Linux is not a good place to use them I've found.

Of course if anyone has found a way to get this working, please update us.

---

### Post by 448191 on 2010-11-27
I'll bump this. Looking to free a PCIe slot. The Nvidia alternatives (Quadro) are slow and expensive.

---

