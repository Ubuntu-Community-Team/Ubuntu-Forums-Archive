---
title: "Dell Inspiron 3521"
date: 2016-04-04
forum: Hardware
---

### Post by Ancinene on 2016-04-04
Hi. I have got a Dell Inspiron 3521 which is Ubuntu Certified. Spec.: CPU I3-3217u, GPU HD 4000 integrated, AMD 7670m 1gb. I do not like Windows 10, even I hate them. I wanted to use Ubuntu 14.04 so I tried to install them. It was succesfull, but when I restarted the system, it was very slow. I wanted to install the proprietary driver of the AMD GPU  and it said the installation was succesfull, then I restarted them, but after that the system became unstable. The crashes were usually and a lot of program did not want to work because of libGL error...I can not remember them because, after I tried every possible solution in wain, I have installed Windows 10, but it is a disaster.

---

### Post by Bucky Ball on 2016-04-04
Welcome. And your question is?

Whatever it is, you will have a better chance of getting support for it with a descriptive title. You can change it by editing the first post and 'Go Advanced'.

---

### Post by Ancinene on 2016-04-04
My question is that how can I fix this problem? I do not want to use Windows, but I am not able to use Ubuntu.

---

### Post by oldfred on 2016-04-04
There is this:
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html) 

I installed to a Dell SFF 3647, but that just uses Intel Video
[http://ubuntuforums.org/showthread.php?t=2275234&p=13272233#post13272233](http://ubuntuforums.org/showthread.php?t=2275234&p=13272233#post13272233)
[http://ubuntuforums.org/showthread.php?t=2284510&p=13312922#post13312922](http://ubuntuforums.org/showthread.php?t=2284510&p=13312922#post13312922)


 When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu

---

