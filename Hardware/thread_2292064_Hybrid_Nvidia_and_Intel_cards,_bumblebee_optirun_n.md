---
title: "Hybrid Nvidia and Intel cards, bumblebee optirun not working and OpenGL not being Int"
date: 2015-08-24
forum: Hardware
---

### Post by santiago87 on 2015-08-24
I have been fighting with the installation and correct usage of my Nvidia GTX960M together with an Intel i7-4720M CPU on Ubuntu 15.04.

I have followed lots of links on this website, on ubuntu wiki and on askubuntu (I will not add all the links here, since it's too much). At the beginning I had even problems with black screen after boot or no rebooting at all. After using proprietary drivers and fixing the "nomodeset" line in GRUB everything works more or less fine, but still I'm not satisfied, since apparently some people have managed to make it work. I just find that some solutions are either too old or they contradict themselves and lead to nothing. By trying all these things, at some point I also solved the ACPI PCC probe failed problem[4], I don't know how.

After following all the instructions to install [Bumblebee][1], checking other [instructions][2] and following the [troubleshooting][3] and even trying to edit my /etc/bumblebee/bumblebee.conf in all suggested ways, I still get messages like:

    $ optirun glxspheres
    [ 1844.581142] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
    [ 1844.581214] [ERROR]Could not connect to bumblebee daemon - is it running?

If I change some of my lines in /etc/bumblebee/bumblebee.conf I get other different errors.

Besides this, I see that my OpenGL renderer is not Intel:

    glxinfo|egrep "OpenGL vendor|OpenGL renderer*"
    OpenGL vendor string: VMware, Inc.
    OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits)

And I get very low performance and flickering when trying to work with visualization software. (I also see strange coloured pixels and flickering after the splash boot screen in Ubuntu). 

I also have no support for Unity3D and my OpenGL is software rendered:

    $ /usr/lib/nux/unity_support_test --print
    OpenGL vendor string:   VMware, Inc.
    OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits)
    OpenGL version string:  3.0 Mesa 10.5.2

    Not software rendered:    no
    Not blacklisted:          yes
    GLX fbconfig:             yes
    GLX texture from pixmap:  yes
    GL npot or rect textures: yes
    GL vertex program:        yes
    GL fragment program:      yes
    GL vertex buffer object:  yes
    GL framebuffer object:    yes
    GL version is 1.4+:       yes

    Unity 3D supported:       no


I have already tried to do stuff like:

    sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

But also unsuccessfully...


I add here some extra information on my devices.




[1]:[https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage](https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage)
[2]: [http://askubuntu.com/questions/36930/is-a-nvidia-geforce-with-optimus-technology-supported-by-ubuntu](http://askubuntu.com/questions/36930/is-a-nvidia-geforce-with-optimus-technology-supported-by-ubuntu)
[3]:[https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting#bumblebeed-module-nvidia-is-not-found](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting#bumblebeed-module-nvidia-is-not-found)
[4]: [http://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed](http://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed)



    lspci -vnn | grep '\''[030[02]\]'
    00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core    Processor Integrated Graphics Controller [8086:0416] (rev 06)   (prog-if 00 [VGA controller])
    01:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:139b] (rev a2)



    $ dpkg -l nvidia-\* | grep '^ii'
    ii  nvidia-346              346.59-0ubuntu1  amd64        NVIDIA binary  driver - version 346.59
    ii  nvidia-opencl-icd-346   346.59-0ubuntu1  amd64        NVIDIA OpenCL ICD
    ii  nvidia-prime            0.8.1            amd64        Tools to enable NVIDIA's Prime
    ii  nvidia-settings         346.59-0ubuntu1  amd64        Tool for configuring the NVIDIA graphics driver


Thanks for any help!! I am sure there has to be some satisfactory solution to all this.

---

### Post by efflandt on 2015-08-26
Not sure which nvidia drivers you need for that chip (or which versions are in 15.04 repos), but nvidia drivers now include nvidia-prime, so you should not even need bumblebee. You should be able to select which graphics to use from **NVIDIA X Server Settings**. For me switching from Nvidia to Intel graphics just requires relogging into X, but switching Intel to Nvidia requires reboot. One thing that I read in a post is that someone could not get hybrid Intel/Nvidia graphics to work on their laptop unless they did NOT use nomodeset (contrary to nvidia on desktops which usually need it). So I did not use nomodeset on my laptop and my older Intel HD 4600 / Nvidia GTX 765M works fine with nvidia-331-updates in Ubuntu 14.04.

But when I first installed a GTX 750 Ti (which has the Maxwell chip) in my desktop, GeForce Experience in Win7 could not tell the capabilities of that card (to optimize games) with what I think was 346 drivers (although it worked fine generally) until I upgraded that to what I think was Windows 347 drivers at the time. In Ubuntu 14.04 this card did not work with nouveau nor nvidia-current, but it worked with nvidia-331-updates. But I am currently using nvidia-352 from xorg-edgers ppa.

Your 960 chip is even newer than that. So maybe you should try purging nvidia-346 and installing nvidia-352 or nvidia-355 package (from a ppa if necessary) and getting rid of bumblebee. That is probably most easily done by booting to recovery mode, enabling networking (which also remounts your drive from read-only to read-write), and using the root console. Nvidia's website says that 352.30 supports your chip, and that is what nvidia-352 package installs (which would say 15.04 on your system):```
efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-352                                            352.30-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA binary driver - version 352.30
ii  nvidia-opencl-icd-352                                 352.30-0ubuntu0~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       355.06-0ubuntu0~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver
```

---

