---
title: "Nvidia module doesn't work on 2.6.10-5--k7"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by znh on 2005-08-23
Hello ubuntu users.
I have a very very weird situation here..
I installed 2.6.10-5-k7, after that I booted with that kernel (yes I am sure).
Everything went fine, I used the 'nv' driver without 3D acceleration.
Now I'd like to play enemy-territory, I followed the ubuntuguide.org to get the drivers.
'apt-get install nvidia-glx nvidia-settings'
Everything went fine, I typed sudo nvidia-glx-config enable.
the driver changed from nv, to nvidia.
*Yaay* was I thinking, but no.. when I tried to start the X server it gave me the anonying message "failed to load module nvidia".
modprobe nvidia didn't work as well..

the drivers work perfectly on -386, but that is no sollution - my GB of ram isn't detected fully (only 900megs).

Help would be so fine!

P.S. I have a Amd Athlon XP 2400 processor, that's why I'd like to use -k7

---

### Post by h4rdc0d3 on 2005-08-23
A similar issue applies on Debian... when you install a more specific kernel (i.e. k7 vice i386) you have to install a matching nvidia-glx package. I also have an amd processor and would like to do what you're trying to do, but have found that there's no k7 nvidia-glx for ubuntu, therefore I stick with i386 kernel because nvidia drivers are more important to me than having a more specific kernel.

So, the questions for you are:


[list=1]
[*]Why do you want to use a k7 kernel?
[*]What advantages does it offer and are you going to use them?
[*]Which is more important to you: k7 kernel advantages or video driver?
[/list]EDIT: By the way, just because you *can*, doesn't necessarily mean you *should*.

---

### Post by theToolman on 2005-08-28
I am interested to hear if the k7 optimised kernel produces real performance improvements; I too have an nvidia card and athlon (2400 too) and want to use the binary drivers.  


Anyone know what the benefits of the optimsed kernels are like?

---

### Post by angkor on 2005-08-28
[QUOTE=h4rdc0d3]A similar issue applies on Debian... when you install a more specific kernel (i.e. k7 vice i386) you have to install a matching nvidia-glx package. I also have an amd processor and would like to do what you're trying to do, but have found that there's no k7 nvidia-glx for ubuntu, therefore I stick with i386 kernel because nvidia drivers are more important to me than having a more specific kernel.

So, the questions for you are:


[list=1]
[*]Why do you want to use a k7 kernel?
[*]What advantages does it offer and are you going to use them?
[*]Which is more important to you: k7 kernel advantages or video driver?
[/list]EDIT: By the way, just because you *can*, doesn't necessarily mean you *should*.[/QUOTE]


You don't need a k7 specific nvidia-glx for the k7-kernel.

Why I use a k7 kernel?

* It's optimised for my proc
* The GUI feels snappier using the optimised kernel, not by leaps and bounds over      the standard kernel but still.
* It recognizes my full 1GB of RAM in stead of 900mb something with the 386 kernel.
* I don't have to choose between my video drivers and the advantages...I get em both :)

---

### Post by tseliot on 2005-08-28
You can try my guide to install whatever nvidia driver version you want:
I recommend you to use the nvidia driver you are trying to install which is version 7174 (which is sure to work for you) try ths:

1) get to nvidia website and go to the drivers section:

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)
You will see a list of drivers: download 7174

2) Use my easy HOWTO to install the driver you've downloaded (just follow the steps)

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

If you have any questions, please ask them at the thread of my guide.

---

### Post by markthecarp on 2005-08-28
[QUOTE=znh]Hello ubuntu users.
I have a very very weird situation here..
I installed 2.6.10-5-k7, after that I booted with that kernel (yes I am sure).
Everything went fine, I used the 'nv' driver without 3D acceleration.
Now I'd like to play enemy-territory, I followed the ubuntuguide.org to get the drivers.
'apt-get install nvidia-glx nvidia-settings'
Everything went fine, I typed sudo nvidia-glx-config enable.
the driver changed from nv, to nvidia.
*Yaay* was I thinking, but no.. when I tried to start the X server it gave me the anonying message "failed to load module nvidia".
modprobe nvidia didn't work as well..

the drivers work perfectly on -386, but that is no sollution - my GB of ram isn't detected fully (only 900megs).

Help would be so fine!

P.S. I have a Amd Athlon XP 2400 processor, that's why I'd like to use -k7[/QUOTE]

zhn, this is working on my Atlon 2000. I mostly followed the steps described by tseliot in the thread he mentions. Hear are the steps I took with some, maybe all differences noted. 

1- System running i386 kernel and nv.
2- Installed k7 kernel and matching headers using apt-get as root.
3- Rebooted to same.
4- Installed nvidia-glx and nvidia-settings binaries from Ubuntu sources using apt-get as root.
5- Working as root I ran nvidia-glx-config enable.
6- Restarted X session with Ctl-Alt-Bksp.

I did not attempt to get nvidia working while using the i386 kernel. I prefer to su to root over typing all those sudo's. That's just my Debian roots showing. tseliot's thread is quite thorough.

-mark
```
mark@smokey:~$ uname -a
Linux smokey 2.6.10-5-k7 #1 Thu Aug 18 23:14:40 UTC 2005 i686 GNU/Linux
mark@smokey:~$ locate nvidia | grep 7174
/usr/lib/tls/libnvidia-tls.so.1.0.7174
/usr/lib/libnvidia-tls.so.1.0.7174
/usr/lib/nvidia/libnvidia-tls.so.1.0.7174
```

---

### Post by pnix on 2005-08-30
[QUOTE=h4rdc0d3]A similar issue applies on Debian... when you install a more specific kernel (i.e. k7 vice i386) you have to install a matching nvidia-glx package. I also have an amd processor and would like to do what you're trying to do, but have found that there's no k7 nvidia-glx for ubuntu, therefore I stick with i386 kernel because nvidia drivers are more important to me than having a more specific kernel.

So, the questions for you are:


[list=1]
[*]Why do you want to use a k7 kernel?
[*]What advantages does it offer and are you going to use them?
[*]Which is more important to you: k7 kernel advantages or video driver?
[/list]EDIT: By the way, just because you *can*, doesn't necessarily mean you *should*.[/QUOTE]
 try to install linux-restricted-modules-2.6.10-5-k7.

---

