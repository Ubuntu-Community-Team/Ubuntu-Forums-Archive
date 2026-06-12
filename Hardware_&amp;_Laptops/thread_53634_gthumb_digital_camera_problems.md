---
title: "gthumb digital camera problems"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by prodi_g on 2005-08-01
i'm having trouble importing pictures from my digital camera with gthumb.  i'm using a Olympus D-560Z and it is supported under gphoto.  i connect my camera and it is recognized as a usb mass storage device.  then i'm prompted to import photos and i choose to import.  gthumb opens up, tries to import the pictures, then fails.  i get the following error: 

"An error occurred in the io-library ('Unsupported operation'): Camera is supported by USB Storage drive" 

has anyone seen this before?  i know that i can just manually grab the pictures off of the mass storage device by navigating it and then just copy and pasting it, but this defeats the entire purpose of automating an import feature.  

any thoughts?  

thanks.

---

### Post by coolclassic on 2005-08-01
After looking at the web sight for gthumb it looks like it doesn't support usb and this may be indicated by your error message.

---

### Post by trash on 2005-08-01
Recently my mothers biggest complaint has been regarding her usb cam and windows, so i popped the Hoary livecd in her lil Toshiba 4020cdt or some such with the usb cam plugged in. Hoary booted perfectly and mounted her camera as usb storage on the desktop... we were stunned and she was tickled pink. Without any tinkering we were able to look at all the pic's on her camera. WAY easier than it was in windows! I'll be installing linux on her machine soon, as per her request!!!!! :D

I didn't get a chance to try much but the import didn't work for me either but I expected that because the camera we used is not supported at all by gphoto.

Would using right click 'create archive' work as a work around? Not that I mind the copy/paste or drag/drop method... 
Sorry I don't have a solution lol... I'm just taking this opportunity to  tell everybody Ubuntu scores another convert;)

---

### Post by David Haas on 2005-08-01
prodi_g--For my Nikon Coolpix, I plug the USB cable into the camera and turn on the camera. Then I open gThumb, in which I had previously selected my camera model. Immediately, thumbnails of all the pictures in the memory card appear. I then click "File > Import Photos" and all pictures are saved in my home directory. I use PTP, not mass storage, because this is the preferred transfer mode for this camera. Of course, PTP must be selected in the camera. You could check the preferred mode for your camera at the gPhoto Web site <http://www.gphoto.org/> if you haven't already done so. I'm sorry that I can't answer your question specifically, but I hope that this information helps you some.
David

---

### Post by coolclassic on 2005-08-02
I had a look at all the graphic files using kynaptic and found a package called 'digikam' this will do everything you want.

---

