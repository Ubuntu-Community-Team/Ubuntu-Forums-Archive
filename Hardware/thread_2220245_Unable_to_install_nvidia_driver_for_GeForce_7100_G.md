---
title: "Unable to install nvidia driver for GeForce 7100 GS"
date: 2014-04-27
forum: Hardware
---

### Post by stefan30 on 2014-04-27
Hello all,

I am posting because I lost all hope in googling for any answer that will work for me. I have really tried a lot and nothing seems to be working, maybe someone here will have an idea what to do.

So here is what is going on - I had installed ubuntu 12.04 LTS with graphics card as in subject and everything worked just fine. I installed proprietary nvidia 173 driver using "Additional drivers" and graphics mode worked just fine. I just updated to 14.04 LTS and what do you know, as always X server failed. I never had a major update without this problem, however this time nothing seems to work, no matter what driver I install it will not work. When I totally purge nvidia drivers I get unity and everything seems to be working, however I expect that nvidia drivers are better in terms of compatibility and performance vs. non-proprietary ones.

What I as doing - when I noticed that X server is not working I tried reinstalling the driver. I purged everything nvidia-related (sudo apt-get -y remove --purge nvidia-*) and removed xorg.conf. This brings back unity but does not do what is the goal... After doing this I go to "Additonal drivers" and install nvidia driver. No matter which I select (173 or 304, based on nvidia's site, both should support this card) after installing the most I get is graphical login screen and when I enter my credentials I get empty desktop with cursor and no icons or functionality whatsoever. That is the best I was able to achieve. The worst case scenario is I get "no signal" from the monitor and (obviously) black screen and only emergency console. I have absolutely no idea why this happens. Based on below logs it seems that nvidia module does not want to load, but I do not know how to make it load. What I did not try yet is to reinstall compiz/unity, but I do not want to do this, because it may break it totally (also I think it is a driver problem and not unity). If this has a chance to help, please let me know what commands to use and I will try it. Is there no more support for 7100 GS in the most recent ubuntu? Any help is appreciated.

A few logs below, if more is needed, please let me know what commands to run and I will post it on the thread.
```
root@xaffax-router:~# nvidia-smi
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_304'
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
NVIDIA: failed to load the NVIDIA kernel module.
NVIDIA-SMI has failed because it couldn't communicate with NVIDIA driver. Make sure that latest NVIDIA driver is installed and running.
```

```
root@xaffax-router:~# startx

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux xaffax-router 3.2.0-61-generic #92-Ubuntu SMP Mon Mar 31 23:47:59 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-61-generic root=UUID=efa770b7-b7d4-4e83-a025-0504b5a8c537 ro vga=792 quiet splash
Build Date: 16 April 2014  01:36:29PM
xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Apr 27 14:37:32 2014
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_304'
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_304'
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
```

```
root@xaffax-router:~# modprobe nvidia
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_304'
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
```

```
root@xaffax-router:~# dpkg -l | grep -i nvidia
ii  libcuda1-304                                          304.117-0ubuntu1                                    amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.117-0ubuntu1                                    amd64        NVIDIA legacy binary driver - version 304.117
ii  nvidia-libopencl1-304                                 304.117-0ubuntu1                                    amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                                 304.117-0ubuntu1                                    amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
```

```
root@xaffax-router:~# lspci -nnk | grep -iA2 vga
05:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV44 [GeForce 7100 GS] [10de:016a] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0273]
        Kernel modules: nouveau, nvidiafb
```


Thanks a lot!
XaFFaX

---

### Post by stefan30 on 2014-04-28
So, I guess nobody has any idea on this one?

Also another thing I noticed that seems to be wrong and also google knows nothing about how to fix it, is:
```

root@xaffax-router:~# update-grub
GRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.
```

I am wondering why the text does not hint on how to fix this "unpacked, but not yet configured", all google answers do not work. I'm starting to like this linux more and more... :evil:

---

### Post by m-dw on 2014-04-28
If it helps, I installed the NVidia drivers using
```
sudo apt-get install nvidia-current
```

dpkg then builds and installs the module for your current kernel, and updates initrd and grub.  This is the first version of Ubuntu for which I did a fresh install since 12.04, so might explain why my experience was more-or-less trouble-free.

---

### Post by stefan30 on 2014-04-28
> **m-dw said:**
> If it helps, I installed the NVidia drivers using
```
sudo apt-get install nvidia-current
```

dpkg then builds and installs the module for your current kernel, and updates initrd and grub.  This is the first version of Ubuntu for which I did a fresh install since 12.04, so might explain why my experience was more-or-less trouble-free.

Thanks, I know about that, it does not help however, I tried to install the drivers using numerous ways, the one you described above was one of them, did not work though.

I have found another possible problem and maybe this will hint someone to help me resolve the problem.
Finally I decided to manually install driver downloaded from nvidia's site. I followed instructions from here: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual). Obviously it could not be problem-proof, so the problem I have is this:

```
root@xaffax-router:~# apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-3.2.0-61-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-3.2.0-61-generic' has no installation candidate
```

In other words for some reason I cannot install those headers. When I go to /lib/modules/3.2.0-61-generic/ there is no "build" folder which means that those headers are not available. While for 3.13.0-24-generic the headers are there. WTF is going on? after runninng "uname -r" I get 3.2.0-61-generic, so why can't I download them??!!! Moreover when I check apt-get there is no possibility to select 3.2.0-61-generic package, others are there, this one NOPE, SORRY!! Isn't in this system anything that works without a problem? I expect that this is the reason for not being able to build the module. Any idea on how to download this? Nvidia installer hints that I can manually specify location of those files, I will try to download this, extract and point manually, maybe then it will work. I still have to say this is beyond stupid and pathetic...

EDIT:
Oh and btw. by default apt-get update, and linux-headers-generic download only for 3.13, so wonderful...

---

### Post by m-dw on 2014-04-28
Well the reason you can only download 3.13 is because that's the starting point for 14.04.  Kernel 3.2 isn't supported on 14.04.  The nvidia drivers won't install because they can't find the headers for the obsolete kernel.  I suspect that 3.2 is left over from 12.04.  You need to remove it.

So have you installed kernel 3.13?  At this point I usually resort to synaptic to see what's installed... I'm on a fresh install here, but I think you should have:
[LIST]
[*]grub version 2.02
[*]kernel and headers 3.13.0.24.29
[*]initramfs-tools 0.103ubuntu4
[/LIST]

You may have got the legacy version installed as your boot loader.  I'm guessing you install grub2 with
```
sudo grub-install [boot_device]
```

Reboot and press the shift key after the POST and you should get the grub menu.  If not reboot and keep pressing esc.  Boot into kernel 3.13.  Make sure you have the headers for 3.13 installed, and remove linux-image, 3.2 (synaptic again is your friend).  This will probably run mkinitramfs and grub-install again

Then install "nvidia-current" using whatever method you prefer.  This will build the module, then run mkinitramfs and grub-install again

Reboot again and you should have a working system with working nvidia drivers.

I hope this works out for you.  I've had a few issues with 14.04, but it does actually seem better for me than previous versions (I couldn't run Unity in 3D on 12.04, it's much quicker on 14.04).

---

### Post by stefan30 on 2014-04-29
> **m-dw said:**
> Well the reason you can only download 3.13 is because that's the starting point for 14.04.  Kernel 3.2 isn't supported on 14.04.  The nvidia drivers won't install because they can't find the headers for the obsolete kernel.  I suspect that 3.2 is left over from 12.04.  You need to remove it.

So have you installed kernel 3.13?  At this point I usually resort to synaptic to see what's installed... I'm on a fresh install here, but I think you should have:
[LIST]
[*]grub version 2.02 
[*]kernel and headers 3.13.0.24.29 
[*]initramfs-tools 0.103ubuntu4 
[/LIST]

You may have got the legacy version installed as your boot loader.  I'm guessing you install grub2 with
```
sudo grub-install [boot_device]
```

Reboot and press the shift key after the POST and you should get the grub menu.  If not reboot and keep pressing esc.  Boot into kernel 3.13.  Make sure you have the headers for 3.13 installed, and remove linux-image, 3.2 (synaptic again is your friend).  This will probably run mkinitramfs and grub-install again

Then install "nvidia-current" using whatever method you prefer.  This will build the module, then run mkinitramfs and grub-install again

Reboot again and you should have a working system with working nvidia drivers.

I hope this works out for you.  I've had a few issues with 14.04, but it does actually seem better for me than previous versions (I couldn't run Unity in 3D on 12.04, it's much quicker on 14.04).

Thanks for the answer, I was able to gather more or less what you have posted, yesterday. I have updated kernel and headers manually using .deb files (found a guide and downloads for that on some other site). Not without problems, installers were trying to do something with nvidia driver 304.88, which I have failed to install previously doing it manually. And there was of course this:
```
root@xaffax-router:~# update-grub
GRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.
```

This message was also "presented" when installing new kernel image. Ubuntu "thought" that he had 3.2 still but it was because of update-grub fail. So what I did is I totally uninstalled grub and reinstalled, this fixed it (I think), now "uname -r" finally gives correct kernel (3.14 I believe it is I installed). However along the way I (again) purged all nvidia crap, did kernel update, fixed grub, system boots (to my astonishment), so finally happy that maybe I will be able to install this damn driver, I installed nvidia-current. And what do you know - the same issue :/. This is getting boring, just to be clear, some logs:
```

Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.14.1-031401-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Tue Apr 29 00:41:34 2014
xaffax@xaffax-router:~$ sudo -i
[sudo] password for xaffax:
root@xaffax-router:~# uname -r
3.14.1-031401-generic
root@xaffax-router:~# nvidia-smi
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_304'
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
NVIDIA: failed to load the NVIDIA kernel module.
NVIDIA-SMI has failed because it couldn't communicate with NVIDIA driver. Make sure that latest NVIDIA driver is installed and running.

root@xaffax-router:~# modprobe nvidia
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_304'
modprobe: ERROR: could not insert 'nvidia_304': Function not implemented
```

And btw. versions of tools (grub, headers and initramfs) are there and (I think) are correct. grub is 2.02 beta2-9 (whatever that means), headers are for 3.14, so is the kernel as noted above. Initramfs is what you posted.

I will try yet again to install nvidia driver manually and see what this does. Other than that, does anyone have any other ideas on what may be wrong? Thanks!

---

### Post by stefan30 on 2014-04-29
Ok, when I try to install nvidia driver manually I get below:

```
  ERROR: Failed to run `/usr/sbin/dkms build -m nvidia -v 304.88 -k 3.14.1-031401-generic`:
         Kernel preparation unnecessary for this kernel.  Skipping...

         Building module:
         cleaning build area....
         make KERNELRELEASE=3.14.1-031401-generic module SYSSRC=/lib/modules/3.14.1-031401-generic/build.........(bad exit status: 2)
         ERROR (dkms apport): binary package for nvidia: 304.88 not found
         Error! Bad return status for module build on kernel: 3.14.1-031401-generic (x86_64)
         Consult /var/lib/dkms/nvidia/304.88/build/make.log for more information.

```

Does anyone have any idea on what is going on here and how to install this damn driver?

---

### Post by m-dw on 2014-04-29
Sorry, have reached the end of my ideas/experience.  Might be an idea to do a fresh install.  My card uses the same driver (it's a GeForce 7600 GS) and it went in straight away with no significant issues after a fresh install.  I've always managed to get it working after an upgrade but never without problems.  I did a fresh install for 14.04 because I wanted to reconfigure my hard disks so I guess I'm just lucky this time.

Of course I also accepted the stock kernel 3.13.0-24 that came with the distribution, installed the NVidia drivers using synaptic, and chose not to do anything out of the ordinary until I had a stable system.

---

### Post by stefan30 on 2014-04-29
> **m-dw said:**
> Sorry, have reached the end of my ideas/experience.  Might be an idea to do a fresh install.  My card uses the same driver (it's a GeForce 7600 GS) and it went in straight away with no significant issues after a fresh install.  I've always managed to get it working after an upgrade but never without problems.  I did a fresh install for 14.04 because I wanted to reconfigure my hard disks so I guess I'm just lucky this time.

Of course I also accepted the stock kernel 3.13.0-24 that came with the distribution, installed the NVidia drivers using synaptic, and chose not to do anything out of the ordinary until I had a stable system.

Thanks for the answer! I figure right now, that the problem is that I upgraded to "too new" kernel. As you mentioned 14.04 comes with 3.13 and I installed 3.14. When I manually install nvidia drivers downloaded from their site I get compilation errors, what (for me) means, that those have probably not yet been optimized/configured for this new kernel (especially since those are older ones). I also found some sites (some in Russian, but what is google translate for ;) ) where people had similar problems and downgrading helped, so maybe getting down to 3.13 will fix it (provided I did not mess up anything else). Now I installed 3.13.11 if I remember correctly, but cannot test it, since I am on a remote console, and I still boot automatically into 3.14. When I will be "on-site" I will try to load-up 3.13 and then try yet again, maybe this time it will work... If not I will maybe go down to 3.11 and then try.

All in all, even if finally this will work my question is why distribution upgrades have problems with updating to new kernel? Or in general - so many problems? And not only Xserver but also grub... This makes this system unusable to "normal" (unexperienced) users. I am no master in terms of linux understanding, but I know my way around more or less and still problems are highly complicated and not easy to fix. There are always problems with updating to newer versions, and not only for me I suppose. Anyway if this will not work I will probably have to fresh install it... Oh well, it happens I guess...

Thanks for the help again! At least someone posted something...

---

### Post by stefan30 on 2014-04-29
Ok, so my final update on this thread: I did as described above, I have started ubuntu under kernel 3.13.0 in which I installed nvidia-current drivers without a problem as it seems. All is working fine, no errors (I am quite astonished to be honest). After that I removed all installed kernels (3.13.11 and 3.14) and I think now all should work fine. So for all those having similar problems - check if your system has updated kernels, and install updated one if not, then install the driver, should help.

Too bad it took me somewhere around 4 days to figure this out.

---

### Post by m-dw on 2014-04-29
> **stefan30 said:**
> Too bad it took me somewhere around 4 days to figure this out.

Congrats and well done.  No need for a new install this time round then, but it probably wouldn't hurt to do one when you get time.

---

### Post by stefan30 on 2014-04-30
> **m-dw said:**
> Congrats and well done.  No need for a new install this time round then, but it probably wouldn't hurt to do one when you get time.

Yes, you're probably right. The machine I had problems with is actually my home router, so graphical interface is not all that important (in terms if how smooth it works), I do 99% of things remotly using console, so as long it works correctly and does not disconnect every hour or so, or startup for an hour ;) I think it should be fine. I just like to have graphical interface, in case I am installing some new feature "on-site" and need google's guidance on things. Not to mention that if something does not work it may be that there are other things messed up (as in this case - grub and kernel...).

The positive is that I learned something new and this is a good thing, as well as maybe this thread will help someone in the future. Hopefully though it will work more problem-free on the next update.

Thanks again for all feedback m-dw! It is appreciated.

---

