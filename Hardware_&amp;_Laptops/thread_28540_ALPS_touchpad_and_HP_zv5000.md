---
title: "ALPS touchpad and HP zv5000"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by Saptarshi Guha on 2005-04-20
Hello,
 I followed the instructions located here 
*[http://www.ubuntuforums.org/showthread.php?t=28132&highlight=alps](http://www.ubuntuforums.org/showthread.php?t=28132&highlight=alps)*

Though the last command didn't work for me
sudo dpkg -i kernel*alps*deb

returned
[I]dpkg: error processing kernel*alps*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kernel*alps*deb
[/I]

However when i start X, this shows up in my Xorg.0.log

[I](II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3[/I]

And later on,
[I](II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(**) Option "Device" "/dev/input/mice"
...
...
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"[/I]

I tried using /dev/psaux but that didnt work.

Could anybody help
Thanks 
Saptarshi Guha

---

### Post by dejitarob on 2005-04-20
Why the new thread? Anyways, be sure you did the 'sudo make-kpkg --us --uc --initrd --append_to_version "-5-386-alps" kernel_image kernel_headers kernel_source' part (where -386 is be sure to put your kernel variant in, e.g. if you are using k7 it would be "-5-k7-alps") and are in the /usr/src/linux-source-2.6.10 director. I accidently skipped it the first time and got the same error message.

---

### Post by Saptarshi Guha on 2005-04-20
Hi,
I had done  exactly that. Still the error message...

Thanks
Saptarshi

---

### Post by mendicant on 2005-04-20
Are you in the correct directory?  Do the .deb files exist in the directory in which you give the commands?  The message is a bit odd, since when I try that in a directory which doesn't have those files, bash complains, not dpkg.

---

### Post by SteveGodfrey on 2005-04-21
I had the same problem so I just issued the commands separately

dpkg -i kernel-headers-2.6.10-5-386-alps_10.00.Custom_i386.deb
dpkg -i kernel-image-2.6.10-5-386-alps_10.00.Custom_i386.deb
dpkg -i kernel-source-2.6.10-5-386-alps_10.00.Custom_all.deb

Which, as far as I know, will do the same thing......

---

