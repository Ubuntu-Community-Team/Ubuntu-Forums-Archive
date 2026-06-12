---
title: "Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M"
date: 2013-04-20
forum: Hardware
---

### Post by iredden on 2013-04-20
I solved my own problem!  Rather than half of the linux community and not post actually how they did it, I'm going to do just that (mainly because I have a terrible memory and will probably re-install some point in the future)

My laptop is a Lenovo Y580 with nVidia Geforce 660M, 16GB of RAM (I upgraded myself from 6), an i7 3630QM and has the lower end display supporting resolutions of 1366x768.

I used a fresh install of Ubuntu 12.10.  

This solved the problem of:
```
NVRM: failed to copy vbios to system memory
```
and
```
Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.
```

after reading several articles on the internet, I stumbled across several forums stating there was a bbswitch acpi hack for lenovo and figured since I had a lenovo, I'd try it out.

This is what I typed (from my bash history):
```

lspci | grep -i "VGA"
apt-add-repository ppa:ubuntu-x-swat/x-updates
apt-get purge nvidia-current nvidia-settings
add-apt-repository ppa:bumblebee/stable
apt-get update
apt-get install bumblebee bumblebee-nvidia git
git clone git://github.com/Bumblebee-Project/bbswitch.git -b hack-lenovo
cd bbswitch/
mkdir /usr/src/acpi-handle-hack-0.0.1
cp Makefile acpi-handle-hack.c /usr/src/acpi-handle-hack-0.0.1/
cp dkms/acpi-handle-hack.conf /usr/src/acpi-handle-hack-0.0.1/dkms.conf
dkms add acpi-handle-hack/0.0.1
dkms build acpi-handle-hack/0.0.1
dkms install acpi-handle-hack/0.0.1
echo acpi-handle-hack | sudo tee -a /etc/modules
update-initramfs -u
apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386
reboot

```
After reboot, I ran:
```
optirun glxspheres
```

which returned:
```

OpenGL Renderer: GeForce GTX 660M/PCIe/SSE2

```

Good luck!

---

### Post by Rayout123 on 2013-05-22
Thank you SO much for this post! With your help I could finally make use of Bumblebee on Ubuntu 13.04. There'll be probably some more people who wil stumble upon this thread, so I just my solution here.
I had to change things a bit since it didn't work right from the start. It might not be the perfect solution, but it's still better than nothing.

It seems like there is some sort of package missing that prevents the acpi-hack from being built on Ubuntu 13.04 with Kernel 3.8. After some research, I installed the missing package and tried again. It however was still not possible to build the hack.
This was also discussed on Launchpad somewhere (can't remember the link though...) and someone's solution was to upgrade the kernel, since the building process was somewhat broken in 3.8.

So I did the following:

1 ) Upgrade kernel to version 3.8.5 or 3.9 (I tried it both and both worked)
2 ) Then I executed the following code
```

lspci | grep -i "VGA"
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get purge nvidia-current nvidia-settings
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
sudo reboot

```

Yup, that's right! No acpi-hack needed! When I ran "optirun glxspheres" after reboot it worked just fine.
I didn't even need to install virtualgl-libs:i386, libgl1-mesa-glx:i386 or libc6:i386 as it was already installed when I tried it.

I hope the new kernel version will come as an official update soon!

---

### Post by ible on 2013-06-28
Thanks guys for the post!  This helped me in my own installation of Ubuntu (13.04) on the Lenovo Y580.

[http://ubuntuforums.org/showthread.php?t=1543006&page=141&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&page=141&p=12710212#post12710212)

---

### Post by kuzirashi on 2014-03-20
Works also in **elementaryOS Luna x86_64 Linux 3.2.0-60-generic**&#8203;. Solved all problems from my previous eOS installation. Thanks!

---

