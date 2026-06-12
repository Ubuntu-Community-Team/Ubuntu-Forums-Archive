---
title: "IVTV module won't load"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by newlinux on 2006-12-27
Hello, 

I'm trying to install a PVR-150 tuner card. I was following the instructions on:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Everything works fine until I try to modprobe ivtv:

```
sudo modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.17-10-generic/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg output:
```

[17182375.312000] ivtv: disagrees about version of symbol video_unregister_device
[17182375.312000] ivtv: Unknown symbol video_unregister_device
[17182375.312000] ivtv: disagrees about version of symbol video_device_alloc
[17182375.312000] ivtv: Unknown symbol video_device_alloc
[17182375.312000] ivtv: disagrees about version of symbol video_register_device
[17182375.312000] ivtv: Unknown symbol video_register_device
[17182375.312000] ivtv: disagrees about version of symbol video_device_release
[17182375.312000] ivtv: Unknown symbol video_device_release
[17182762.044000] ivtv: disagrees about version of symbol video_unregister_device
[17182762.044000] ivtv: Unknown symbol video_unregister_device
[17182762.044000] ivtv: disagrees about version of symbol video_device_alloc
[17182762.044000] ivtv: Unknown symbol video_device_alloc
[17182762.044000] ivtv: disagrees about version of symbol video_register_device
[17182762.044000] ivtv: Unknown symbol video_register_device
[17182762.044000] ivtv: disagrees about version of symbol video_device_release
[17182762.044000] ivtv: Unknown symbol video_device_release
```

I have to other tuner cards installed on this machine, both using dvb cards (kworld atsc 110) that work fine in mythtv. Searched around but didn't find this error anywhere. 

Any ideas on how I can load this module?

---

### Post by superm1 on 2006-12-28
> **newlinux said:**
> Hello, 

I'm trying to install a PVR-150 tuner card. I was following the instructions on:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Everything works fine until I try to modprobe ivtv:

```
sudo modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.17-10-generic/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```dmesg output:
```

[17182375.312000] ivtv: disagrees about version of symbol video_unregister_device
[17182375.312000] ivtv: Unknown symbol video_unregister_device
[17182375.312000] ivtv: disagrees about version of symbol video_device_alloc
[17182375.312000] ivtv: Unknown symbol video_device_alloc
[17182375.312000] ivtv: disagrees about version of symbol video_register_device
[17182375.312000] ivtv: Unknown symbol video_register_device
[17182375.312000] ivtv: disagrees about version of symbol video_device_release
[17182375.312000] ivtv: Unknown symbol video_device_release
[17182762.044000] ivtv: disagrees about version of symbol video_unregister_device
[17182762.044000] ivtv: Unknown symbol video_unregister_device
[17182762.044000] ivtv: disagrees about version of symbol video_device_alloc
[17182762.044000] ivtv: Unknown symbol video_device_alloc
[17182762.044000] ivtv: disagrees about version of symbol video_register_device
[17182762.044000] ivtv: Unknown symbol video_register_device
[17182762.044000] ivtv: disagrees about version of symbol video_device_release
[17182762.044000] ivtv: Unknown symbol video_device_release
```I have to other tuner cards installed on this machine, both using dvb cards (kworld atsc 110) that work fine in mythtv. Searched around but didn't find this error anywhere. 

Any ideas on how I can load this module?
This likely is caused by something going wrong with your headers that you built against.  Are you booted into an older kernel rather then the most recent update?  Have you modified /usr/src/linux by these dvb card installations or anything?  When you installed the dvb card, what did you follow?  The reasoning would be that if the dvb card uses some of the same modules, but you rebuilt them - then that would cause these unknown symbol errors.

---

### Post by newlinux on 2006-12-28
I'm booted into 2.6.17-10-generic, which I believe is the current kernel with Edgy.

I followed [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) for the most part (to install and load the latest v4l-dvb drivers) and I also went to pchdtv's web site and downloaded their drivers as well for the pchdtv 5500 (not sure if this was necessary - I have since removed that card and replaced it with another Kworld on this machine) and did a make and make install. I was guessing somehow installing the dvb modules might have been the problem.  Anyway I can determine which ones to rebuild so they work with both?

Ohh, crap. I had installed these cards (the kworlds) on a previous release which required me to download v4L dvb drivers. So I just followed those instructions again - however looking more closely at these directions, I don't think I needed to download and compile the v4L drivers for this release, I just needed to build the firmware - Could that have been it? Any ideas on how I should proceed (I don't know how to "undo it" :)).

I think you hit the problem on the head...

---

### Post by superm1 on 2006-12-28
> **newlinux said:**
> I'm booted into 2.6.17-10-generic, which I believe is the current kernel with Edgy.

I followed [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) for the most part (to install and load the latest v4l-dvb drivers) and I also went to pchdtv's web site and downloaded their drivers as well for the pchdtv 5500 (not sure if this was necessary - I have since removed that card and replaced it with another Kworld on this machine) and did a make and make install. I was guessing somehow installing the dvb modules might have been the problem.  Anyway I can determine which ones to rebuild so they work with both?

Ohh, crap. I had installed these cards (the kworlds) on a previous release which required me to download v4L dvb drivers. So I just followed those instructions again - however looking more closely at these directions, I don't think I needed to download and compile the v4L drivers for this release, I just needed to build the firmware - Could that have been it? Any ideas on how I should proceed (I don't know how to "undo it" :)).

I think you hit the problem on the head...
Alright, so considering this is the problem - i've got a couple of things you can try to cleanup the drivers that got installed, you'll have to let me know which one works for you and i'll add this to the troubleshooting section.

1) Try this in the v4l-dvb directory that you did a make install
```
sudo make uninstall
sudo depmod -a

