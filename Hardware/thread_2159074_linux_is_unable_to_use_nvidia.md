---
title: "linux is unable to use nvidia"
date: 2013-07-01
forum: Hardware
---

### Post by G1adiss on 2013-07-01
I have 2 grafic cards:
-integrated intel HD 4000
-external nvidia geforce 635m

When I want to install nvidia drivers in ubuntu software center, I get this error:

[IMG]http://i44.tinypic.com/oa3q87.png[/IMG]

So I've decided to install it manually. But there are more errors:

[IMG]http://i41.tinypic.com/296izd.png[/IMG]

[IMG]http://i40.tinypic.com/1pgtj4.png[/IMG]

[IMG]http://i42.tinypic.com/o0s7y8.png[/IMG]

[IMG]http://i43.tinypic.com/zwxlqh.png[/IMG]

Could someone help me?? I'm beginer in linux and I have no idea...

---

### Post by Bashing-om on 2013-07-01
G1adiss; Hi ! Welcome to the forum.

That is a tough introduction to ubuntu ...
Nvidia does not offer support for hybrid (split) graphics and as such ubuntu does not cope well either....
One option - not generally recommended - is to disable one of the graphics components ... pros and cons and result is not a good graphical experience and/or hard on the hardware. 
With Intel/Nvidia -> optimus == BumbleBee.
Many have had success with BumbleBee, I have seen good report .. the downside is that one must learn to work with BB when switching graphic modes.

Can be done: starting info here ..
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) 
Additional info is available on the forum in respect to BumbleBee and as well info is plentiful; Google search term "bumblebee ubuntu" gets ya all kinds of returns; In order for you to make an informed decision as to what you want to do.

[INDENT][INDENT]seek and ye shall find, we will answer questions[/INDENT][/INDENT]

---

### Post by grahammechanical on 2013-07-01
The install of Nvidia 173 failed because it is an old driver that existed before your hardware was released and the OS also has a newer Xserver than the driver expects to find. Nvidia 173 depends on X11-common version 1.7.0.0 but X11-common 1.7.7 (a later version) is to be installed. This is because you are using a newer version of Xubuntu.

Have you tried activating a video driver through a system utility? I do not know what it is called in Xubuntu but it is called Additional Drivers in Ubuntu. The drivers listed there are matched with the Linux kernel that is in use in your OS. I myself have installed Nvidia 319.32 through the Additional Drivers utility. 

If you are using Xubuntu 13.04 then at the moment Nvidia 319.32 is perhaps the best available. Try installing through Additional Drivers. It is not perfect for Nvidia Optimus technology but that is because Nvidia has been slow to provide a driver that will run Optimus.

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

That link is about Nvidia 319.12 but 319.32 is later. So there may have been improvements.

This link is about Bumblebee. Note the link to Bumblebee Configurator GUI

[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

Oh, one more thing, when we use an Nvidia driver we get an Nvidia Xserver settings utility. It will be available through one of the Xubuntu menus.

Regards.

---

### Post by G1adiss on 2013-07-02
> **grahammechanical said:**
> The install of Nvidia 173 failed because it is an old driver that existed before your hardware was released and the OS also has a newer Xserver than the driver expects to find. Nvidia 173 depends on X11-common version 1.7.0.0 but X11-common 1.7.7 (a later version) is to be installed. This is because you are using a newer version of Xubuntu.

Have you tried activating a video driver through a system utility? I do not know what it is called in Xubuntu but it is called Additional Drivers in Ubuntu. The drivers listed there are matched with the Linux kernel that is in use in your OS. I myself have installed Nvidia 319.32 through the Additional Drivers utility. 

If you are using Xubuntu 13.04 then at the moment Nvidia 319.32 is perhaps the best available. Try installing through Additional Drivers. It is not perfect for Nvidia Optimus technology but that is because Nvidia has been slow to provide a driver that will run Optimus.

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

That link is about Nvidia 319.12 but 319.32 is later. So there may have been improvements.

This link is about Bumblebee. Note the link to Bumblebee Configurator GUI

[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

Oh, one more thing, when we use an Nvidia driver we get an Nvidia Xserver settings utility. It will be available through one of the Xubuntu menus.

Regards.

there are no drivers listed

[IMG]http://i40.tinypic.com/2exyeyd.png[/IMG]

---

### Post by G1adiss on 2013-07-02
> **Bashing-om said:**
> G1adiss; Hi ! Welcome to the forum.

That is a tough introduction to ubuntu ...
Nvidia does not offer support for hybrid (split) graphics and as such ubuntu does not cope well either....
One option - not generally recommended - is to disable one of the graphics components ... pros and cons and result is not a good graphical experience and/or hard on the hardware. 
With Intel/Nvidia -> optimus == BumbleBee.
Many have had success with BumbleBee, I have seen good report .. the downside is that one must learn to work with BB when switching graphic modes.

Can be done: starting info here ..
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) 
Additional info is available on the forum in respect to BumbleBee and as well info is plentiful; Google search term "bumblebee ubuntu" gets ya all kinds of returns; In order for you to make an informed decision as to what you want to do.
[INDENT][INDENT]seek and ye shall find, we will answer questions[/INDENT]
[/INDENT]


I've tried it, maybe I did some mistake but there are no changes. Nvidia is not running

---

### Post by Bashing-om on 2013-07-02
G1adiss; Your last ->
You mean that you have installed the Bumblebee ppa ... installed BumbleBee and can not get BumbleBee to configure your graphics ?
Have a read in this thread, about 2/3 rds of the way into it is a discussion of hybrid graphics neglecting the use of BumbleBee. Some other options are presented.
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86)

