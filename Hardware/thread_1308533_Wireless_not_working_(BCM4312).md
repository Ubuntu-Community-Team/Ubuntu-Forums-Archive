---
title: "Wireless not working (BCM4312)"
date: 2009-10-31
forum: Hardware
---

### Post by kut77less on 2009-10-31
I just installed Kramic Koala, but the wireless does not work. It did work in Ubuntu 9.04. I think it is because of the Kernel that it doesn't work. I tired to install, and reinstall, the package bcmwl-kernel-source but no luck. I tired to go to the Hardware Drivers, but it said "not in use." I tried to click "activate" but nothing happened. Is there any suggestions how to resolve this issue. I would really love a method that does not require internet access via a wired connections. I think that the only way to fix the problem is downgrading the kernel.

Thanks for all your help.

---

### Post by Ayuthia on 2009-10-31
> **kut77less said:**
> I just installed Kramic Koala, but the wireless does not work. It did work in Ubuntu 9.04. I think it is because of the Kernel that it doesn't work. I tired to install, and reinstall, the package bcmwl-kernel-source but no luck. I tired to go to the Hardware Drivers, but it said "not in use." I tried to click "activate" but nothing happened. Is there any suggestions how to resolve this issue. I would really love a method that does not require internet access via a wired connections. I think that the only way to fix the problem is downgrading the kernel.

Thanks for all your help.

You might try the following from the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If it produces any error messages, please post the error messages.

---

### Post by kut77less on 2009-10-31
> **Ayuthia said:**
> You might try the following from the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```
If it produces any error messages, please post the error messages.

everything expect "wl" works. It says "Fatal error module not present"

any suggestions? 

Thanks

---

### Post by Ayuthia on 2009-10-31
Can you check and see if the following two files exist:
```
ls /lib/modules/$(uname -r)/updates/dkms
ls /var/lib/dkms/bcmwl/5.10.91.9+bdcom/2.6.31-14-generic/$(uname -m)/module
```

---

### Post by craig.o on 2009-10-31
> **kut77less said:**
> I just installed Kramic Koala, but the wireless does not work...

Go to [this site]("http://wireless.kernel.org/en/users/Drivers/b43") & follow the instructions closely.

By the way, I had just come across this while installing 9.10 on this laptop less than 30 minutes ago(!)  For future reference, I found out about this from the system's dmesg.  There's a note in there about needing firmware for Broadcom and to visit the above site (non-free issue).  A thousand thank-yous to whoever was responsible for that pointer.

Back to you, kut77less:  Why are you using Wubi?  Just curious... I've heard of it but not sure what the advantage is over a dual-boot e.g.

hth,
-Craig

---

### Post by kut77less on 2009-10-31
> **craig.o said:**
> Go to [this site]("http://wireless.kernel.org/en/users/Drivers/b43") & follow the instructions closely.

By the way, I had just come across this while installing 9.10 on this laptop less than 30 minutes ago(!)  For future reference, I found out about this from the system's dmesg.  There's a note in there about needing firmware for Broadcom and to visit the above site (non-free issue).  A thousand thank-yous to whoever was responsible for that pointer.

Back to you, kut77less:  Why are you using Wubi?  Just curious... I've heard of it but not sure what the advantage is over a dual-boot e.g.

hth,
-Craig
I have tried your suggestion before, but it didn't work. I will do what Ayuthia said, but it would be later because I can't access my laptop right now. I use Wubi instead of dual-boot because my brother is a mean person:(

---

### Post by kut77less on 2009-10-31
> **Ayuthia said:**
> Can you check and see if the following two files exist:
```
ls /lib/modules/$(uname -r)/updates/dkms
ls /var/lib/dkms/bcmwl/5.10.91.9+bdcom/2.6.31-14-generic/$(uname -m)/module
```
Thanks
I did this and found out that these files do not exist

> ls: cannot access /var/lib/dkms/bcmwl/5.10.91.9+bdcom/2.6.31-14-generic/x86_64/module: No such file or directory 

ls: cannot access /lib/modules/2.6.31-14-generic/updates/dkms: No such file or directory

How would I get these files?

---

### Post by Ayuthia on 2009-10-31
It should have come with bcmwl-kernel-source.

You might try:
```
sudo dpkg-reconfigure bcmwl-kernel-source and then check to see if the files are there or not.
```
It will attempt to configure the package again.

---

### Post by kut77less on 2009-11-01
> **Ayuthia said:**
> It should have come with bcmwl-kernel-source.

You might try:
```
sudo dpkg-reconfigure bcmwl-kernel-source and then check to see if the files are there or not.
```
It will attempt to configure the package again.



When I do that I get an error message. 


> Error! Could not locate wl.ko for module bcmwl in the DKMS tree.

You must run a dkms build for kernel 2.6.31-14-generic (x86_64) first.


Any suggestions? Is there a manual way of adding the files?

thanks

---

### Post by Ayuthia on 2009-11-01
Check and see if you have the following directory:
```
ls /var/lib/dkms/bcmwl
```
If you do and it returns something like
```
5.10.91.9+bdcom
```

Try the following:
```
sudo dkms build -m bcmwl -v 5.10.91.9+bdcom
```

If that is successful try:
```
sudo dkms install -m bcmwl -v 5.10.91.9+bdcom
```

The first dkms command will build the Broadcom kernel module and create the wl.ko.  The second command will install it.

Hope that helps.

---

### Post by kut77less on 2009-11-01
> **Ayuthia said:**
> Check and see if you have the following directory:
```
ls /var/lib/dkms/bcmwl
```
If you do and it returns something like
```
5.10.91.9+bdcom
```

Try the following:
```
sudo dkms build -m bcmwl -v 5.10.91.9+bdcom
```

If that is successful try:
```
sudo dkms install -m bcmwl -v 5.10.91.9+bdcom
```

The first dkms command will build the Broadcom kernel module and create the wl.ko.  The second command will install it.

Hope that helps.


Well it worked!!!!

But I did it a different way. I downloaded 

dpkg-dev (and some dependencies for it) 

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

And then I ran 

> 
sudo dpkg-reconfigure bcmwl-kernel-source

And Then 

> sudo modprobe -r b43 ssb wl
sudo modprobe wl

It finally worked. 

Thanks for all your help.

---

### Post by milan.skocic on 2009-11-07
> **kut77less said:**
> Well it worked!!!!

But I did it a different way. I downloaded 

dpkg-dev (and some dependencies for it) 

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

And then I ran 



And Then 



It finally worked. 

Thanks for all your help.

I did in the same way and wireless works fine.

Just reinstalling bcmwl42xx-kernel-source wasn't sufficient in my case. I had errors during the DKMS building operation.

:)

---

### Post by rob81 on 2009-11-10
> 
dpkg-dev (and some dependencies for it) 

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

And then I ran 

     Quote:
                                                 sudo dpkg-reconfigure bcmwl-kernel-source                                 
And Then 

     Quote:
                                                 sudo modprobe -r b43 ssb wl
sudo modprobe wl                                 
It finally worked. 
I am running a new Dell Studio 15 and this worked perfectly for me. 

However, I need to run the following each time I start my laptop:

sudo dpkg-reconfigure bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl

I'm a bit of a new to all this wireless stuff. Any idea why I have to do this each time I restart?

---

### Post by Ayuthia on 2009-11-10
> **rob81 said:**
> I am running a new Dell Studio 15 and this worked perfectly for me. 

However, I need to run the following each time I start my laptop:

sudo dpkg-reconfigure bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl

I'm a bit of a new to all this wireless stuff. Any idea why I have to do this each time I restart?

You might try the following:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
sudo update-initramfs -u
```
This will prevent the b43 and ssb modules from loading and it will load the wl module.  The update-initramfs will update the system boot information so that it will not try to load the b43 and ssb during the boot process.

