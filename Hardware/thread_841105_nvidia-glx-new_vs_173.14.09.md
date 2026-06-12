---
title: "nvidia-glx-new vs 173.14.09"
date: 2008-06-26
forum: Hardware
---

### Post by lviggiani on 2008-06-26
Hi,
I have a big question...

I've seen that nVidia has recently released the latest linux driver ver 173.14.09 with added support for GeForce 8400M GS included in my notebook.
I currently have installed package nvidia-glx-new which includes driver 169.12 (that should not have support for my GPU) which worked fine so far.
So, what is best: 
1) installing 173.14.09 driver from nvidia web site?
2) keep nvidia-glx-new package from ubuntu?
3) or wait (if ever) that ubuntu community upgrades the nvidia-glx-package to latest available driver?

Thanks and ciao.

---

### Post by jetpeach on 2008-07-30
hmm, i'm curious about this too - did you decide and notice any performance increase with the newer nvidia driver?

---

### Post by Nepherte on 2008-07-30
I have a GeForce 8400M GS in my notebook as well. I seem to have a better performance with the latest driver (173.14.09). Everything now goes a lot smoother.

---

### Post by jimv on 2008-07-30
I noticed an improvement as well when I installed the new driver.  If you use EnvyNG, it will grab the new driver for you when you run it.

---

### Post by sdennie on 2008-07-30
The 8400M GS is supported just fine with the default Ubuntu drivers.  I don't recommend moving away from the default Ubuntu drivers unless you have some real need to do so.  If compiz performance is a bit sluggish, you may want to try this guide: [ HOWTO: Improve NVidia Laptop Graphics Performance]("http://ubuntuforums.org/showthread.php?t=828369")

---

### Post by Nepherte on 2008-07-30
It is true that I've switched to the latest driver because Compiz Fusion was sluggish. So you might want to try the above suggestion first if you're uncomfortable with installing the latest driver. Compiz Fusion aside, I did have a small but noticeable overall performance increase though.

---

### Post by blacksea on 2008-07-30
> **lviggiani said:**
> Hi,
I have a big question...

I've seen that nVidia has recently released the latest linux driver ver 173.14.09 with added support for GeForce 8400M GS included in my notebook.
I currently have installed package nvidia-glx-new which includes driver 169.12 (that should not have support for my GPU) which worked fine so far.
So, what is best: 
1) installing 173.14.09 driver from nvidia web site?
2) keep nvidia-glx-new package from ubuntu?
3) or wait (if ever) that ubuntu community upgrades the nvidia-glx-package to latest available driver?

Thanks and ciao.

the best and easy way is install envyng
sudo apt-get install envyng-gtk
then 
envyng -t 
then press 1 to install nvidia driver

---

### Post by -random on 2008-07-30
if you install the nvidia driver yourself, will you be notified when new updates are available? 

..i'm thinking long term ease of use > brand new top notch drivers..

---

### Post by evets25 on 2008-07-30
If you want the drivers to be updated along with everything else on your system and have everything go smooth, just go with the standard ubuntu packages, rather than the bleeding edge drivers that you need to install manually with each kernel update. The ubuntu package versions tend to lag behind the latest-beta-bleeding-edge-hot-new nvidia driver, but it's as was previously mentioned, unless you know of a specific issue that you are having that the new version will fix, it's not worth upgrading. Just wait for the new version to trickle down to the ubuntu repos; it will come eventually, don't worry. :)

---

