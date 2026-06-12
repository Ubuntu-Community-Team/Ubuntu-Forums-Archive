---
title: "How to configure an HP onboard webcam"
date: 2008-06-07
forum: Hardware
---

### Post by BerT0 on 2008-06-07
Hello World!

This is my first time to use linux - Ubuntu Gutsy, also my first time to post in forums. I need your help.

How to configure HP Presario B1244TU webcam.

please help!

[www.ubuntuforums.org/showthread.php?t=593231](www.ubuntuforums.org/showthread.php?t=593231)

I followed the directions on how to configure webcam on the link
above, but none of this works for me. I have a HP webcam (5986:0104)
which is not in the supported UVC devices. but when i check if my
webcam is working or detected by the uvc driver by reading the 'Kernel
System log' here's what i got.

-------------------------------------------------------------------
[14.740000] uvcvideo: Found UVC 1.00 device HP Webcam (5986:0104)
[14.852000] input: HP Webcam as /class/input/input4
[14.852000] usbcore: registered new interface driver uvcvideo
[14.852000] USB Video Class driver (SVN r213)
-------------------------------------------------------------------

continue to installing: by copying and pasting this line in the terminal.

Code:----------------------------------------------------------------
sudo apt-get install subversion build-essential linux-headers-$(uname
-r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo cp -av /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname
-r)/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae $(uname -r)
---------------------------------------------------------------------

then reboot.. but still it wont work.

am i doing the right thing? I use cheese, and ekiga but non of this works.

the error message is: "unable to find webcam! sorry"

please help, I'm stuck.. 
Thanks

---

