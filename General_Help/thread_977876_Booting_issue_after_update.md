---
title: "Booting issue after update"
date: 2008-11-10
forum: General Help
---

### Post by malfist on 2008-11-10
I have a problem...I can't boot after updating.

This is what happens:

I turn on the computer, and grub loads default option
Computer mounts hdds and complains about trying to write to sectors that don't exist
Then the screen goes blank and my monitor starts flashing it's power LED meaning it's receiving no signal and is now sleeping.

If I select the recovery option in grub I can boot. It boots normally, asks for my crypt password for my encrypted partition and then boots. The default option goes past where I would enter my password for some reason.

Any help is appreciated!

---

### Post by -Zeus- on 2008-11-10
try booting to recovery, and running 'fsck'

---

### Post by malfist on 2008-11-10
Why would it boot at all if there is a problem with the filesystem?

---

### Post by malfist on 2008-11-11
That did not fix anything.

---

### Post by michaelbraganza63 on 2008-11-11
To Recover our Data or softewain in our Computer...............

---

### Post by 4-Ever-Euphemistic on 2008-11-11
What System are you runing?

---

### Post by malfist on 2008-11-11
I'm running 8.10, it was working fine in 8.04 As far as system specs:

750GB HDD (encrypted with truecrypt)
250GB HDD (encrypted with DKMS or whatever came on the alt install CD)
200GB HDD (windows, unencrypted)

AMD 9850 Black Edition, quad core 2.5GHz, 64-bit
Nvidea 8600 GeForce
5.1 C-Media sound card
4 GB RAM

---

### Post by malfist on 2008-11-12
I can boot if I use the kernel before the update. I may just reinstall if no one has any suggestions. fsck found nothing.

---

### Post by TeXtonyx on 2008-11-12
In the 8.10 release notes it said something about the Nvidia drivers
not having full support yet. I'm not sure exactly how the recovery
grub option works. But typically, a safe video driver is loaded,
like vesa. That's my theory, your Nvidia driver isn't fitting in
with the new kernel. Back in the days of RedHat 6, the installation
used the wrong driver for my video card and the screen came up black.
I had to do a text install, iirc, and specify the vesa driver. After
the booting was normal, I later added the correct video driver. Well,
something about your situation triggered that memory, I'm not sure,
perhaps the analogy is stretched too thin. This readme may be helpful.

[http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-04.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-04.html)

"You should also set the default run level on your system such that it 
will boot to a VGA console, and not directly to X. Doing so will make it 
easier to recover if there is a problem during the installation process."

 [http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-04-section-03.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-04-section-03.html)

Installing the Kernel Interface

"The NVIDIA kernel module has a kernel interface layer that must be 
compiled specifically for each kernel. NVIDIA distributes the source code
to this kernel interface layer, as well as precompiled versions for many 
of the kernels provided by popular Linux distributions. 

When the installer is run, it will determine if it has a precompiled 
kernel interface for the kernel you are running. If it does not have one,
it will check if there is one on the NVIDIA FTP site (assuming you have 
an Internet connection), and download it. If one cannot be downloaded, 
either because the FTP site cannot be reached or because one is not 
provided, the installer will check your system for the required kernel 
sources and compile the interface for you. You must have the source code 
for your kernel installed for compilation to work. On most systems, this 
means that you will need to locate and install the correct kernel-source,
kernel-headers, or kernel-devel package; on some distributions, ...
You must have a linker installed prior to installing the NVIDIA driver." 

TeX: I don't think that Nvidia has released the restricted drivers for
the new 8.10 release (and kernel?), yet. So there you have my suspicion
about why you can't boot the new 8.10 kernel. Maybe it is just as off
target as the idea that the problem is the filesystem. build-essential

[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)
Maybe this post will prove to be useful if you develop this problem. :-)

---

### Post by malfist on 2008-11-16
Issue is not the graphics driver. The issue is either the kernel or usplash, or both.

I am able to book in older kernels. I am also able to boot without usplash. Previously when I changed the usplash theme before this has happened. I checked the startup manager and it told me I was using the xubuntu usplash. On next reboot when I use the ubuntu usplash theme I will see if it works, and if it does, I'll file a bug report.

---

