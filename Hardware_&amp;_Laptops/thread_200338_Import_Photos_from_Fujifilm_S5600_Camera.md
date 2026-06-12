---
title: "Import Photos from Fujifilm S5600 Camera"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by Weta on 2006-06-20
Hello   

I am unable to download photos from our Fujifilm FinePix S5600 digital camera (also known as a S5200), onto a desktop running Hoary.  Can someone please either point me (still a newbie) to, or provide a, step-by-step guide that will help me to do this.

I have tried importing photos under gThumb, setting the camera to a Fuji FinePix S700 (PictBridge mode), but when I attempt to import the photos from the camera I get the following message: 

"An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4cb, product 0x142). Make sure this device is connected to the computer."

Thank you  

Weta

---

### Post by PWill on 2006-07-23
Bump, because I am getting the same kind of error with a FujiFilm FinePix, except I am running Dapper. The device mounts as a disk, and I can manually drag the images to the folder I want them in, but autodetect won't work with this camera.

---

### Post by brainkilla on 2006-07-23
> **xiamcitizen said:**
> The device mounts as a disk, and I can manually drag the images to the folder I want them in, but autodetect won't work with this camera.

What do you mean? If you want a program autostarted upon your camera being plugged in, then you could add to Removable drive and media preferences - Digital Camera something like this

```
f-spot --import /media/usbdisk
```

Uncheck 'browse removable media when inserted' and you'll get f-spot automagically importing your photos instead of nautilus displaying them...

---

