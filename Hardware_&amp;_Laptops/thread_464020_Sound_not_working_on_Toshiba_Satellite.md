---
title: "Sound not working on Toshiba Satellite"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by ataylor1988 on 2007-06-04
I am running feisty on my toshiba laptop.  It is using the intel 945gm chipset with the intel high def audio.  It is a IHC7 family sound card.  I had fedora core 6 installed on here for a little while and the sound worked on it, I could just never get it to mount my windows partition so i could access all my files so i went to ubuntu.  Any idea how to get my sound to work.  Any help is greatly appricated 

Thanks
Andrew.

---

### Post by ataylor1988 on 2007-06-05
any help would be greatly appricated, i think i have to update my alsa drivers to get this to work.  Does anyone know a easy way of doing this like with synapic or a couple easy terminal commands Thanks.

---

### Post by Freaky_Llama on 2007-06-06
Add to the end of /etc/modprobe.d/alsa-base:

```

options snd-hda-intel model=3stack 
```

It worked on my Toshiba A135-S4527

---

### Post by moran on 2007-06-07
sudo gedit /etc/modprobe.d/alsa-base

from the terminal window.


you should be putting this: options snd-hda-intel model=3stack

after the last options row at the very bottom.

so it goes from this:

options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

to this

options snd-usb-usx2y index=-2
options snd-hda-intel model=3stack
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

then save it, and reboot the system, should work then.

---

### Post by alhead on 2008-07-23
Do you know if this would work on a Satellite M45?  I think my driver should be snd-intel8x0 but I don't really know what I'm doing.

---

