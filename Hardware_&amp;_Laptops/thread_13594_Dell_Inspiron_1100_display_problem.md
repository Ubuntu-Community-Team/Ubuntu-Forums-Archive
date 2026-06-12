---
title: "Dell Inspiron 1100 display problem"
date: 2005-02-01
forum: Hardware &amp; Laptops
---

### Post by chambery on 2005-02-01
Hey all,

I just upgraded my older Hoary installation (once I [read](http://www.ubuntuforums.org/showthread.php?t=10366) that the madwifi/atheros driver is available through Synaptic), and my display has changed after reboot from 1024x768 to 800x600.  

Desktop->Preferences->'Change screen resolution'  only offers 640x and 800x.  IIRC on installation I followed [Damien Solley](http://www.geocities.com/randomnumbergenerator2001/#bios_info)'s instructions to correct this problem, but as the bios is now up-to-date, I'm not X savvy enough to get my laptop back to 1024x.  

I did notice that when running [FONT=Courier New]sudo X -configure[/FONT] (I didn't have enough information to complete the configuration), the suggested video card is i810, when I believe the Inspiron 1100 has a i845.

Any suggestions appreciated,

Todd

---

### Post by schwankl on 2005-04-20
Hi,

I don't know if you ever got this resolved.  You probably did. But I had a similar problem when I upgraded from Warty to Hoary, so if you didn't get it working here's what worked for me.  In Warty I had 1024 and after the upgrade only had 640 listed as a choice.  What eventually worked for me was copying the xfree86.conf file and then renaming it xorg.conf.

Good luck,
Jimmy

---

### Post by grakhul on 2005-05-11
Does the Dell Insprion use an sis chipset?

If I understand you correctly, you will want to grab the driver from winscholssler and dump it into your /usr/X11/.../modules/     directory( cant remember offhand)  then go into your xfree86-4.conf file and make sure that under the "devices" section that "sis" is selected.  

You can find the complete instructions here.  Bear in mind that this does not work if the 1100 does not use an SIS chipset for the graphix driver.


**[SiS Integrated Video Chipset Drivers](http://www.winischhofer.at/linuxsisvga.shtml)**

---

### Post by Hemal on 2005-06-04
Hey there,
I just installed ubuntu on my dell inspiron 1100.
I had this same problem of display where after some fishing found that "xorgconfig" does the job for us.

I have attached the copy of xorg.conf file that the above program makes after choosing the options that are needed.

Also the attached file is in the txt format due to the attachment rules on this forum.
So rename the file from xorg.conf.txt to xorg.conf.
Also before you do this do back up your old xorg.conf

Cool...
so yeah, something like

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
mv xorg.conf.txt xorg.conf
cp xorg.conf /etc/X11/

should help...

---

### Post by Hemal on 2005-06-04
And yes, one more thing to my above reply,
you will need to become root to copy the file.

---

### Post by DJCollins on 2006-02-20
Hello I just recently installed Unbuntu 5.10 onto my computer and I have having the same problem with everyone else.  I am unable to resolve the Screen Resolution, it is stuck on 640X480 at a refresh rate of 60Hz. I have tried reconfig. the xserver, installing 845patch, manually editing the config. file.  Any help would be greatly appreciated.

Thank you
DJ

---

### Post by blitzmoo on 2006-03-02
Same problem here.

---

### Post by blitzmoo on 2006-03-02
Got it to work!  Just need to add two lines to your xorg.config

```
        
HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
VertRefresh  50.0 - 75.0 # Very conservative. May flicker.

```

Put those lines into the monitor section ... It should look something like this:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
        VertRefresh  50.0 - 75.0 # Very conservative. May flicker.
EndSection


```

---

