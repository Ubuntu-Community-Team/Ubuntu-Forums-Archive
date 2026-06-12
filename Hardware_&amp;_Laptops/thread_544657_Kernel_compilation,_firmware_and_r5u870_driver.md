---
title: "Kernel compilation, firmware and r5u870 driver"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by Keyper7 on 2007-09-06
Hi all,

I have two questions, but I think they are somehow related.

I've recently compiled a vanilla 2.6.22 kernel for my Ubuntu Feisty in a HP Pavillion dv6258se.

Compilation with make-kpkg went fine, but when I installed the generated .deb for the image I've got:
find: /lib/firmware/2.6.22.6-custom: No such file or directory
find: /lib/firmware/2.6.22.6-custom: No such file or directory
find: /lib/firmware/2.6.22.6-custom: No such file or directory
find: /lib/firmware/2.6.22.6-custom: No such file or directory
find: /lib/firmware/2.6.22.6-custom: No such file or directory
find: /lib/firmware/2.6.22.6-custom: No such file or directory
(those were just warnings, though: I can boot the new kernel normally)

The folder /lib/firmware/2.6.22.6-custom wasn't created during the kernel compilation process and
it's probably necessary (since there are folders /lib/firmware/2.6.20-16 and /lib/firmware/2.6.20-15
for my previous kernels). So here comes the first question:

1) Did I skip a step during the compilation process or I really should create a new folder and
copy the firmware to it, all manually? If it's really a manual process, can I just copy them, since
the kernel versions are different?

My second question involve's Sam Revich's r5u870 driver, necessary for the webcam. I can install
it on the other two kernels, but not for the new one. The boot process says that the microcode
file r5u870_1810.fw wasn't found. However, I checked lib/firmware and the file is there. I also
tried to create the /lib/firmware/2.6.22.6-custom folder manually, copy the files in lib/firmware
and /lib/firmware/2.6.20-16 to it and execute an update, but the boot still says that the file
cannot be found. To sum it up,

2) What should I do to use r5u870 with a compiled-by-myself kernel?

Thanks in advance to all you guys, you helped me a lot so far
-Keyper7

---

### Post by Keyper7 on 2007-09-06
By the way, I've just confirmed that the problem happens with the Ubuntu-patched 2.6.20 kernel, as well,
so it doesn't seem like the problem is it being a vanilla kernel.

---

### Post by Keyper7 on 2007-09-07
*bump* No one?

---

### Post by WakkaDojo on 2007-09-10
I had the same problem. Here's what I did:

```
cd /lib/firmware; ls
```
yielding 2.6.20-15-generic  2.6.20-16-generic
When I compiled the kernel it didn't make a directory with my firmware. So, I made a symbolic link:
```
ln -s 2.6.20-16-generic /lib/firmware/2.6.22.6-custom
```
(I modified the commands so you can just use the command there)

Then go back to whichever directory has your kernel.deb packages, and just reinstall them. You will get some warning about how it could be bad for your system because you might have some inconsistencies in there, but obviously you won't because you're reinstalling the same package. So after making the directory link and reinstalling the kernel, reboot the computer and you should be all set!

---

### Post by Keyper7 on 2007-09-14
Thanks.

---

