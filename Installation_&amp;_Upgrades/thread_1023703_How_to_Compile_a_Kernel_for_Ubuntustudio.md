---
title: "How to Compile a Kernel for Ubuntustudio?"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by uwe2006 on 2008-12-28
Hi all,

I am relatively new to Linux and I tried to get my Soundcard Edirol UA-25 EX running on Ubuntu Studio in Advanced mode. I found out that I have to recompile the Kernel and change the usbquirks.h. Then I recompiled the Kernel. I downloaded the source <linux-source-2.6.24> and performesd the steps I found in several How To's. 
1.) I copied the current config-file <sudo cp /boot/config-2.6.24-22-rt>.config
2.) I activated the USB Sound modules in <sudo make xconfig>
3.) Then I compiled with 
<sudo make-kpkg clean> and 
<sudo make-kpkg --initrd --revision i386 binary>
4.) Then I installed with <sudo dpkg -i ../linux-image-2.6.24.3_i386_i386.deb>
5.) Than I had some problems with the X-Window which i fixed by < sudo dpkg-reconfigure -phigh xserver-xorg>, after I rebooted with the old Kernel. 
After that I rebooted with the new Kernel, but I can not activate the WLAN and I can not start midi. An error message is shown (module_snd_seq_midi not found) If I try to start this with modprobe. 
The new build Kernel is also named <kernel 2.6.24.3> while my old working kernel is called <kernel 2.6.24-22-rt>. Do I have to use different source package. If I try to install the linux-rt package I get the message that the lates verison is already installed. 
Did used the wrong approach, or should I repeat the steps and have a brief look into the configuration settings?

Regards Uwe

---

### Post by Bucky Ball on 2008-12-28
Not sure if you compiled the correct kernel. You need the rt (real time) kernel designed for low latency, which it appears your old one is and the new one isn't.

---

### Post by albinootje on 2008-12-28
Which howtos are you referring to exactly ?
Please provide links.

---

### Post by Bucky Ball on 2008-12-28
> **albinootje said:**
> which howtos are you referring to exactly ?
Please provide links.

+1

I see now though. Your custom kernel has the same name as the one already installed or will have if you compile the correct one. That is where the confusion is coming in perhaps.

---

### Post by albinootje on 2008-12-28
And an alternative can be this, this is an example with 8.10 :

apt-cache search linux-image|grep rt
linux-image-2.6.27-3-rt - Linux kernel image for version 2.6.27 on Ingo Molnar's full real time preemption patch (2.6.26.5-rt9)
```

sudo apt-get build-dep linux-image-2.6.27-3-rt
sudo apt-get source linux-image-2.6.27-3-rt
cd linux-rt-2.6.27/
--> change the usbquirks.h
--> active the driver options needed in the kernel config, don't change
      anything else
sudo dpkg-buildpackage -rfakeroot -uc -b

```

Replace the kernel version in this example with the 2.6.24.x that you need.
After this all goes well, afaik you should find a deb. package if you navigate ../ out of that source directory.

References :
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)
[http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html)

---

### Post by uwe2006 on 2008-12-29
> **albinootje said:**
> Which howtos are you referring to exactly ?
Please provide links.

Hi,

I used this one: [http://wiki.ubuntuusers.de/Kernel?highlight=kernel#source-5](http://wiki.ubuntuusers.de/Kernel?highlight=kernel#source-5)

Regards Uwe

---

### Post by uwe2006 on 2008-12-29
> **albinootje said:**
> And an alternative can be this, this is an example with 8.10 :

apt-cache search linux-image|grep rt
linux-image-2.6.27-3-rt - Linux kernel image for version 2.6.27 on Ingo Molnar's full real time preemption patch (2.6.26.5-rt9)
```

sudo apt-get build-dep linux-image-2.6.27-3-rt
sudo apt-get source linux-image-2.6.27-3-rt
cd linux-rt-2.6.27/
--> change the usbquirks.h
--> active the driver options needed in the kernel config, don't change
      anything else
sudo dpkg-buildpackage -rfakeroot -uc -b

```

Replace the kernel version in this example with the 2.6.24.x that you need.
After this all goes well, afaik you should find a deb. package if you navigate ../ out of that source directory.

References :
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)
[http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html)

Unfortunately this leads also to some errores during the compiling process. But I will try some other ways.

---

