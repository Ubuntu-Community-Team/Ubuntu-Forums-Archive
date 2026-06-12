---
title: "ATI 6870 Ubuntu x64 driver problem"
date: 2011-01-02
forum: Hardware
---

### Post by reimerma on 2011-01-02
first of all im new Hi :D
and sorry for my bad english wich will follow xD
 
 
i just started with linux i installed ubuntu 10.10 x64 installed my graffiksdriver amd ccc 10.10 but it dont sopported my grafikscard i installed now 10.12 and it dont works anyways -.- someone knows the issuie =? i would like to use my new graffikskard but cant when u know what i mean xD

---

### Post by cariboo on 2011-01-02
I not sure what you mean by version 10.12, as there isn't one, Ubuntu is rleased in April and October, so the first part of the version number is the year, and the second part is the month. 10.10 = October 2010.

The first thing to try is to go to System-Administration->Additional Drivers to see if there is a driver listed for your graphics card.

If that doesn't work, you can go [here]("http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx") and download the driver. Once you have downloaded the driver, double-click the zip file and extract it to where ever you want. I don't use ATI/AMD, so I would suggest you check the documents in the directory you just extracted for information on how to install it.

---

### Post by fabricator4 on 2011-01-02
Try:

System -> Administration -> Hardware Drivers.

If this doesn't work there may not be any drivers available yet.

In this case contact AMD and find out how long before some drivers are available.  Others may have some suggestions...  hopefully.

Chris

---

### Post by reimerma on 2011-01-02
> **cariboo907 said:**
> I not sure what you mean by version 10.12, as there isn't one, Ubuntu is rleased in April and October, so the first part of the version number is the year, and the second part is the month. 10.10 = October 2010.
 
The first thing to try is to go to System-Administration->Additional Drivers to see if there is a driver listed for your graphics card.
 
If that doesn't work, you can go [here]("http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx") and download the driver. Once you have downloaded the driver, double-click the zip file and extract it to where ever you want. I don't use ATI/AMD, so I would suggest you check the documents in the directory you just extracted for information on how to install it.
 
i installed amd ccc 10.10 than amd ccc 10.12 not ubuntu 
 
 
 
bont i need to uninstall the installed driver=? how do i do that when i need to

---

### Post by cariboo on 2011-01-02
Those are windows drivers, I don't know how you managed to install them, I linked to the latest Linux drivers in my post up ^ there.

---

### Post by reimerma on 2011-01-02
> **cariboo907 said:**
> Those are windows drivers, I don't know how you managed to install them, I linked to the latest Linux drivers in my post up ^ there.

yeah i see but i downloaded it on ati forums it was called ccc10.12 it was an .run file i got ati applications on my desktop now ill try to install what u sended to me :D hope it runs :D

EDIT: it was **ati-driver-installer-10-12-x86.x86_64.run**

---

### Post by reimerma on 2011-01-02
> **fabricator4 said:**
> Try:

_**System -> Administration -> Hardware Drivers.**_

If this doesn't work there may not be any drivers available yet.

In this case contact AMD and find out how long before some drivers are available.  Others may have some suggestions...  hopefully.

Chris


i tryed this option now i black screened how can i reset it =?

EDIT= ty solved my problem :D to baad no driver for my card now on the internet-.-

---

### Post by fabricator4 on 2011-01-02
> **reimerma said:**
>  to baad no driver for my card now on the internet-.-

There might be drivers available from AMD.  Cariboo907 gave you a link to the drivers in the first reply to you.  Did you try it?

Chris

EDIT: the drivers on the AMD site look promising.  definitely worth trying.  It seems you missed the link the first time, have you found it now?

Chris

---

### Post by reimerma on 2011-01-02
> **fabricator4 said:**
> There might be drivers available from AMD.  Cariboo907 gave you a link to the drivers in the first reply to you.  Did you try it?

Chris

EDIT: the drivers on the AMD site look promising.  definitely worth trying.  It seems you missed the link the first time, have you found it now?

Chris

tryed it but it didnt work for me dont know why but i read in other forums that the driver had no fullsupport and i got newer version allready and still dont work


low resulution and no grafik adapter found like before 


amd is bad in linux support -.-

---

