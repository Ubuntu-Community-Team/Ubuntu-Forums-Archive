---
title: "restricted hardware"
date: 2008-10-16
forum: Hardware
---

### Post by cacharreo on 2008-10-16
Hi
How can I enable the nvidia restricted module from terminal?

---

### Post by Mark_in_Hollywood on 2008-10-16
FROM: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_restricted_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_restricted_drivers)

[COLOR="Red"]This information I give you is about HARDY HERON, ver. 8.04, so IF YOU HAVE something else, please double check:[/COLOR]

Install restricted drivers
[edit]
NVidia Driver

    * Determine what kernel you have running: 

user@localhost:~$ uname -a
Linux ubuntu804server 2.6.24-17-server #1 SMP Thu May 1 14:28:06 UTC 2008 x86_64 GNU/Linux

    * I have the server kernel, so I need to install the following: 

sudo apt-get install linux-restricted-modules-server

You can also install this package from Synaptic Package Manager (which I did.)

    * Go to System > Administration > Restricted Drivers Manager and turn on the driver. 

    * Reboot 

    * Some users may receive an error screen: "The software source for the packsge nvidia-glx-new is not enabled." This can be overcome by going to System > Administration > Software Sources and ticking all the boxes under the heading "Downloadable from the Internet", click close and then allow Ubuntu to reload the package lists. The NVidia drivers can then be enabled using the method above. 

    * You can optionally prevent showing NVidia logo on startup by: 

sudo nvidia-xconfig --no-logo

[edit]
Install latest EnvyNG driver (ATI & nVidia)

    * Ensures you are always running the latest version of the drivers.
    * Read this faq. 

    * Install the gtk package: 

 sudo apt-get install envyng-gtk

[edit]
Install drivers from the repository (ATI & nVidia)

    * From Synaptic Package Manager: 

 System --> Administration --> Hardware Drivers

    * Choose your Graphics Card and desired options. 

    * Reboot.

---

