---
title: "Ubuntu 13.04 Nvidia Geforce 9300 GS driver installation"
date: 2013-09-10
forum: Hardware
---

### Post by 88dEFGA on 2013-09-10
Hi all,
I'm new here, hope I'm not breaking any rules. I'd like to get help with nvidia driver installation for my lenovo N500 laptop. I've been using ubuntu 12.04 for a year or so. I had problems installing nvidia driver with 12.04 as well, but I finally got it working and ubuntu was running smooth. But few days ago, I wanted to change unity to gnome3. When I wanted to install gnome3, terminal suggested I upgrade my ubuntu first. So I upgraded to 12.10 and than to 13.04. When loaded ubuntu, I got login screen as usual. After I typed in my password, blank screen appeared with cursor and I could not do anything. Run terminal, etc. I could switch to tty1-tty6 though.
I googled for a little bit and found, that I should upgrade kernel and it will work in some cases. I had 3.8.something as latest. After I installed newest kernel, it was 3.9.something. But it was worse. Right after grub laptop rebooted. Currently I am running on 3.2.0-52-generic. 
I thought the problem was nvidia driver, so I installed nvidia-304, then tried 310, 325, 313 and 173. Not changed a thing. 
I tried to install following few tutorials as well. 
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
[http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/)
I believe, that when I looked into logs, I found following error:
```

[LIST]
[*]sudo nvidia-modprobe 
[*]libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='nvidia_current' 
[*]ERROR: could not insert 'nvidia_current': Function not implemented 
[/LIST]

```
and than link:
[https://devtalk.nvidia.com/default/topic/545594/nvidia-modprobe-from-developer-zone-debian-repository-fails/](https://devtalk.nvidia.com/default/topic/545594/nvidia-modprobe-from-developer-zone-debian-repository-fails/)
I did their solution:
> 1) dkms remove -m nvidia-current -v 319.21 --all
2) edit /usr/src/nvidia-current-319.21/dkms.conf and remove the "PATCH" and "PATCH_MATCH" lines
3) dkms install -m nvidia-current -v 319.21
with an replacement of nvidia-current to nvidia-304 and different version. However it did not help either.
I was frustrated after few days and removed nvidia drivers completely. I'm using nouveau drivers, but now my laptop is super slow and overheated. I can not even watch movies or work fluently. I hoped some of you might help me, what logs should I look into and how to fix it. When I install nvidia driver, I have only tty1-6 accessible. With newer kernel versions not even that.
There might be some inconsistency in my post because I'm writing it by heart. Sorry for that.

---

### Post by 88dEFGA on 2013-09-13
I tried to install driver again. I followed [this instructions]("http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal").
and did "dpkg --configure -a". Did not help.
Latest error message in Xorg.0.log is:
```
[    37.799] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
I've googled that uninstalling [nvidia-glx and linux-restricted-modules]("http://ubuntuforums.org/showthread.php?t=808247") packages might help, but I did not have them installed.
I tried [this(last post)]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/810647"):
```

[LIST]
[*]mv /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so.backup 
[*]ln /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/nvidia-304-updates/xorg/libglx.so 
[/LIST]

```
Did not help eithher, some more error appeared in Xorg.0.log.
I gave a shot to this again:
```

[LIST]
[*]1) dkms remove -m nvidia-304-updates -v 304.88 --all 
[*]2) edit /usr/src/nvidia-current-314.88/dkms.conf and remove the "PATCH" and "PATCH_MATCH" lines 
[*]3) dkms install -m nvidia-304-updates -v 304.88 
[/LIST]

```
Error message appeared:
```

[LIST]
[*]Error: Your kernel headers for kernel 3.2.0-52-generic cannot be found. Please install the linux-headers-3.2.0-52-generic package, or use the --kernelsourcedir option to tell dkms where it's located 
[/LIST]

```
I guess I should not have use "apt-get install linux-headers-3.2.0-52-generic", but I did:
```

[LIST]
[*]E: Unable to locate package linux-headers-3.2.0.52-generic 
[*]E: could not find any package by regex 'linux-headers-3.2.0-52-generic' 
[/LIST]

```

---

### Post by 88dEFGA on 2013-09-13
Unable to locate package linux-headers-3.2.0.52-generic happened because it was old kernel not longer available in ubuntu 13.04 ppa-source. So I installed 3.8.0-30-generic. It's crashing as well, but recovery mode is working with nvidia driver. It's still slow, hope it will change when I fix normal mode.
//edit: It took one more restart and it's working. So it was not really nvidia problem, but kernel did not update/upgrade successfully. Hope it will last.

// I also did this symlink.
> 
[LIST]
[*]mv /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so.backup
[*]ln /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/nvidia-304-updates/xorg/libglx.so
[/LIST]


---

