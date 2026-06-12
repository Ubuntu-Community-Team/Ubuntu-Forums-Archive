---
title: "Creative Live! cam always on"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by archivator on 2007-04-14
I recently bought a Creative Live! Cam VideoIM and have had no troubles using it in Windows. In fact, thanks to the gspca driver, I got it up and running in no time in Linux too. However, I just recently realized that something I had taken for granted was actually some kind of a bug.

So.. the camera has a LED indicating its status. The LED should be green in standby and red in capturing mode. In Windows, it  strictly follows this behaviour (though, it becomes red during boot up). In Linux, however, the LED was always red. The only solution I found to this problem was to open up gqcam and then close it which in turn would turn off the camera completely (meaning, the LED would be turned off, too). I thought that was a buggy part in the gspca driver and just ignored it, enjoying the flawless video support the driver provided.

Recently, with all the kernel troubles in feisty, I was forced to install the kernel that comes with the Edgy Knot 3 Live CD (2.6.17-7). I was quite surprised when I first used this kernel as the camera's LED was green instead of the usual red. Thus, I concluded that for some reason the newer kernels initialize all devices, ignoring their standby capabilities. Or something like that.

Is there any way I can save myself opening and closing gqcam every time I boot into Ubuntu?

---

