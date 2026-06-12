---
title: "Digital camera problems"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by thantos on 2006-04-13
So hopefully I am not asking a question that has already been asked, been searching for my answer for about 6 or 7 hours though, so I think I am safe.

I am having problems getting gphoto2 or even ubuntu to recognize that my usb camera (Radioshack FlatFoto 2.0 Megapixal) is existing.  It seems that the filesystem itself sees the camera but it isn't auto mounted and when I try to manually mount it, it mounts and fails to work correctly (meaning I am not getting any useful information, such as raw picture data or any data that I can make sense of).

The only idea I have to solve this problem is that possibly the device driver for the camera is not working (since, I am pretty sure it is experimental), and needs to somehow be edited.  If this is the case, could someone point me in the direction of learning how to write device drivers?

Any help on either figuring out the problem prior to possibly re-inventing the wheel or making a new wheel would be sweet, and please forgive me if I overlooked the thread that has the info I am looking for.  Thanks for the help

---

### Post by zerhacke on 2006-04-13
Help is here.

Your camera uses the SMAL chipset.  Installing libgphoto2 should take care of it.  Let me know if it does not.

At a terminal input

```
sudo apt-get install libgphoto2
```

And press enter.

---

### Post by thantos on 2006-04-13
I have libgphoto2.  I do not known why, but the usb doesn't auto mount, gthumbs doesn't recognize that there is a camera plugged into a usb port, and when I go to where it appears the camera is mounted (/proc/bus/usb) I don't get any useful information.  So any other suggestions?

---

### Post by zerhacke on 2006-04-13
Have you tried to use a known working USB device in that USB slot?  This would be to troubleshoot to find out if the USB slot is working.  Alternatively, does the camera work on a Windows machine?

---

### Post by thantos on 2006-04-14
Ok, both USB ports are working just fine and linux realizes that there is stuff plugged  
in to the port that my camera is plugged into; however, linux doesn't realize that it is a camera.  I checked the my USB plugs with another device (trackball) and said device works just fine.  

Yes, the camera does work on windows systems (at least on Windows 2k, but I have no desire to use windows to get my pictures, so next solution, please.

Oh, and thanks Zerhacke for your time and possible solutions (in the future I will post what I have already tried so as to not waste the time of others, sorry about that).

---

### Post by thantos on 2006-04-14
I think that the problem is that my the pci controllers that control the bus, are not working correctly.  Well, I suppose a better way of putting it is as devices, they are unkown.

this is the output of using the command lspci editing it to only show usb info:

[COLOR="Blue"]
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0084 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 0088 (rev a2)
[/COLOR]

well, I know that having an unkown device means very little (one of the other pci devices works just fine and is an unknown device), but could this have anything to do with my problem?

---

