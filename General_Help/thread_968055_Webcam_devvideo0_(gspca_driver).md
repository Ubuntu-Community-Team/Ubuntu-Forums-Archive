---
title: "Webcam /dev/video0 (gspca driver)"
date: 2008-11-02
forum: General Help
---

### Post by Ferrat on 2008-11-02
I've seen a lot of people having trouble with their webcams after updating to Ibex, I had similar problems with my PC-CAM 300 that has been working without problems on Ubuntu for a long long time. 



here is a list of cams working with this driver
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678)
Shows a problem with /dev/video0 not being there even when the driver loads ok but when looking around not only this but a lot of drivers seem to have similar problems and some had solutions, some didn't. 

What I did what just to check what module was loaded for my cam, in my case **gspca_main** and **gspca_spca500**.

to check this (since you need to restart it just open a terminal and write
```

**sudo modprobe -r gspca_** 
```

then hit tab and you should get the output 

**gspca_main** ......  **gspca_xxxxxx**  (xxxxx = the driver for your cam)

now finish your input ```

**sudo modprobe -r gspca_xxxxxx** 
```

then just run 
```

**sudo modprobe gspca_xxxxxx** 
```  (same but no -r switch)

and now check if you got a /dev/video0 

```

**ls /dev/vid***

```

if you get the output 
**/dev/video0**
then you are good to go and your webcam should work as it was intended. 

you might have to do this everytime you restart (haven't checked yet, will get back to you on that). 

also this could work for other drivers (but ofc then you modprobe those drivers not gspca_ drivers) as well it seems that register as they should but you don't get a /dev/video0 since it seems to be a problem with the kernel (Debian has the same problem as Ubuntu) not loading the modules correctly at start up.

---

### Post by panteraz on 2009-12-16
Thanks a lot!!! I have the same webcam (Creative PC-CAM 300) and it work as you described.

Can you know how to do this permanent?

---

