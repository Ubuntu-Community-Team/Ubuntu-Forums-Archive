---
title: "Driver Installation Help"
date: 2014-12-21
forum: Hardware
---

### Post by Jared_French on 2014-12-21
My linux knowledge is fairly basic and I've never had to install a driver before so I'm having some problems as I don't know what to do.  I have a USB ethernet adapter and the driver file for it, but I don't know how to compile and install it.

The read me says:

>   USBKR-100 on linux is as follows:

  step 1: compile:
       gcc -DMODULE -D__KERNEL__ -c rtl8150.c -I/usr/src/linux-2.4.0/include/
           *linux-2.4.0 will change according to the kernel version
           
  step 2: insert the driver as module:
           insmod rtl8150.o        
           (run 'lsmod' to see if the module is inserted)


  step 3: bind your card to an IP address:


           /sbin/ifconfig eth0 ${IPADDR} netmask ${NETMASK} broadcast ${BROADCAST} 
           (run 'netstat -i' to see if there is a interface 'eth0')


  step 4: add your card to IP routing table and add gateway:
       /sbin/route add default gw ${GATEWAY} dev eth0




*make sure that your kernel is version 2.4.0 or next version.
 Otherwise, you have to    upgrade your kernel.
 ([http://www.kernel.org/pub/linux/kernel/v2.4](http://www.kernel.org/pub/linux/kernel/v2.4)) 

And I have the c file.

Can someone help me out (or maybe point me in the direction of a pre-existing guide for this type of driver installation?  I have gcc installed too.  Where do I need to put the driver file to compile? Does it matter?  Any help is appreciated thanks

---

### Post by agillator on 2014-12-21
To determine your kernel version, use the command 'uname -r'. Then run the compile command they say. What directory the source file is in should't matter. It may be necessary to compile as root, i.e. 'sudo gcc. . . .'. I would guess the compilation will put it in the correct directory as a .ko file. It should go into /lib/modules/{kernel version number}/{module name}. The rest of the steps seem fairly self explanatory. The ip address you use appears to be up to you. I don't know enough about your setup to really say. But this, at least, should get you started.

---

### Post by Yellow Pasque on 2014-12-21
You shouldn't need to download/build your own module (this isn't Windows). The rtl8150 module has been in the kernel for a long time and it's only had a handful of changes in the past couple of years. To verify you already have the module available:
```
sudo modinfo rtl8150
```

Plug the adapter in and look at dmesg to see if you're getting an interface:
```
dmesg | tail -n 30
```

Some other commands that may be helpful:
```
sudo modprobe -v rtl8150   #manually load driver/module
sudo ifconfig -a      #check network interfaces
sudo lsusb -v       get information about the USB devices
```

---

