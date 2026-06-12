---
title: "Resolution too big for screen"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Jobinma on 2009-08-25
Hi everyone!

I searched this forum before posting and did not find anything yet.  I just installed Ubuntu 9.04 and everything was done properly.  When restarted, the resolution is too big for my screen : 1600x1200 (4:3). It looks like half of what should be displayed is out of the screen.

I tried to change resolution and no matter what resolution I try, the screen is messed up to a point where I must restart in safe mode and run xfix to come back to the previous (too big) resolution.

My laptop is a Gateway MX3230[COLOR=Red]h[/COLOR] (the "h" seems important as it's not the samething as without it). I found a thread explaining what to do but it messes all up too when I change the xorg.conf.

What I notice is that, in the xorg.conf, no resolution are written in the file.

If only I could put a resolution that fits in the screen...

HELP !!

Thanks

---

### Post by Jobinma on 2009-08-26
Nobody ever got this kind of problem during installation ?

---

### Post by mulligan on 2009-08-26
i am very new here. but have you tried uninstalling it and installing it again. although don't try it unless some else tells you to do. i just find with a lot of things that helps especially drivers.

---

### Post by amsum on 2009-08-26
I too had this problem after fresh install of Ubuntu 9.04 not once but 2-3 times. So, fresh installation will not be of much help.
In one instance, it got rectified once it installed all updates after fresh-installation.
In other instance, I had to put some terminal commands to rectify that. I will try to recall those commands.

But I must say it should get fixed after downloading all UPDATES.

By the way... did you download all UPDATES?

---

### Post by amsum on 2009-08-26
> **Jobinma said:**
> Nobody ever got this kind of problem during installation ?

I got this problem with my Samsung 19 inch LCD monitor with resolution 1400:900.

Infact, still when fresh installing, my half of the screen goes below the taskbar area. I don't even see OK or Cancel button and just press Enter to complete the whole process.

---

### Post by Jobinma on 2009-08-27
I found the answer!!

In a terminal (Applications > Accessories > Terminal) :
```

sudo gedit /etc/X11/xorg.conf

```I found the device section and added a line :
```

    Section "Device"
        Option    "XaaNoImageWriteRect"
    EndSection
```Then, in the "screen" section, I added this subsection :
```

   SubSection "Display"
      Virtual 1024 768
   EndSubSection
```I saved my file (I suggest you back up you old file before!), closed it and then :

```

/etc/init.d/gdm restart

```
I waited and all status went to [OK] and then nothing happened.  I restarted the laptop and it was all perfect!

So nice!

---

### Post by Jobinma on 2009-08-27
Forgot to say that this link helped me :

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Good luck!

---

### Post by amsum on 2009-08-28
> **Jobinma said:**
> I found the answer!!

In a terminal (Applications > Accessories > Terminal) :
```

sudo gedit /etc/X11/xorg.conf

```I found the device section and added a line :
```

    Section "Device"
        Option    "XaaNoImageWriteRect"
    EndSection
```Then, in the "screen" section, I added this subsection :
```

   SubSection "Display"
      Virtual 1024 768
   EndSubSection
```I saved my file (I suggest you back up you old file before!), closed it and then :

```

/etc/init.d/gdm restart

```
I waited and all status went to [OK] and then nothing happened.  I restarted the laptop and it was all perfect!

So nice!

Yep, I too did the same last time.

---

### Post by BCPlanner on 2009-08-28
> **amsum said:**
> I got this problem with my Samsung 19 inch LCD monitor with resolution 1400:900.
 
Infact, still when fresh installing, my half of the screen goes below the taskbar area. I don't even see OK or Cancel button and just press Enter to complete the whole process.
 
Are you viewing Ubu on an external monitor? I had the same issue with an HP 1740 external tube. I could change the resolution to "make it fit" but then the display on the (Toshiba Satellite L350) was messed up. Finally disconnected the external monitor. (Monitor was OK with XP on one machine aand Vista on the other, but with the laptop's 17-incher, who needs the exterenal?? .. I still use a common keyboard and mouse for both systems.)

---

### Post by amsum on 2009-09-01
> **BCPlanner said:**
> Are you viewing Ubu on an external monitor? 

Samsung LCD is my desktop monitor. I too have Toshiba L305 and ubuntu 9.04 is working like a charm on it.

---

### Post by Jose Catre-Vandis on 2009-09-20
> **Jobinma said:**
> I found the answer!!

In a terminal (Applications > Accessories > Terminal) :
```

sudo gedit /etc/X11/xorg.conf

```I found the device section and added a line :
```

    Section "Device"
        Option    "XaaNoImageWriteRect"
    EndSection
```Then, in the "screen" section, I added this subsection :
```

   SubSection "Display"
      Virtual 1024 768
   EndSubSection
```I saved my file (I suggest you back up you old file before!), closed it and then :

```

/etc/init.d/gdm restart

```
I waited and all status went to [OK] and then nothing happened.  I restarted the laptop and it was all perfect!

So nice!

Thanks, this fixed it for me (admittedly only 2D but this will not be a problem for the user). I did have to do one more step, which was to create the xorg.conf file. So before trying to edit a blank, new file (if an xorg.conf has not been generated) run this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then make the above adjustments and additions.

My fix was needed on an oldish Fujitsu-Siemens Amilo Pro laptop with an S3 Unichrome Pro VGA adapter

---

