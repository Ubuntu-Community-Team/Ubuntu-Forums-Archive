---
title: "Nvidia drivers don't persist across reboot"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by expostfacto on 2007-07-10
I've installed the latest Nvidia drivers from the Nvidia site.  X works fine.  But after a reboot it complains that the kernel module version does not match the driver version.  Re-running the installer fixes this, until the next reboot.

I think this happened because the first time I ran the Nvidia installer, I hadn't updated to the latest nvidia-glx package.  Now I have but the problem comes back after every reboot.

---

### Post by adam_kimber on 2007-07-10
I am not sure why you would want to install the drivers from the website? This is more difficult to accomplish and requires some command line fiddling. I am not sure how good you are. :P Ubuntu offers a restricted driver package to make installing nvidia drivers easier. If you are using Fesity Fawn there is even a restricted driver manager to tell you whether the driver is being used and is installed. Its under System --> Administration

Check out [Linux Nvidia HowTO]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") for more info on installing drivers. 

Hope this helps

Adam

---

### Post by expostfacto on 2007-07-10
The packaged drivers don't work for me, they are not new enough.

I tried the HOWTO's advice you linked and uninstalled nvidia-glx nvidia-kernel-common, didn't help.

I started over with a fresh system and eventually did get it to work.  I had to manually "rm /lib/linux-restricted-modules/.nvidia_new_installed" to get it to load the new kernel module rather than the old packaged one.  Perhaps I would not have had to do this if I had not initially installed nvidia-glx-new and later removed it.

---

### Post by dabl on 2007-07-10
If it breaks again, you might want to give the Envy script installer a try.  It comes from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Advantages:

1. It automatically removes the files that need to come out before it installs the driver.
2. He keeps it pretty up-to-date -- it has had the 100.14.11 driver version since June 22.
3. When a kernel upgrade breaks the driver, and you find yourself booted to a text prompt, all you need to do is ```
sudo envy -t
``` and you'll be back to your GUI in 20 seconds. :popcorn:

---

