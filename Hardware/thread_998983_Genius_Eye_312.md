---
title: "Genius Eye 312"
date: 2008-12-01
forum: Hardware
---

### Post by sges on 2008-12-01
I need help configuring a Genius Eye 512 webcam with Ubuntu 8.10 AMD64

lsusb gives

Bus 001 Device 003: ID 093a:2622 Pixart Imaging, Inc. 

gspca seems to support 093a:2621 but not 2622 

Can you help?

---

### Post by tuesdaytaurus on 2008-12-28
Hi sges

Any luck in finding a solution for this problem? I have the same web cam and the same problem. Initially I was unable to even detect the cam in Intrepid. 
After applying the change suggested in [http://ubuntuforums.org/showthread.php?t=1009985](http://ubuntuforums.org/showthread.php?t=1009985), both skype and ekiga and Cheese detected the cam, but none of them displayed any video or images. I have tried the PRELOAD thing, but with no luck. 

It seems like there are many people around the world that are struggling with this same problem (same web cam and the same version of ubuntu) and I think it merits some time from the guys at canonical. If someone can translate the solutions in this post, it might also help. [http://ubuntuforums.org/showthread.php?t=845262](http://ubuntuforums.org/showthread.php?t=845262)

---

### Post by sges on 2009-01-06
Still no luck. Looks I will have to wait until drivers for this webcam are written.

---

### Post by dof on 2009-01-14
> **sges said:**
> Still no luck. Looks I will have to wait until drivers for this webcam are written.

Please let us know if you find a solution to this, i have the same problem. The microphone works fine but no webcam

---

### Post by kapi on 2009-01-30
not sure if this helps anyone but I was having similar problems trying to get cam going in Ubuntu 810 when using aMSN.

so tried opening ekiga and then selecting the video tab, then go to the edit tab and select preferences form the drop down list.

next click the enable video check box and Success! the web cam sprang to life.

have no success as yet though in aMSN

kapi

---

### Post by webdebbyjoss on 2009-03-28
Sorry. Have the same problem... any help on this?

---

### Post by webdebbyjoss on 2009-03-29
Found the solution.
Just need to get te following gspca sources and compile them.

run this as a single command!

```

 sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)

```

REBOOT! :)

and here we are!!

:guitar:

web camera "Genius Eye 312" is ready to use. tested with "Cheese"!
By default the picture is fliped up side down, picture hight level contrasted and very dark, but I think this can be configured. 

Anyway if somebody knows how to do this - detailed instructions will be appreciated!!

Good Luck!

---

### Post by szirakitamas on 2009-04-09
Hi!
Does not work on Hardy. Cheese flashes one flash per 10 secs, Skype has a green screen, and nothing more. :(

---

### Post by sges on 2009-05-17
> **szirakitamas said:**
> Hi!
Does not work on Hardy. Cheese flashes one flash per 10 secs, Skype has a green screen, and nothing more. :(

Does not work with the new kernel on Jaunty Either.

---

### Post by kapitanbar on 2009-06-15
Doesn't work and also when doing modprobe gspca gives a strange and new error message: FATAL: error insterting gspca. Makes to see dmesg and this is what you get.

> gspca: disagrees about version of symbol video_devdata
[  157.718341] gspca: Unknown symbol video_devdata
[  157.718481] gspca: disagrees about version of symbol video_unregister_device
[  157.718483] gspca: Unknown symbol video_unregister_device
[  157.718532] gspca: disagrees about version of symbol video_device_alloc
[  157.718533] gspca: Unknown symbol video_device_alloc
[  157.718552] gspca: disagrees about version of symbol video_register_device
[  157.718553] gspca: Unknown symbol video_register_device
[  157.718640] gspca: disagrees about version of symbol video_usercopy
[  157.718642] gspca: Unknown symbol video_usercopy
[  157.718659] gspca: disagrees about version of symbol video_device_release
[  157.718661] gspca: Unknown symbol video_device_release


---

### Post by kapitanbar on 2009-06-15
try this

in a root box (Ctrl+Alt+F1)

first check what's on lsmod

```
lsmod |grep gspca
```it should show something like this

> gspca_sonixb           13824  1
gspca_main             29568  2 gspca_sonixb
videodev               45088  3 gspca_main,compat_ioctl32
usbcore               170288  6 gspca_sonixb,gspca_main,usblp,ehci_hcd,ohci_hcdremove any gspca_"XXXX" (were XXXX is any other sub-module, that doesn't work with the 312 spheric thingy), doing this:

```
sudo modprobe -r gspca_XXXX
```(replace the XXXX with anything that you could have)

Then put the right sub-module, which is

```
sudo modprobe gspca_pac7311
```Watch this interesting file from the linux foundation regarding drivers for devices that SHOULD work with video4linux

[http://www.kernel.org/doc/Documentation/video4linux/gspca.txt](http://www.kernel.org/doc/Documentation/video4linux/gspca.txt)

I have a Genius iLook 300 (Vendor ID 093a:2628 ) and that one is not present at the video4linux list isn't any replacement? :(

---

### Post by Takmadeus on 2009-07-09
> **webdebbyjoss said:**
> Found the solution.
Just need to get te following gspca sources and compile them.

run this as a single command!

```

 sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)

```

REBOOT! :)

and here we are!!

:guitar:

web camera "Genius Eye 312" is ready to use. tested with "Cheese"!
By default the picture is fliped up side down, picture hight level contrasted and very dark, but I think this can be configured. 

Anyway if somebody knows how to do this - detailed instructions will be appreciated!!

Good Luck!

Worked for me in cheese and skype (the latter with some few quirks)

Now, is there any way we can get a normal and acceptable image quality (non inverted and with decent contrast)?

---

### Post by razor7 on 2009-10-02
Hello...the solution proposed above solved the problem in my Ubuntu 9.04 and Genius Eye 312, but there is a problem...the image get flicked  ¿¿¿???

Any idea why?


Thanks a lot!

---

### Post by Takmadeus on 2010-01-07
Now, sorry for the thread revival, but has anyone managed to fix the problems mentioned before with this webcam?

---

### Post by Amr_not_Amr on 2010-04-24
Finally I got my Genius iLook 300 to work on karmic .. other webcams should work too .. 
You can follow the steps explain here [http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/) and your webcam will work...

---

### Post by Gramzivi on 2011-09-26
I have Ubuntu 11.04 and Genius Eye312

when i wrote lsmod |grep gspca i get this

gspca_pac7302        18099  0 
gspca_main             27826  1 gspca_pac7302
videodev                 75143  1 gspca_main

i wrote like they sad here to wrote gspca_7311 instead gspca_pac7302 but no succes,

btw audio works fine.

---

