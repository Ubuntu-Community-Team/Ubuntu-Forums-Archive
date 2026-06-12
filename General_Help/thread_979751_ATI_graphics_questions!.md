---
title: "ATI graphics questions!"
date: 2008-11-12
forum: General Help
---

### Post by pejpm on 2008-11-12
Hi. I am a relative newbie to Ubuntu. I recently got a toshiba satellite l305d-s5895 and installed 8.10. I have a weird issue where occasionally (probably around 30% of the time) that I boot up, i get these weird lines across my screen. it looks like when a you rewind a movie on a vcr. its blurry and the lines are jagged horizontal lines that run across the screen.

I checked my xorg.conf file and it looks like this...

> 
Section "Device"
        Identifier  "Configured video device"
Endsection

Section "Monitor"
        "Configured Monitor"
Endsection

Section "Screen"
        Identifier "Default screen"
        Monitor "Configured monitor"
        Device  "Configured video device"
Endsection

 

Does this mean I am not using the correct drivers??

The laptop uses an AMD turion 64 processor, and ATI graphics. lspci tells me:

ATI Technologies Inc RS690M [Radeon x1200 Services]

In addition to this, I had compizconfig settings manager running and had dekstop cube working. however I booted this morning and I am now back to standard 2 desktops and no desktop effects. ccsm is still available, but none of the effects work. I thought I was using compiz fusion, but now I'm not even sure if I have that installed. does standard compiz support desktop cube? how do i check?

---

### Post by Titan8990 on 2008-11-12
Which version of Ubuntu are you using?

---

### Post by Ryadt on 2008-11-12
Post
```
lshw -C Display
```It will give you your graphic card model.

---

### Post by pejpm on 2008-11-12
> **Titan8990 said:**
> Which version of Ubuntu are you using?


Intrepid. I mentioned that in the post..

I just went to System > Administration > Hardware Drivers and enabled the proprietary ATI drivers. Was that the correct thing to do? Compiz seems to be working again, but I'm not sure if I've got it setup correctly. What do people reccomend i use. are the ati drivers ok?

---

### Post by pejpm on 2008-11-12
> **Ryadt said:**
> Post
```
lshw -C Display
```It will give you your graphic card model.

this is what it says.....

> WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=64 module=fglrx


---

### Post by nikgare on 2008-11-12
Is the ATI driver listed under **System->Administration->Hardware Drivers**

---

### Post by pejpm on 2008-11-12
> **nikgare said:**
> Is the ATI driver listed under **System->Administration->Hardware Drivers**

Yes. it was, so I activated it. is this the best driver to use?

---

### Post by nikgare on 2008-11-12
Probably - which one does it say it is?

After activating it, you'll need to restart X - or maybe reboot.

---

### Post by Ryadt on 2008-11-12
Can you post the output of ```
fglrxinfo
```

---

### Post by aaaantoine on 2008-11-12
I thought the latest version of X.org no longer used xorg.conf.

---

