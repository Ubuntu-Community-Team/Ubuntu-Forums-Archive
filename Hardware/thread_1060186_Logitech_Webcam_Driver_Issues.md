---
title: "Logitech Webcam Driver Issues"
date: 2009-02-04
forum: Hardware
---

### Post by Houseplant on 2009-02-04
Edit: Please delete as I have fixed the problem. Sorry for any convenience!

---

### Post by cariboo on 2009-02-04
Unfortunately that driver will not work with anything newer than 8.04. If you are running Intrepid (8.10) then the driver is included in the kernel. Below is a listing of the drivers:

```
lsmod | grep spca
gspca_zc3xx            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32
``` 

You can install xawtv to be able to use the webcam. Xawtv is in the repositories and you can use Synaptic Package Manager to install it. Once it is installed, for testing purposes open a Applications-->Accessories-->Terminal and type:

```
sudo xawtv -c /dev/video0
```

If you don't have a tv tuner card the device should be video0

If the above command works, edit the xawtv launcher in Apllications-->Sound & Video to the command above.

Edit: change the sudo to gksu in the above command.

Jim

---

