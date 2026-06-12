---
title: "Packard Bell EasyNote MZ35-U-005"
date: 2008-07-25
forum: Hardware
---

### Post by SnappyU on 2008-07-25
Hi,

I've got Ubuntu installed on the Packard Bell EasyNote MZ35-U-005 notebook and was having sound working with alsa and pulseaudio, but the headphone jacks were not working.

After searching through, I did couple of things and now it works:

1.  Installed latest version of realtek drivers.  (Still didn't work)
2.  gksu gedit /etc/modprobe.d/alsa-base and added "options snd-hda-intel model=dallas" (Still didn't work)
3.  Then I found one of the mixer control option
File->Change Device->Realtek ALC861-VD (OSS Mixer)
3.1 There is a PCM-2 (for my notebook) and it was way low.  I slide it up, and presto, beautiful sound loud and clear on my earphone!

To be fair, I saw a link that mention about how the earphone audio would be soft, and I took that hint to double check with a LOUD audio test file that basically was 8hours long!

Anyway, I hope this helps you, 'cos it ended my 4~5 months wait for proper audio support! :)

Now Ubuntu 8.04 works perfectly on my notebook! :) ... oh wait, I still have to fix the ATI 200m graphics support to have proper compiz ... *dang* ... well, not perfect, but 98% anyway! ;)

PS: I don't know for sure whether step 1 & 2 is needed, but I don't wish to undo and break a working system.  So you may try hunting for the PCM-2 option before trying 1 & 2.  Maybe the updated Realtek driver revealed the PCM-2 option.  Post your findings and results. :)

---

### Post by SnappyU on 2008-07-27
UPDATE: I just enabled the ATI proprietary driver set and now Compiz effects works!  The ATI driver used to cause the black screen boot up problem but has probably been updated.

Now the *whole* notebook is working just fine! Woo hoo! :)  My transition to Ubuntu is complete! :D

---

### Post by JosephWheatley on 2010-01-09
@**SnappyU **I have the same laptop as you and have installed Ubuntu 9.10 Karmic Koala. 
Have you any new advice  on getting the sound to come out of the headphone socket please?

Also how are you able to make the Ati driver work? I can run it downloaded from here [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) and it runs. 

But still I can't get the Visual Effects to go to Normal and installing the Ati Catalyst control from the Software Centre. The Catalyst Control Centre say there is no hardware or no driver. But there is no driver in the "Hardware Drivers" menu.

Any advice appreciated. I am new to Ubuntu and have not used previous versions.

Thanks

---

### Post by SnappyU on 2010-02-01
> **JosephWheatley said:**
> @**SnappyU **I have the same laptop as you and have installed Ubuntu 9.10 Karmic Koala. 
Have you any new advice  on getting the sound to come out of the headphone socket please?

Also how are you able to make the Ati driver work? I can run it downloaded from here [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) and it runs. 

But still I can't get the Visual Effects to go to Normal and installing the Ati Catalyst control from the Software Centre. The Catalyst Control Centre say there is no hardware or no driver. But there is no driver in the "Hardware Drivers" menu.

Any advice appreciated. I am new to Ubuntu and have not used previous versions.

Thanks

I'm using 9.04 Jaunty on my Packard Bell.  Karmic was too flaky on it so I reverted to Jaunty.  In Jaunty, I have compiz working completely fine.

My suggestion is to use Jaunty. :)

Welcome aboard using Ubuntu! :)

---

### Post by jamesa00789 on 2010-12-27
I have the same laptop and I posted the solution to the sound problem here:

[http://ubuntuforums.org/showthread.php?t=1583184](http://ubuntuforums.org/showthread.php?t=1583184)

---

### Post by SnappyU on 2011-04-26
Thanks James!

---

### Post by JosephWheatley on 2011-10-19
It seems that because of the **ATI Express 200m** card in the **MZ35** that ubuntu beyond 8.04 or 8.10 will not work with the ati graphics and falls back on the generic ubuntu driver.

That's why the 3d games I installed in 10.10 never worked properly and Google earth which works in my Windows 7 partition works but only shows muddled have hidden images in Ubuntu 10.10

I may try and install Hardy Heron just to see Google Earth working.

I came across important info here [http://translate.google.de/translate?hl=de&ie=UTF8&prev=_t&sl=es&tl=en&u=http://jumax9.otakus-en-accion.es/2008/09/ubuntu-804-hardy-heron-en-packard-bell.html](http://translate.google.de/translate?hl=de&ie=UTF8&prev=_t&sl=es&tl=en&u=http://jumax9.otakus-en-accion.es/2008/09/ubuntu-804-hardy-heron-en-packard-bell.html) to prevent hanging.

---

### Post by JosephWheatley on 2012-11-09
It appears the MZ35 really does work out of the box with 12.04.

The headphones work straight away and the 3D graphics work too!

Although small issue with Power Management causing wireless to cut out when running on battery. The advice here should help [http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67)

---

