---
title: "nVidia Quadro Installation help"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by chieferer on 2007-09-10
I recently aquired a brand new Latitude D630 with an nVidia Quadro NVS 135M graphics card.  I am aware that i need the proprietary driver from nVidia but what I need help with is the install.

It wont let me boot from the liveCD Or from a normal install.  I would really like to be able to use ubuntu so how would I go about installing ubuntu and/or installing the nVidia driver. I know you need wget(url) then sh (file) but how can I do that since I am not able to get to a console? Help is much appreiciated

In case it is useful, here are my system specs:

CPU: Intel Mobile Core2 Duo T7300 2GHz
Chipset: Intel GM965
GPU: nVidia Quadro NVS 135M
Display: 1280 x 800
RAM: 2GB DDR2
HD: 120GB Hitachi HTS722012K9A300 ATA

---

### Post by Bryon Speede on 2007-09-19
I had the exact same problem. When you get the error saying that X failed press <ctrl><alt><F1> to get to the console. You should now be able to enter your user name and password at the prompts. To get X running (in minimal mode) try the following:

edit /etc/X11/xorg.conf

Look for a section that looks like this:
```
Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nv"
EndSection

```

Change the "nv" to "vesa"
Save the file.

Type:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

X should start this time. Then you can go about setting up the rest of the system.

---

### Post by rybu on 2007-09-19
What Byron says should get you a usable GUI.  To get the native NVIDIA driver, go to the NVIDIA web page and find the appropriate driver for your computer. 

The current one for your system should be:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.19/NVIDIA-Linux-x86_64-100.14.19-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.19/NVIDIA-Linux-x86_64-100.14.19-pkg2.run)

Once you've downloaded that driver, see these instructions:

[http://ubuntuforums.org/showpost.php?p=3000269&postcount=28](http://ubuntuforums.org/showpost.php?p=3000269&postcount=28)

---

