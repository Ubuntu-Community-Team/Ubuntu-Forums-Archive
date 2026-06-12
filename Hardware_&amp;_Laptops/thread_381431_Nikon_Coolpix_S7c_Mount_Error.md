---
title: "Nikon Coolpix S7c Mount Error"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by larryandrews on 2007-03-10
I've been using Ubuntu Edgy i386 on my computer for about 2 weeks now. And I love it. But right now I'm beginning to run into a few small set backs. Today I tried mounting my digital camera (Nikon Coolpix S7c) And encountered this error. 


An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I searched the forums trying to fix this myself with no success. No other programs are open besides Beryl. So I'm stumped.

Thanks in advance for any help I may receive.

My Computer Specs are:

AMD  X2 4800+
Nvidia 7800gt
2GB Ram

---

### Post by dozch on 2007-03-10
This is happening to me too after yesterday's update of libgphoto:

libgphoto2-2 (2.3.0-0ubuntu3~edgy1) to 2.3.0-0ubuntu3~edgy2

You can still import photo's as root, so somewhere a permission needs to be changed. 

Importing as root is a workaround and is probably not recommended:

  gksudo gthumb

Another, safer, workaround would be to set the camera not to PTP mode but normal USB (I know you can do that with Nikon SLRs). Then your camera will mount as an ordinary USB device and you can manually copy your photo's.

---

### Post by larryandrews on 2007-03-10
> **dozch said:**
> This is happening to me too after yesterday's update of libgphoto:

Another, safer, workaround would be to set the camera not to PTP mode but normal USB (I know you can do that with Nikon SLRs). Then your camera will mount as an ordinary USB device and you can manually copy your photo's.

How would I got about doing that?

Thanks for the reply.

---

### Post by dozch on 2007-03-10
Go in the menu of your Coolpix, select the Tool icon, go to Interface->USB and change "PTP" to "Mass Storage".

Then attach your camera to your PC again and you'll see the camera icon appear on your desktop.

Hope this helps.

(you can change it back in a couple days after the libgphoto problem has been fixed :-))

---

### Post by larryandrews on 2007-03-10
Works like a dream. Thanks a million!

---

### Post by Mateusz Ho&#322;ysz on 2007-03-11
Unfortunetely given solution can't help with Canonn S1 IS. This camera handles photo export only in ptp mode. Hope I see fixed package soon.

I have signed bug raport regarding this.

[https://launchpad.net/bugs/91265](https://launchpad.net/bugs/91265)

---