```
And then rebuild the modules per the ivtv wiki page.
If you get an error about make uninstall not working, then this method won't work.

2) Go to /lib/modules/2.6.17-generic and look for a 
misc or dvb-v4l directory.  Hopefully this is where the modules got installed to.  If you don't see either of these directories, search by
```
find /lib/modules/2.6.17-generic -name tuner.ko
```
You will need to remove the directory that has the non kernel provided tuner modules.
Rerun
```
sudo demod -a
```
And then rebuild the modules per the ivtv wiki page

---

### Post by newlinux on 2006-12-28
The first method did not work (no make uninstall specified).

For the second method, I couldn't find any place where the new modules were installed. The only tuner.ko I could find was in /lib/modules/2.6.17-10-generic/kernel/drivers/media/video/tuner.ko, and I believe this is where the the modules that come with kernel go, so I didn't want to delete this directory. If this is the directory i should delete, I will give it a go... But I couldn't find any place where it put the modules. Maybe it overwrote the default kernel modules? Any other ideas? If not, maybe I'll just start over with a clean install makign sure not to intall and v4l-dvb drivers ... Good practice...

---

### Post by superm1 on 2006-12-28
This being the case, if they were just overwritten (no other weird directories in /lib/modules/2.6.17-generic)

```
sudo apt-get install --reinstall linux-image-2.6.17-10-generic
sudo depmod -a
```

Shoudl do it.

---

### Post by superm1 on 2006-12-28
> **superm1 said:**
> This being the case, if they were just overwritten (no other weird directories in /lib/modules/2.6.17-generic)

```
sudo apt-get install --reinstall linux-image-2.6.17-10-generic
sudo depmod -a
```Shoudl do it.

Also, 
reinstall the headers in case they were overwritten too.

```
sudo apt-get install --reinstall linux-headers-2.6.17-10-generic
```

---

### Post by newlinux on 2006-12-28
And that did work. hauppage is up and running. Once again thanks for all your invaluable help...

---

### Post by newlinux on 2006-12-28
I sent that without reading your last message. Apparently reinstalling the headers was unecessary, but i look into that if something else gets weird.

---

### Post by superm1 on 2006-12-28
> **newlinux said:**
> I sent that without reading your last message. Apparently reinstalling the headers was unecessary, but i look into that if something else gets weird.
If they are working without reinstalling the headers, don't worry about it.  I'll add this to the IVTV troubleshooting page.  Glad it worked.

---

### Post by Staach on 2006-12-29
I also have a problem loading the ivtv module (or so it seems). I have followed the instructions on [https://help.ubuntu.com/community/Install_IVTV_Edgy]("https://help.ubuntu.com/community/Install_IVTV_Edgy")
When getting to the: "sudo apt-get install ivtv-firmware" I get following error message:

Pakken ivtv-firmware har ingen tilgængelig version, men der refereres til den i en 
anden pakke. Det kan betyde at denne pakke blevet overflødiggjort eller 
kun kan hentes fra andre kilder
E: Pakken ivtv-firmware har ingen installationskandidat

roughly translated: The packet ivtv-firmware has no available version, but there is refered to one in another packet. This can mean that this packet has been made superfluous or only can be downloaded from other sources.
E: The packet ivtv-firmware has no installations candidate

I have tried to see if my PVR-350 is installed by typing "dmesg |grep Initialized" and only get the following:
"[17179578.492000] ieee1394: Initialized config rom entry `ip1394'
[17179612.408000] [drm] Initialized drm 1.0.1 20051102
[17179612.532000] [drm] Initialized via 2.7.4 20051116 on minor 0"

Soo..what do i do from here?

By the way, I am doing this on a VIA Epia MII 12000. Just in case this should have any impact on anything.

---

### Post by superm1 on 2006-12-29
> **Staach said:**
> I also have a problem loading the ivtv module (or so it seems). I have followed the instructions on [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)
When getting to the: "sudo apt-get install ivtv-firmware" I get following error message:

Pakken ivtv-firmware har ingen tilgængelig version, men der refereres til den i en 
anden pakke. Det kan betyde at denne pakke blevet overflødiggjort eller 
kun kan hentes fra andre kilder
E: Pakken ivtv-firmware har ingen installationskandidat

roughly translated: The packet ivtv-firmware has no available version, but there is refered to one in another packet. This can mean that this packet has been made superfluous or only can be downloaded from other sources.
E: The packet ivtv-firmware has no installations candidate

I have tried to see if my PVR-350 is installed by typing "dmesg |grep Initialized" and only get the following:
"[17179578.492000] ieee1394: Initialized config rom entry `ip1394'
[17179612.408000] [drm] Initialized drm 1.0.1 20051102
[17179612.532000] [drm] Initialized via 2.7.4 20051116 on minor 0"

Soo..what do i do from here?

By the way, I am doing this on a VIA Epia MII 12000. Just in case this should have any impact on anything.
It sounds like you don't properly have the ivtv firmware repository added to your /etc/apt/sources.list.

Double check and make sure that your /etc/apt/sources.list contains
```
deb http://dl.ivtvdriver.org/ubuntu edgy firmware

```
And make sure to do

```
sudo apt-get update
```

---

### Post by Staach on 2006-12-30
Thx Superm1. It turned out to be an error 40. In sources.list I wrote firmaware instead of firmware. I dont have the time to check if I can record from the card now, but I can certainly see it..which is a good start :p

---

