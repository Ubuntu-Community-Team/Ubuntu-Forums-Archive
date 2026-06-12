---
title: "Ubuntu Gutsy perfection on T60"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by neixian on 2008-01-15
Recently, I installed ubuntu gutsy on my laptop Thinkpad T60, which has following hardware:
Model: 2613-CTO
Videocard: ATI x1300 64M
Soundcard: Inter HDA
LAN: Intel e1000
Wireless: Intel ipw3945
Bluetooth
IRDA

And it works fine. 

Undoubtedly, Ubuntu Gutsy is an amazing OS. I started to use it just after I had installed it. Everything works fine, the soundcard, videocard, wireless, bluetooth, LAN. The only thing  I need to do is  just to run restricted manager, and, Bingo, perfect! Surfing the Ubuntu forum, searching the Internet by googling, play Supertux and Neverball, etc.

However, I think there is some perfection needed to be done.

Fisrt of all, it is about suspend and hibernate. Many guys here complained about the bug concerns the open-sourced  fglrx driver, and suffered a lot while push the sleep button and with the laptop's halfmoon light flashing system halt.  

The second, I need to make my battery protection working, I am a little worried about that the laptop battery works fully charged. It is said that this situation may cause shorter and shorter battery lifespan. So I need to build tp-smapi module to make things right.

The last thing, I also need to utilize IBM HDAPS feature to protect my harddisk, in case it drops or something. And, of cause, taking advantage of the feature to play games like Neverball sounds interesting--imaging that you hold your T60 as if you were holding a flatpad with a ball on it, trying to make the ball roll all the way to the exit. Of course, this kind of games can be a little risky, so I do not recommended them strongly.

So, I start here as below.

---

### Post by neixian on 2008-01-15
According to thinkwiki, there are two diffefent ways to solve the suspend and hibernate problem. The first is to install the newest fglrx driver downloadable from ATI support page. The second, however, is to compile a  custom kernel. But unfortunately, compiling a kernel in the Ubuntu way is a little discouraging.  So I decided to compile it but in the legacy Debian way. Definitely, the legacy method is more simple and effective. What is more, I believe building a custom kernel can be useful in a number of ways. First, why should I install so many modules and enable various hardware support on my laptop which will never need them? And, why not just boot a small and clean kernel which comfortably meets my own requirements? 
So, let's do it.
Get the source:
sudo apt-get source linux-source-2.6.22
and get the build-essential , kernel package debhelper and libncurses5-dev:
sudo apt-get install build-essential kernel-package libncurses5-dev debhelper

the make menuconfig
There is a huge number of options here, and it is very frustrating if you want make sure of every one. But, just remember your hardware and the modules you need and try times and times again,(I do not know how to post attachment here, or else I will post my .config.) Let the options alone, if you want to make suspend and hibernation happen, you really need to do is to choose SLAB allocator under general setup option, and that is all!
The do the following:

#make-kpkg --initrd --append_to_version=-t60 kernel-image kernel-headers

then install the debian files created in the parent directory.

---

### Post by neixian on 2008-01-16
Now that I have a custom modified kernel to support suspend/hibernate.  It works pretty fine but then what else? For with this kernel I am not only unable to use WIFI internet connection but paly 3D games.

As there is no Intel wireless driver and fglrx driver in stock dedicated to this new kernel, I need to compile them myself. 

But on Ubuntu, ATI fglrx driver and Intel ipw3945 are in restricted modules and ubuntu modules which are totally kernel related. So, the only thing I can do  is to download source file and compile them.

First to solve the videocard problem, which I have gone so far for to get suspend/hibernate done with fglrx driver. 

 ATI fglrx drivers can be download on this page: [http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html](http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html)
Choose anyone you like. I select version 8.40 for it is said to be more stable.

Then do as following:
chmod u+x  ati-driver-installer-8.40.4-x86.x86_64.run 
sudo ./ati-driver-installer-8.40.4-x86.x86_64.run  --buildpkg Ubuntu/gutsy

These steps will generate some debian package,  such as:
xorg-driver-fglrx_8.40.4-1_i386.deb
fglrx-kernel-source_8.40.4-1_i386.deb

The two listed here are most important, for I need them to install a driver and a kernel module.
Do as following:

dpkg -i xorg-driver-fglrx_8.40.4-1_i386.deb
module-asssitant 
Choose fglrx-kernel  to build the module and install it. A debian package will be generated, named fglrx-kernel-2.6.22.9-tp*.deb  (2.6.22.9-tp is my kernel custom version number)

Install this package. The 3D driver are ready to roll.

Here is some output infomation:
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6747 (8.40.4)

Test with suspend/hibernate, it works great! So goes the videocard driver. Then I have to compile ipe3945 driver too.

---

