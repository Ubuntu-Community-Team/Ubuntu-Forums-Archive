---
title: "Ubuntu 8.10 Nvidia driver issues"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Baggyeyes on 2009-01-26
I'm relatively new to ubuntu having made the change from windows a few months ago to ubuntu 8.04.

I recently upgraded to 8.10 and there are some serious issues with the video card drivers.

First off they would not download, I managed to remedy this using some help on the forums but now whenever I start up the system it gives me a number of error messages before the ubuntu GUI opens giving me a number of warning messages and usually forcing me to either restart or use low graphical settings.

I am using a HP Pavilion dv6000

Obviously I understand that my description of the situation is limited but I was wondering if anyone has had any experience that is similar and can give me some pointers on how best to go forwards

Thanks in advance

---

### Post by Partyboi2 on 2009-01-27
Have you treid booting into recovery and choosing xfix?
If that does not work then maybe  your log file will give some info. Open a terminal (Applications>Accessories>Terminal) and type
```
cat /var/log/Xorg.0.log |grep EE
``` and post the results.

---

### Post by Baggyeyes on 2009-01-27
Ok, I tried the xfix in recovery mode and it told me that it was overwriting a customized file and that the file had been backed up :s

I put in the terminal command and this is the result:


	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


I have a compatible and recommended NVIDIA driver installed and I am running in low graphics mode with it activated. Also whenever I try to open the NVIDIA X server settings in administration it gives me the following error message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

However, the screenshot of my hardware drivers screen (in glorious low-res) is attached and it is clear I am using a NVIDIA driver.

I might be getting this all totally wrong, my usual approach to problems in ubuntu is to search for people with the same problem and read the solutions but there doesn't seem to be a definitive one for this problem.

Sorry again for my lack of experience :(

If I can't work this out soon I'm reinstalling hardy...

EDIT: Here is the message I get when I run xfix:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090127163227

obviously this was my fault, wondering how to remedy it :s

---

### Post by Partyboi2 on 2009-01-27
Have you tried reinstalling the driver again? Try using envyng to install the driver. You can install it from the terminal.
```
sudo apt-get install envyng-gtk
``` Then launch it from Applications>System Tools

---

### Post by Baggyeyes on 2009-01-28
Yea I have tried that a few times now, I tried it again just in case but no luck.

I have tried almost every suggestion on the forums now but nothing seems to be happening. I think I will reinstall hardy as soon as possible, this is really starting to get on my nerves...

Thanks very much for the help anyway :)

---

### Post by utter-imadness on 2009-01-28
Hello. I had a similar problem with my nvidia driver on the same laptop when I upgraded from 8.04 to 8.10. It seemed that sometimes when the OS was upgraded the kernels were not upgraded to the new versions and nvidia needs these new kernels to compile on startup. 
Can you please post the output of 
```
gksudo gedit /boot/grub/menu.lst
```
between "## ## End Default Options ##" and "### END DEBIAN AUTOMAGIC KERNELS LIST".

---

### Post by Baggyeyes on 2009-01-28
I guess that would make sense of the problem, here is the result of the command:

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-9-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.24-23-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro  single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.10, kernel 2.6.24-22-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro  single
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.10, kernel 2.6.24-19-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=592152dc-1252-4338-b494-69a16509dec9 ro  single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.10, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


Hope this is useful :)
Baggyeyes

---

### Post by Baggyeyes on 2009-02-02
can anyone do anything with this info?

sorry to keep asking I'd just rather not reinstall hardy from scratch

---

### Post by Bart_D on 2009-02-03
> **Partyboi2 said:**
> Have you tried reinstalling the driver again? Try using envyng to install the driver. You can install it from the terminal.
```
sudo apt-get install envyng-gtk
``` Then launch it from Applications>System Tools

Does Envy work with Ubuntu 8.10?  On the official Nvidia website, it only shows support for Ubuntu 8.04:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Baggyeyes on 2009-02-09
Ok I got this to work (finally) thanks so much for all the help :D

Mainly due to the tip off about the kernel problems I was able to change some settings and it is now working :)

---

