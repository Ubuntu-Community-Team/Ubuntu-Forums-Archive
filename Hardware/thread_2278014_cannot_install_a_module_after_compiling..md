---
title: "cannot install a module after compiling."
date: 2015-05-13
forum: Hardware
---

### Post by nos09 on 2015-05-13
Hey, guys I am trying to install a module called usbtv. I am running mythbuntu and the module included by default. But I need to edit it to add support for my device.

I even tried to compile the whole kernel but it seems useless in this case where I only require one single module, but I gave it a shot and my VM's HDD got full, nearly occupying 20gb of space before I stopped the process.

Then I decided to only build what I need, and I have tried so many things since then, but nothing seems to work out. And after 2 days of troubleshooting I come to you for aid. Hope you guys can help me out with this one.  

Here are the steps I followed. based on this post - [http://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module](http://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module) (note - I followed many guides but this is the last one on fresh source)

```

    cd new-src/
    apt-get source linux-image-$(uname -r)
    cd linux-lts-utopic-3.16.0/
    make oldconfig && make prepare && make scripts
    cp -v /usr/src/linux-headers-$(uname -r)/Module.symvers .
    nano drivers/media/usb/usbtv/usbtv-core.c 
    cd drivers/media/usb/usbtv/
    make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
    make -C /lib/modules/$(uname -r)/build M=$(pwd) modules_install

```

Now the last command module_install ends with an error here is the full output - 

```

root@x-VirtualBox:/home/x/new-src/linux-lts-utopic-3.16.0/drivers/media/usb/usbtv#  make -C /lib/modules/$(uname -r)/build M=$(pwd) modules_install
make: Entering directory `/usr/src/linux-headers-3.16.0-30-generic'
  INSTALL /home/x/new-src/linux-lts-utopic-3.16.0/drivers/media/usb/usbtv/usbtv.ko
Can't read private key
  DEPMOD  3.16.0-30-generic
make: Leaving directory `/usr/src/linux-headers-3.16.0-30-generic'
```

Now where do i go from here ??? Please provide suggestion, I am getting desperate!

---

### Post by dino99 on 2015-05-13
Sorry i can't propose a solution, but only some light about the "Can't read private key" error shown: it only means you are not the maintainer; so no worry about that one
[https://github.com/slavrn/gm12u320/issues/7](https://github.com/slavrn/gm12u320/issues/7)

it seems you are not alone trying to deal with usbtv  [http://ubuntuforums.org/showthread.php?t=2259081](http://ubuntuforums.org/showthread.php?t=2259081)  [http://ubuntuforums.org/showthread.php?t=2217493](http://ubuntuforums.org/showthread.php?t=2217493)

---

