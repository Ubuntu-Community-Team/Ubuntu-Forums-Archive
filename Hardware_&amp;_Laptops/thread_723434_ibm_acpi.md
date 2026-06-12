---
title: "ibm acpi"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by thischarmingman on 2008-03-13
Hi

I recently just upgraded my ibm t40 thinkpad with a bluetooth/modem combo card. I believe I need to install the acpi drivers. I have downloaded the version correct for my linux kernel but am a bit stuck on how to install it. Anyone have any ideas on how to do this successfully or if there is some other way to get the bluetooth enabled? Thanks muchly!

---

### Post by unutbu on 2008-03-13
Did you download a patch file? a tar.gz file?
If it is a patch file, it is meant to be run thru patch, to alter the linux kernel source code. You would then compile a new kernel, install it in /boot, and tell grub how to boot it.

If it is a tar.gz or tar.bz2 file, then you'll want to uncompress and untar it and then follow the directions, usually in a file called README or INSTALL.

---

### Post by thischarmingman on 2008-03-13
Its a .tar file. I extracted it but the only file i get is 'thinkpad-acpi-0.18-20071203_v2.6.22.14.patch.gz'

I'm pretty clueless on what way I install this. A beginners guide would be appreciated!

---

### Post by unutbu on 2008-03-13
Follow the instructions at
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

If you run into any problems, you can post here and we'll try to help you.

---

### Post by unutbu on 2008-03-13
If you choose to follow the link above, I would recommend *not* logging in as root.
Root powers should be used as sparingly as possible. It is entirely possible to compile kernels as a normal user, and so you should compile the kernel as a normal user. The only steps where you need root powers is when using apt-get (type 'sudo apt-get') or installing the kernel (sudo dpkg -i).

---

### Post by thischarmingman on 2008-03-13
> **unutbu said:**
> Follow the instructions at
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

If you run into any problems, you can post here and we'll try to help you.

I'm kinda confused. Do I have to update my kernel in order to install the ibm patch? I don't really want to go ahead with anything in fear of messing up my system.

---

### Post by unutbu on 2008-03-13
Maybe you can get what you want without having to compile anything.

Do you have the "Integrated Bluetooth II with 56K Modem (BMDC)" 
IBM FRU PN: 26P8396, 91P7259, 91P7315?

If so, perhaps this is the page for you:

[http://www.thinkwiki.org/wiki/IBM_Integrated_Bluetooth_II_with_56K_Modem_(BMDC](http://www.thinkwiki.org/wiki/IBM_Integrated_Bluetooth_II_with_56K_Modem_(BMDC))

It appears the kernel you already have may have the thinkpad-acpi built in and it is just a matter of enabling it.

Here are some commands that might be helpful
```

locate thinkpad

```       
This will show you all the files on your system with the string 'thinkpad' in it.

If your system is like mine, one of the files will be 
```

/lib/modules/2.6.22-14-generic/kernel/drivers/misc/thinkpad_acpi.ko

```

By the way, the thinkwiki url above mentions an ibm_acip kernel module. I think it has been renamed thinkpad_acpi... (See [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg415208.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg415208.html))

If you are using a version of Ubuntu other than Gutsy, your kernel version will probably be something other than 2.6.22-14, in which case your file name will be slightly different
(but hopefully still present).

This file, I believe, is the driver you would have been compiling with that patch you downloaded.

Let's be optimistic and assume you have this driver on your system already.
That doesn't mean the driver is already loaded into your kernel. 
To test that the driver is loaded, type this in a terminal:

```

lsmod | grep thinkpad_acpi

```

If it is loaded, you should get some output back. If you get no love, then try this:
```

sudo modprobe thinkpad_acpi

```

The modprobe command should add the thinkpad_acpi module to the kernel.
If everything went well, 
```

lsmod | grep thinkpad_acpi

```
should now give you some feedback. If that's the case, then all you need to do to enable
bluetooth (and here I'm just parroting the thinkwiki) is:

```

echo enable > /proc/acpi/ibm/bluetooth

```

---

### Post by Whiffle on 2008-03-13
That driver is usually compiled already, you shouldn't have to compile it yourself.

---

### Post by thischarmingman on 2008-03-17
Thank you all for your advice. In the end turned out I had forgot to attach the antenna to the bluetooth card. Bit of a thick moment. Live and learn!

---