Hope that helps.

---

### Post by rob81 on 2009-11-11
> 

You might try the following:

     Code:

 echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo wl | sudo tee -a /etc/modules
sudo update-initramfs -u 


This will prevent the b43 and ssb modules from loading and it will load the wl module. The update-initramfs will update the system boot information so that it will not try to load the b43 and ssb during the boot process.

Hope that helps.     

Thank you Ayuthia. This worked for me! 

Wireless was the only issue I had in setting up Ubuntu 9.10 on my Dell Studio 15. It is now running like a dream. :D

---

### Post by piccirippo on 2009-11-15
Hi all,
thk for solutions. 
I applied your indication:
sudo dpkg-reconfigure bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl
and the wlan started well....but i am not able to update the system boot information:

ubuntu@ubuntu:~$ sudo update-initramfs -u 
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
cp: cannot stat `/vmlinuz': No such file or directory

I thinks that's becouse i am using ubuntu booting from  a usb pen whith persistent option, so vlinuz is 
in /cdrom/casper directory .
I am new in linux so please what's the right command for me?
thx a lot

---

### Post by h1kz0r on 2009-11-26
Unfortunately I tried all the different methods online including this one and still the wireless doesn't work on my hp mini.
The wl is loaded fine, the STA Driver says active and in use and the wireless led is on.
iwlist gives me an error... failed to read scan data, invalid argument when i do scan or scanning.
I see this issue resolved in many places, but this is complete bs imo and all those ppl have it working on 9.04 not 9.10 and the rest of us just downgraded.
this issue is still unresolved, just like all the other "solved" threads about this.

---

### Post by leorolla on 2010-04-27
With Lucid it works a treat.

With Wubi, Live USB, or a true install, doesn't matter. And it's easy.

Instructions at
[https://wiki.ubuntu.com/Testing/Laptop/Reports/AcerAspireOneD150#Wireless%20%28Lucid%20Lynx%29](https://wiki.ubuntu.com/Testing/Laptop/Reports/AcerAspireOneD150#Wireless%20%28Lucid%20Lynx%29)

On some machines it gives a DMA error.

If it fails with another error rather than DMA, it is probably due to the dirt of previous hacking, in this case try with the Live USB to be sure.

---

