---
title: "Problem with GeForce Go 7600"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by nto on 2006-12-09
Hi everybody!

A couple of my friends have been using Ubuntu for a long time now, so I figured I'd try it on my new laptop, a Zepto 6214W. I installed the newest BIOS prior to installing Ubuntu 6.10 on it. Everything but the graphics driver works fine. I've tried to install the nvidia driver in a couple of different ways. I tried both Method 1 and 2 at [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy")
and I tried by just installing nvidia-glx and nvidia-glx-dev with apt-get.

My problem is that whenever I installed it, I get a black screen when I restart gdm, it's as if it doesn't find my screen after I switch to nvidia driver from the nv driver.

the nv driver works though, but I really want to get the Nvidia driver working instead.

I know that there are problems with Nvidia drivers recognizing it's own 7600 hardware, so I also tried installing the "fixed" driver from this page: [http://www.laptopvideo2go.com/forum/index.php?showtopic=12069]("http://www.laptopvideo2go.com/forum/index.php?showtopic=12069")
But that gave me a strange error:

: 896: ==: unexpected operator
                         make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'. Stop.
make: *** [print-module-filename] Error 2

I don't know what it means, and neither did any of my friends. Can anyone please help me? I'm enjoying using Ubuntu but I would really like to have these drivers installed :)

---

### Post by anti_microsoft on 2006-12-09
I have used Linux and NVidia for many years. The problem you are having is the kernel was compiled using a different version of gcc then the driver. What you need to do is learn howto recompile your kernel with a gcc version and recompile your NVidia drive. MAny places give instructions on howto compile a kernel. If you know your hardware really well compiles are a breeze. Some people find this part of linux scary, just take your time and double check as you compile and you will be fine.

---

### Post by nto on 2006-12-09
Thanks a lot, will try that. :)

Hopefully I'll be able to do it :D

---

