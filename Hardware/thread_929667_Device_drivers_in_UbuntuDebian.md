---
title: "Device drivers in Ubuntu/Debian"
date: 2008-09-25
forum: Hardware
---

### Post by nisarg on 2008-09-25
Hi all,

I was looking for some help in searching for some good guides/Wiki on installing and maintaining device drivers under Debian.
I have not been a Ubuntu/Linux user for too long, only about 10-12 months now. Can do a bit of basics though. I have been using Ubuntu Gutsy and now Hardy with Compiz,Emerald,Avn on IBM T40 with 512 RAM and 1.2GHz Mobile processor. And it occurred to me things under the hood of my machine were slightly cluttered, and then decided to do things the tough way, the geek's way. So I have got the latest version of Debian net install and plan to run it with XFCE and other eye-candies like AVN and Compiz. 
Anyways, thats the background  - So now to cut the long story short - Can someone please point me to some guides on understand how devices are managed/works under Linux? And more importantly managing device drivers. I understand a lot of devices should work right out of the box? 

Enlighten me please!!

Thanks.

---

### Post by Sef on 2008-09-25
> I understand a lot of devices should work right out of the box? 


Yes that is correct.  If you want to know if something of yours or want to get will work google or ask in the forums.

---

### Post by nisarg on 2008-09-25
Cheers. Thats helpful.

I was wondering how would I go about configuring devices, upgrade drivers etc..
For instance on Debian minimal install - my wifi doesn't seem to work as of yet.. (i haven't spent a lot of time yet either) i have tried madwifi,etc but it wont connect. its an Atheros chipset... 
And my main idea behind getting low with minimal system like Debian is to learn more and build my own system. so I really want like to understand this a bit better.

Your inputs are appreciated.
Thanks.

> **Sef said:**
> Yes that is correct.  If you want to know if something of yours or want to get will work google or ask in the forums.

---

### Post by kerry_s on 2008-09-25
[http://www.newt.com/debian/thinkpad-t40p/](http://www.newt.com/debian/thinkpad-t40p/)

---

### Post by IntuitiveNipple on 2008-09-25
It all starts when the kernel is configured, before it is built.

The [Ubuntu git kernel repository](https://wiki.ubuntu.com/KernelGitGuide) contains the Debian package build scripts and other resources in ./debian/, such as the kernel config files for the various architectures and flavours. These are combined at [build-time](https://wiki.ubuntu.com/KernelMaintenance) into the file the kernel expects, **./.config**

A config file contains text options of the form:
```

CONFIG_SOME_OPTION=y
# CONFIG_ANOTHER_OPTION is not set

```
The values that can be assigned to an option are controlled by files named **Kconfig** in the sub-directory where the particular option's code lives. See the kernel's **[Documentation/kbuild/kconfig-language.txt](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=blob;f=Documentation/kbuild/kconfig-language.txt;h=616043a6da99a0afd945e3cb5acb93b26bbb3f17;hb=refs/heads/master)**. For example, **[drivers/usb/gadget/Kconfig](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=blob;f=drivers/usb/gadget/Kconfig;h=f81d08d6538b6d34ce9d112a18de3dec909d096f;hb=refs/heads/master)** contains, in part:
```

config USB_GADGET
        tristate "Support for USB Gadgets"


```
A tristate value is one of **n**, **y**, or **m** (no, yes or module). It controls what object files are built by the rules in the **Makefile** in the same directory.
[list]
[*] No means don't include this object-code.
[*] Yes means include this object-code, and build it into the kernel image itself.
[*] Module means include this object-code, but build it as a dynamically loadable module.
[/list]
Modules (whether built-in or dynamically loadable) that support hardware devices declare the PCI or USB device IDs (via a **struct usb_device_id**) array of known IDs (See [example](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy.git;a=blob;f=drivers/media/video/ov511.c;h=d55d5800efb463cb19de27ac6ecd670bbfd6152f;hb=refs/heads/master#l210)).

When the kernel is built and installed, **depmod** is executed and it generates tables (in text form) listing all the registered device IDs and the module that supports each. These can be found in the directory **/lib/modules/$(uname -r)/** as **modules.pcimap** and **modules.usbmap**.

When the kernel discovers a new device, if the driver module is dynamically loadable the fires an event that a user-space helper picks up (through udev) that causes the module to be loaded.

modprobe handles this functionality. It uses the files in **/etc/modprobe.d/** to decide what to do. These range from ignoring the module load request due to a blacklist entry to loading a different module based on an alias.

Any module-specific command line options are then read from **/etc/modprobe.d/options** and the module is loaded and passed any options.

The module then registers and initialises itself, and the kernel core calls it to deal with the hardware device.

---

