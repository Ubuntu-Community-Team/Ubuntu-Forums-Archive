---
title: "camera upside down"
date: 2009-12-11
forum: Hardware
---

### Post by someNewb on 2009-12-11
hello,
 i have bought new asus notebook and the webcame is shown upside down

i have read through [this thread](http://ubuntuforums.org/showthread.php?t=908660&page=3) but my driver is called "uvcvideo" and it does not seem to know option vflip=1

everytime i write 
sudo modprobe uvcvideo vflip=1
it writes:
FATAL: Error inserting uvcvideo (/lib/modules/2.6.31-15-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

i also tried installing this utility called "v4l2ucp" (who the hell makes these terrible `names`??) and it has all kind of  settings like brightness, contrast and everything but no "vflip" option

i am hopeless :(

---

### Post by someNewb on 2009-12-13
bump

---

### Post by drubin on 2009-12-13
It seems you need to install [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

---

### Post by someNewb on 2009-12-19
i tried following the guide but it says "Navigate to the 'uvcvideo-1b4c7a6b9d26' directory "

where is this directory? i searched all the directories inside / the only results it brought were directories named "uvcvideo"   

and when i wrote "make menuconfig" inside them (as the guide tells me to) it wrote error
**make: *** No rule to make target `menuconfig'. Stop**

 by the way, are you trying to make me install drivers for my usb camera? because i thought they came with the ubuntu. or is there some option that can flip the video when recompiling drivers?  i'm confused

---

### Post by someNewb on 2009-12-20
i found solution [here](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/comment-page-3)

---

### Post by talktorishav on 2010-02-06
Hi SomeNewB, I found the same solution with better and simple instructions here, [http://techspalace.blogspot.com/2010/02/upside-down-web-cam-simple-fix.html](http://techspalace.blogspot.com/2010/02/upside-down-web-cam-simple-fix.html)

---

