---
title: "broadcom wireless driver and nvidia optimus support in ubuntu"
date: 2012-12-18
forum: Hardware
---

### Post by vivek1729 on 2012-12-18
I have been trying to completely shift to ubuntu for almost 2 years now. I have tried all the ubuntu distros starting from 10.04 through 11.10, but there have always been some bugs with the display drivers or the wireless cards not being recognised and the additional drivers suggested from the ubuntu community not doing the trick.

I tried a lot to fix bugs, checked a lot of forums, launch pad, got some of them fixed, but could not really get a neat and complete ubuntu machine set up till now. Now I really like the whole open source community and the linux platform, my pc at home runs ubuntu 11.04 perfectly but there have been some glitches always with ubuntu on my laptop that has forced me to stick with windows only which is sad :(.

Now I am currently on an hp dv6 laptop that has the broadcom bcm4313 wireless driver and the nvidia 630gtm graphics(optimus) driver. Now I tried to do some research on the support of these drivers in ubuntu machines but could not get anywhere. So I would really appreciate if you guys could suggest some linux distro that I could use that has full support of these drivers or has stable bug fixes for these kind of issues. I tried precise pangolin (LTS) through a live CD but i still see a problem with wifi networks which is a little frustrating. 

Now I would be the happiest person if somebody could point me in the right direction and help me figure out the suitable ubuntu distribution for this configuration!

---

### Post by grahammechanical on 2012-12-18
In my opinion any Linux distribution will support Linux drivers. The issue is are the drivers capable of fully supporting the hardware?

Nvidia Optimus technology has been used on motherboards for some months but Nvidia has only just announced that it will start developing Linux drivers for this technology.

For commercial reasons corporations like Nvidia do not release technical details of how their hardware works. So, Linux developers have to produce drivers without any or with little help from the copyright or patent holder of the hardware. And they have to develop these drivers without becoming illegal in the process.

It is frustrating I know but this is life using Linux.

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

> Linus Torvalds, the Linux kernel maintainer, in his famous finger-giving-to-Nvidia speech, criticized the company as being "the single worst company we've had to deal with" because it provided no support for Optimus laptops

[http://en.wikipedia.org/wiki/Nvidia_Optimus]("http://en.wikipedia.org/wiki/Nvidia_Optimus")

[http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html]("http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html")

Don't get your hopes up. I stopped using Nvidia drivers on my machine because updates to newer drivers broke the installation.

As for Broadcom, note the date of this post

[http://www.pcworld.com/article/205258/linux_wifi_gets_easier_with_new_broadcom_driver.html]("http://www.pcworld.com/article/205258/linux_wifi_gets_easier_with_new_broadcom_driver.html")

> Wireless networking has long been a sticking point for Linux users with netbooks and laptops including Broadcom chipsets, which have traditionally used proprietary drivers that don't work with Linux. 

Regards.

---

### Post by vivek1729 on 2012-12-18
Thanks a lot for your quick and helpful response @grahammechanical, I went through this article
[http://www.pcworld.com/article/205258/linux_wifi_gets_easier_with_new_broadcom_driver.html](http://www.pcworld.com/article/205258/linux_wifi_gets_easier_with_new_broadcom_driver.html), published in 2010 according to which broadcom bcm43XX drivers will be provided support for linux and that is true. However as i mentioned my issue has been that despite downloading the additional drivers suggested by ubuntu and blacklisting some other drivers in the modprobe.conf file(actually getting the wifi to work has been a lot of trouble).I had a really tough time especially with 11.10 , even after installing the drivers, the problem is not completely solved. So i uninstalled it and have been looking at upgrade options.

I am willing to do away with the graphics driver. But i really need my wifi card to be supported. Do you have any idea if the bcm 4313 specifically is supported out of the box in 12.04 or 12.10. Or are there some tested fixes for these bugs. I would really appreciate your help because I tried 12.04 with the live CD and the wifi signals were really weak and after a suspend and resume, the wifi started working again. But it was buggy. Is there any distribution in ubuntu that supports broadcom bcm 4313 drivers smoothly. I do not mind going back to 10.10 if it does frankly!

---

### Post by vivek1729 on 2012-12-20
Nobody knows if the broadcom bcm 4313 driver pre installed with the kernel works well with ubuntu 12.10 or not?

---