[INDENT][INDENT]I be try'n to help
[/INDENT][/INDENT]

---

### Post by G1adiss on 2013-07-03
gladiss@gladiss-Lenovo-G580:~$ sudo su
[sudo] password for gladiss: 
root@gladiss-Lenovo-G580:/home/gladiss# optirun '/home/gladiss/.wine/drive_c/Program Files (x86)/Activision/Call of Duty 4 - Modern Warfare/iw3mp.exe'
/usr/bin/vglrun: 303: exec: /home/gladiss/.wine/drive_c/Program Files (x86)/Activision/Call of Duty 4 - Modern Warfare/iw3mp.exe: Permission denied
root@gladiss-Lenovo-G580:/home/gladiss#

---

### Post by Bashing-om on 2013-07-03
G1adiss;

I have no experience with either optimus -> BumbleBee nor with "wine". Nor do I have any hardware means to set up and test your condition.  Very little I can advise now.
Unable to advise as to why "sudo -su" results in a permission issue with "vglrun".

In the event that none other responds to this thread ... I respectfully suggest that you inquire in the wine subforum for a directive.

[INDENT]sometimes I wonder, other times I just do not know[/INDENT]

---

### Post by G1adiss on 2013-07-03
ok I'll try to ask people in the wine subforum, thanks for helping me

---

### Post by jp734 on 2013-07-04
Hello, not sure if this is solved.

Are you trying to use both cards at the same time for multi screen purpose? Is your BIOS setup to use the integrated video as the primary? If you only want to use the nvidia card, you might want to check the BIOS and set PCIe as your primary card before installing the driver.

I have a desktop with an integrated Intel video and a radeon card. I was trying to setup a multi screen and I wasn't able to with the integrated video activated. I had to choose PCIe as my primary device. Hope this help if you haven't solved this yet.

---

### Post by G1adiss on 2013-07-08
> **jp734 said:**
> Hello, not sure if this is solved.

Are you trying to use both cards at the same time for multi screen purpose? Is your BIOS setup to use the integrated video as the primary? If you only want to use the nvidia card, you might want to check the BIOS and set PCIe as your primary card before installing the driver.

I have a desktop with an integrated Intel video and a radeon card. I was trying to setup a multi screen and I wasn't able to with the integrated video activated. I had to choose PCIe as my primary device. Hope this help if you haven't solved this yet.

I don't want to use multiscreen, I want to use integrated intel card on desktop and nvidia for exe programs (such as windows games)

---

### Post by dannyboy79 on 2013-07-08
as others have said, linux is behind when it comes to that sort of configuration. you can check this out: [http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car](http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car)
you'll need to use 1 or the other. If it were me, i'd go with the nvidia card and run the 319.32 driver. also, if you really want to play Call of Duty and get decent performance you may want to dual boot and play COD in windows as running games intense like that thru wine isn't really that good.

---

### Post by G1adiss on 2013-07-09
> **dannyboy79 said:**
> as others have said, linux is behind when it comes to that sort of configuration. you can check this out: [http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car](http://askubuntu.com/questions/131506/how-can-i-get-nvidia-cuda-or-opencl-working-on-a-laptop-with-nvidia-discrete-car)
you'll need to use 1 or the other. If it were me, i'd go with the nvidia card and run the 319.32 driver. also, if you really want to play Call of Duty and get decent performance you may want to dual boot and play COD in windows as running games intense like that thru wine isn't really that good.

I have installed windows too but I want to get rid of it and use only linux. How to set up bumblebee is very hard to me because I get a lot of errors and I don't understand them at all. All solutions are unreachalbe for me because I don't understand it, I'm total noob in this stuff

---

### Post by G1adiss on 2013-07-10
OK, I've tried to install the game in linux into .wine directory. It looked fine, it was launching the game but after that launching stopped and I saw this errors (and my desktop changed it's resolution)

[IMG]http://i43.tinypic.com/zjf15e.png[/IMG]

---

