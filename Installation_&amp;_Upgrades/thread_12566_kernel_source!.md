---
title: "kernel source!"
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by recmar on 2005-01-25
Hiyah!
I'm trying to install modem drivers but first I need to configure some options. Could somebody tell me where in ubuntu I can find kernel source tree (I mean a full path to kernel source tree).
Thanks

---

### Post by martijntje on 2005-01-25
[QUOTE=recmar]Hiyah!
I'm trying to install modem drivers but first I need to configure some options. Could somebody tell me where in ubuntu I can find kernel source tree (I mean a full path to kernel source tree).
Thanks[/QUOTE]
 Surely. You can find your kernelsource (if installed) in /usr/src/*yourkernelname*

---

### Post by recmar on 2005-01-25
I thought that sources are installed automatically. If not how to do this?

---

### Post by machiner on 2005-01-25
install linux-source-2.6.8.1-16.10

I'm not sure which repository...try:

# deb [ftp://ftp.debian.com/debian/](ftp://ftp.debian.com/debian/) testing contrib main non-free  
# deb-src [ftp://ftp.debian.com/debian/](ftp://ftp.debian.com/debian/) testing contrib main non-free

uncomment.  THis is a DEBIAN REPOSITORY -- I hav eno problems. It's just a source.

---

### Post by az on 2005-01-25
linux-source-2.6 is in main.

Just use the linux-headers for your kernel.  It is much easier.

---

### Post by machiner on 2005-01-25
That didn't work for me and nvidia.

---

### Post by az on 2005-01-26
It should work for modem drivers.  I would not reccommend using debian sources, since we are not talking about a pristine kernel.  I think some work has been done to the Ubuntu kernel on top of the debian stuff...

---

### Post by recmar on 2005-01-26
All right guys.
First of all &#8211; talking about linux &#8211; I&#8217;m rookie. Second, I need kernel sources to install my modem drivers (agere AC'97) - that means I'm not connected to the net through ubuntu at the moment. Third &#8211; installation manual says that I NEED sources if I want to install drivers with 2.6.8.1 kernel. A simple and short explanation how to do this, please! I'm using WinXp to connect the net.

---

### Post by az on 2005-01-26
The kernel-headers are on the cd.  You do not need to go onto the net.  The reason for the existance of this package is for making driver modules.

Agere could be a Lucent modem, or an intel chipset.  Either way, many ac97 modems work with the sl-modem packages found in multiverse.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)

If you are trying to use the ltmodem driver, you will have problems with the make-deb script, for various reasons.  You should be able to make the module files, though.

I do not know what driver you are using.  Let me know and I will give you more detailed information.

Basically, untar it and read the documentation.  Substitute the kernel-headers directory when prompted for the kernel source.

/usr/src/kernel-headers-2.6.8.1-3-386


Good Luck!

---

### Post by recmar on 2005-01-26
Thanks a lot for all information. I was trying to install ls-modem drivers using tar.gz package. With deb it should be much easier.

---

### Post by recmar on 2005-01-26
I downloaded ls-modem deb package and tried to install it with dpkg -i command. I've received information that sl-modem-source depends of module-assistant and installation was cancelled.  Unfortunately I can't find module-assistant using synaptics. 
Directory /usr/src/kernel-headers-2.6.8.1-3-386 doesn't exist as well. All I have in /usr/src is rpm directory. Have no idea what to do. I'm really newbie to linux, not only ubuntu.

---

### Post by az on 2005-01-26
[http://ubuntuforums.org/showthread.php?t=5648](http://ubuntuforums.org/showthread.php?t=5648)


[http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](http://www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)

---

### Post by recmar on 2005-01-28
O.K. I've installed sl-modem-source, sl-modem-daemon and sl-modem-modules.  But there's no /etc/default/sl-modem-daemon directory. Modem is not working. Do I need to configure anything more?

---

### Post by az on 2005-01-28
"no /etc/default/sl-modem-daemon "

Don't panic.  The install script creates one.  It is just a message.

sudo dpkg-reconfigure sl-modem-daemon

tell it to use the slamr modules.  If that does not work, you may need another driver.  Google for scanModem and run that.  It will tell you what driver you need.


Here is the Lucent driver, that may also be the driver you need.
[http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a10_i386.deb](http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a10_i386.deb)

I do not know if it works, since I can compile it, but I do not have the hardware.  Let me know.  Remove the package if it fails to detect your modem.

---

