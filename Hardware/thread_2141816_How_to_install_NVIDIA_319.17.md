---
title: "How to install NVIDIA 319.17"
date: 2013-05-03
forum: Hardware
---

### Post by SkylineGTR on 2013-05-03
Hi.

Can someone give me all the steps to install the new NVIDIA 319.17 drivers on Ubuntu 13.04?

[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)

Thanks.

---

### Post by kobayash1 on 2013-05-08
I'm not on 13.04, but I can tell you how I did it on my setup.

Log out.  Then Ctrl+Alt+F1.  Login.

sudo service lightdm stop
cd /path/to/nvidia.runfile
sudo ./nvidia.runfile

Go through installer.  Then when returning to prompt,

sudo service lightdm start

It didn't work for me the first time I did it, but that was on a PC that I had the proprietary drivers installed through the X-Swat PPA.  These steps worked for me on a fresh install with installed system updates.

---

### Post by Lightning Dragon on 2013-05-09
Hi,

I just installed that driver, and it is working perfectly fine. I have made a rather detailed post, but if you need any questions answered, please ask them. Please try;

[http://tinylink.net/24646](http://tinylink.net/24646)

(don't worry about tinylink; it is safe)

Oh, and make sure that is the right driver you need! :)

---

### Post by fr2632 on 2013-05-11
Check also here:

[http://www.thelinuxguy.nl/how-tos/how-to-install-the-new-stable-nvidia-driver-319-17-for-linux/](http://www.thelinuxguy.nl/how-tos/how-to-install-the-new-stable-nvidia-driver-319-17-for-linux/)

---

