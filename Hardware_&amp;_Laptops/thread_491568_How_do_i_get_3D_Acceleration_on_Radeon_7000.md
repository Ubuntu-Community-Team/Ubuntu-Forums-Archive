---
title: "How do i get 3D Acceleration on Radeon 7000"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by molom on 2007-07-03
Hi,
I have a problem on making my ATI Radeon 7000 work on Ubuntu Feisty. I can't get 3D Acceleration or OpenGL to work. I suppose its because I don't have the drivers installed. I can't find the drivers, which is a big problem. Can somebody help me?

---

### Post by don durito on 2007-07-09
Hi,

i am using the same card on an thinkpad x31; this card is supported by the default kernel ati driver;

please try this 2 commands 
1. glxgears
this should give you a frame output with about 1000 frames

and try glxinfo | grep direct

which should give yout the output directrendering yes.

---

### Post by stchman on 2007-07-09
> **molom said:**
> Hi,
I have a problem on making my ATI Radeon 7000 work on Ubuntu Feisty. I can't get 3D Acceleration or OpenGL to work. I suppose its because I don't have the drivers installed. I can't find the drivers, which is a big problem. Can somebody help me?

Go to System--->Administration--->Restricted drivers.

Enable the restricted ATI drivers.  Simple, works on my ATI equipped laptop.

Once you have them enabled typing fglxgears will will let you know that OpenGL is working.

---

### Post by Prosthetic Head on 2007-09-18
I have an x31, unfortunatly I can't get 3d acceleration working, the restricted drivers applet says i don't need any and if i manually set to use fglrx X won't start!

~$ glxgears 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1283 frames in 5.4 seconds = 239.314 FPS
1243 frames in 5.2 seconds = 236.870 FPS
1582 frames in 5.1 seconds = 312.563 FPS

~$ glxinfo|grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

any help??
thanks :)

---

### Post by w4ett on 2007-09-18
Your card is not supported by the fglrx driver from ATI...the correct driver for your card is already included in Ubuntu.  xorg-driver-ati see:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"] "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
<Ctrl><Alt><Backspace> 
```

to restart X

This should  get you to a GUI desktop.

---

### Post by Prosthetic Head on 2007-09-19
That gave em back my GUI, but did not give me direct rendering or proper 3d acceleration. I used the driver called 'radeon' and that gave me 1200ish fps in glxgears and had Direct rendering support.
Thaks for the help, it got me looking in the right place :)

now to see if i can find a way to get compiz to work..

---

### Post by w4ett on 2007-09-19
Here's a good how to for compiz-fusion:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

