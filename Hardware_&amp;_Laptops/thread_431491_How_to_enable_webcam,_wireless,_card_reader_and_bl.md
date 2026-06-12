---
title: "How to enable webcam, wireless, card reader and blue tooth of ASUS F3Jc laptop?"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by chunchengch on 2007-05-03
Ubuntu 7.04 is working fine on my ASUS F3Jc laptop except the built-in webcam, card reader, wireless and blue tooth , I am just a linux newbie, I really don't know how to make those working? should there be any solution? thanks!

---

### Post by jjordan on 2007-05-03
There are solutions but they may take a bit of effort and research to implement.  

Here is a place to start:
[http://gentoo-wiki.com/HARDWARE_Asus_F3JC](http://gentoo-wiki.com/HARDWARE_Asus_F3JC)

and here is another:
[http://gquintana.free.fr/laptop/asus_f3jc/kubuntu-6.10.html](http://gquintana.free.fr/laptop/asus_f3jc/kubuntu-6.10.html)

And here is one in Italian.

-j

---

### Post by jjordan on 2007-05-03
sorry,

the Italian site:
[http://gquintana.free.fr/laptop/asus_f3jc/kubuntu-6.10.html](http://gquintana.free.fr/laptop/asus_f3jc/kubuntu-6.10.html)

-j

---

### Post by chunchengch on 2007-05-04
Hi jjordan,

Thanks for valuable information, however I don't know how to "compile"?



----------------------------------------------------------------------------------------------------------------------------------
At first you need to **compile** in videodev in your kernel, preferably in module format:
Linux Kernel Configuration: Kernel 2.6.19-gentoo-r4

Device drivers  --->
  Multimedia devices --->
     <M> Video For Linux
     [ ] Enable Video For Linux API 1 (DEPRECATED)
     [*]   Enable Video For Linux API 1 compatible Layer
         Video Capture Adapters  --->
         Radio Adapters  --->
         Digital Video Broadcasting Devices  --->
     < > DABUSB driver

Under Video Capture Adapters and DVB I have checked almost all available drivers but it is your personal choice and you may wish to do not include any of them. Compile as always.
----------------------------------------------------------------------------------------------------------------------------------

---

### Post by chunchengch on 2007-05-06
I found an article may be useful for installing webcam, but I experienced problem when tried to execute

sudo ln - s /usr/src/linux-source-2.6.20 /usr/src/linux

I can not find directory or file "linux" under /usr/src:confused: , in which there are only 3 directories and 1 file as follows :

chun@paul:/usr/src$ ls
linux-headers-2.6.20-15          linux-source-2.6.20
linux-headers-2.6.20-15-generic  linux-source-2.6.20.tar.bz2

should anyone could help? thanks.

---

### Post by chunchengch on 2007-05-22
I finally enable my webcam, please refer to my another thread [http://ubuntuforums.org/showthread.php?p=2699093#post2699093](http://ubuntuforums.org/showthread.php?p=2699093#post2699093)

---

