---
title: "HP deskjet all in one scanner"
date: 2016-02-19
forum: Hardware
---

### Post by gil.rito on 2016-02-19
Hi, 

I'm trying to setup my scanner on my ubuntu 14.04. If I start the system with the printer/scanner connected I don't have problems to do a scanning job. However if I  connet the sacnner with the system already started I can't do a scanning job. However I can do a printing job.
I would appreciate very much if someone could help to setup properly my prinetr/scanner.

Gil

---

### Post by mörgæs on 2016-02-19
Which printer/scanner?

---

### Post by gil.rito on 2016-02-25
It is a HP deskjet F370. Thanks

---

### Post by mörgæs on 2016-02-27
It is well supported in Buntu:
[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f300_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f300_series.html)

I don't know if there is a solution to the problem, and... is there a problem at all? Why don't you just keep the printer attached at all times?

---

### Post by carydconover on 2016-02-27
I found that even once you find the drivers and have them installed and running that all the features are not in place.  You really need to do a config check and run the printer manager and click on the tool in the top bar.  Let it run and find out what components are missing.  Once you know that (It will tell you and try to install them.)  Mine did not install them.  Failed to do so.  So I started up the Ubuntu Software Center and searched for each component that it was missing and loaded each and every one.  They were all on the Center save one that I found by a very similar name.  Once I had those in place I was good to go.  I have an HP Office Jet All in One 6310 and Office Jet All in One Pro 8600.  Both work well.  Can scan also.

---

### Post by ajgreeny on 2016-02-27
It may be worth making sure that hplip and hplip-gui are both installed then using the hp-toolbox gui to configure the printer and scanner.

---

### Post by gil.rito on 2016-03-10
> **ajgreeny said:**
> It may be worth making sure that hplip and hplip-gui are both installed then using the hp-toolbox gui to configure the printer and scanner.

Hi I've solved the problem by reinstalling the hplib and xsane and changing the permissions for usb.

Thanks for all of your effort.

---

### Post by mörgæs on 2016-03-10
Good, please mark the thread 'solved'.

---

### Post by slickymaster on 2016-03-10
*Moved to the ***Hardware*** sub-forum*

---

