---
title: "Geforce 6600GT and 6699 drivers.."
date: 2004-12-09
forum: Hardware &amp; Laptops
---

### Post by DyDx on 2004-12-09
I just installed Ubuntu on my desktop for the first time since I got my nVidia Geforce 6600GT AGP.  I figured everything would work-out great but I forgot that Ubuntu doesn't come with drivers that support the 6600GT out-of-box!

Initially, the only way for me to get X to work at all was to use vesa mode.  Then I tried the nVidia drivers on Warty Universe but of course they didn't work.  So I tried the binary from nVidia, but that claims I do not have the source for my particular kernel installed -- I went ahead and installed the 2.6.8.1 kernel source in synaptic and it still gives me this error and refuses to install.  

So I found this thread here: [http://www.ubuntuforums.org/showthread.php?t=6148&highlight=nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=6148&highlight=nvidia+drivers)

I installed the glx, linux-restricted and nvidia-kernel-source debians at daniels site, then made sure my XF86Config-4 file was correct (added glx, removed dri and GLCore, changed vesa to nvidia).  Now I can get into X and it shows me the nVidia load screen, but opengl games always seg fault before doing ANYTHING.  

What have people done to get 6600's and newer cards working??

---

### Post by TravisNewman on 2004-12-09
You'll have to download your kernels source and install the official nvidia drivers. The new drivers haven't been implemented in warty

---

### Post by DyDx on 2004-12-09
[QUOTE=panickedthumb]You'll have to download your kernels source and install the official nvidia drivers. The new drivers haven't been implemented in warty[/QUOTE]

But, as I said, I have installed the kernel source and it won't let me install the nvidia drivers from nvidia's site.  WW 4.10's default kernel is 2.6.8.1 correct?  I installed the kernel source from Synaptic and nvidia's installer still gives me the finger....

---

### Post by Rancoras on 2004-12-09
Here's a thread I started a short time ago.  Please, try searching before you post, it just helps keep clutter down.  This is the result of a search for "6600gt".

[http://ubuntuforums.org/showthread.php?t=6148&highlight=6600gt](http://ubuntuforums.org/showthread.php?t=6148&highlight=6600gt)

---

### Post by DyDx on 2004-12-09
[QUOTE=Rancoras]Here's a thread I started a short time ago.  Please, try searching before you post, it just helps keep clutter down.  This is the result of a search for "6600gt".

[http://ubuntuforums.org/showthread.php?t=6148&highlight=6600gt](http://ubuntuforums.org/showthread.php?t=6148&highlight=6600gt)[/QUOTE]

If you had taken the time to read my post you'd see that I have already found that link and tried what is described in it (I even link to that thread in my original post).  And yet I still cannot get OpenGL to work...

---

### Post by Rancoras on 2004-12-09
My apologies, I stand corrected.  Someone walked in and interrupted me while I was reading your post and I completely missed that part of it.  I haven't tried any opengl games yet.  Which game is giving you problems and I'll see if I have it and see if it does the same to me.

---

### Post by DyDx on 2004-12-09
[QUOTE=Rancoras]My apologies, I stand corrected.  Someone walked in and interrupted me while I was reading your post and I completely missed that part of it.  I haven't tried any opengl games yet.  Which game is giving you problems and I'll see if I have it and see if it does the same to me.[/QUOTE]

Well I immediately get seg faults on the command line with Chromium and Tux Racer (no other output).  OpenGL screensavers just don't work in the screensaver application ("No Preview Available" it says)

---

### Post by TravisNewman on 2004-12-09
try typing glxgears into a terminal and see what average fps you get

---

### Post by DyDx on 2004-12-09
[QUOTE=panickedthumb]try typing glxgears into a terminal and see what average fps you get[/QUOTE]

Segmentation fault.

How about this: If someone could give me the exact procedure to install the drivers from a fresh install I will just reinstall and try them to see what happens.  This not working may be a result of me trying a few things which didn't work at ALL before trying something that half worked.

---

### Post by Rancoras on 2004-12-09
As soon as I get home, I'll try glxgears and see if it segfaults.  Mine is a fairly clean install with the drivers from the thread you found.  I'll post back in about an hour to hour and a half.

---

### Post by Rancoras on 2004-12-09
Sorry, I got tied up with family stuff.  Yup, I have the same problem.  Seg fault with glxgears.  Daniel are you watching?  Any ideas?

---

### Post by jegler on 2004-12-13
The same thing occurred for me when i upgraded to the 2.6.9 kernel and newer nvidia drivers.  However, I do not own a 6600GT.  This occurs on a geforcefx 5600 and  segfaults for any opengl application.  I don't know if this helps but when i try to run ```
sudo nvidia-glx-configenable
``` I get the following output:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
sudo md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


```

And when I try to run ```
sudo md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum
``` I get an error saying ```
bash: /var/lib/xfree86/xorg.conf.md5sum: Permission denied
```

---

### Post by Rancoras on 2004-12-13
Are you running x.org?  If so, are you running Hoary?  I'm running niether.

---

### Post by daniels on 2004-12-14
Yeah, I'm working on a new version of the nvidia drivers (linux-restricted-modules-2.6.9 2.6.9-8; nvidia-glx 1.0.6629-0ubuntu7.  Should be up shortly, will give you guys a shout for testing when it is.

---

### Post by daniels on 2004-12-14
```
deb [http://people.ubuntu.com/~daniels/](http://people.ubuntu.com/~daniels/) l-r-m/$(ARCH)/
```

Only i386 at the moment, but please test.

---

### Post by Rancoras on 2004-12-15
linux-restricted-modules-2.6.9-1-k7 won't install for me.  I get an error:

Depends: linux-image-2.6.9-1-k7 but it is not installable

I guess that's because I'm not running Hoary with 2.6.9?

---

### Post by daniels on 2004-12-16
Yeah, correct.

---

### Post by Rancoras on 2004-12-16
Well, my linux install isn't mission critical so I guess I might dist-upgrade to Hoary.  I'll post in the other thread in the Hoary forum if I do that.  Thanks for at least getting me back into X Daniel.

---

### Post by daniels on 2004-12-16
No worries -- enjoy it.  I suppose the other thing you could do is to install nvidia-kernel-source and build a module with linux-headers-$(uname -r) installed.

---

### Post by billputer on 2005-01-08
Could you tell me exactly how to do that?

I tried installing the NVIDIA binary for 6629 initally, but it gave me the error:

> ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
I installed the specific kernel headers for my kernel (linux-headers-2.6.8.1-4-k7).  I then tried specifying the path to my kernel headers with "sudo sh NVIDIA-Linux-x86-1.0-6629-pkg1.run --kernel-source-path /usr/src/linux-headers-2.6.8.1-4-k7" but I was given the same error.  Could someone explain what I'm doing wrong, or tell me how to build a module as described?

---

### Post by daniels on 2005-01-08
Oh, you're using a stock kernel now?  In that case, try just installing linux-restricted-modules-2.6.8.1-4-k7.

---

### Post by daniels on 2005-01-08
Try untarring /usr/src/nvidia-kernel-source.tar.gz and running make KSRC=/usr/src/linux-headers-2.6.8.1-4-k7 in the directory it creates.

---

### Post by billputer on 2005-01-08
I'll try that.  Also, it is worth the extra effort to start using X.org and 2.6.9?

Edit: I tried running make KSRC = and got this:

> $ make KRSC=/usr/src/linux-headers-2.6.8.1-4-k7
Makefile:418: .config: No such file or directory
scripts/kconfig/conf -s arch/i386/Kconfig
drivers/net/wireless/Kconfig:303:warning: 'select' used by config symbol 'IPW2200' refer to undefined symbol 'IEEE80211_CRYPT_WEP'
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** [include/linux/autoconf.h] Error 2

That's probably because I'm running a stock kernel.  

In response to just installing the restricted modueles, I was under the impression that the installing the restricted modules wouldn't help because Warty doesn't have 6629, which adds support for Geforce 6600GT's.

---

### Post by billputer on 2005-01-09
Apparently all I needed to configure a kernel was libncurses-dev.  That and running make menuconfig made it so that the make KSRC= command worked.  I'm just about to try installing the NVIDIA drivers again.

EDIT:  I got the Nvidia drivers working, I just had to compile the kernel by hand following parts of this guide:  [http://www.ubuntulinux.org/wiki/KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto)

Then the driver installation worked perfectly.  I went from ~200 fps in glxgears to ~12000 fps. :)

---

### Post by pseudonym on 2005-01-24
Hi. I'm in the same boat as you were. I'm running the 2.6.8.1-4-k7 kernel and getting the same kinds of errors when trying to install the 6629 binary package from nvidia's website. As I understand it, the work involved in getting this to install is to configure your kernel correctly so that the new nvidia module can be built, rather than having to recompile the whole kernel, right?. I've never done this before so can someone verify that I'm doing this correctly?

Here's what I have planned-

1. I've installed the following packages:

nvidia-kernel-source 1.0.6629-0ubuntu7 (from the daniels repository)
linux-headers-2.6.8.1-4-k7
linux-source-2.6.8.1 (still tarred, not sure if this is required)
gcc
libncurses5-dev
build-essential
bin86

I noticed that the version of nvidia-kernel-common I have relates to the 6111 driver. Is this a problem? Or perhaps it's something that gets updated as a result of the new build?

2. Untar /usr/src/nvidia-kernel-source.tar.gz

3. Run make menuconfig

4. Run make KSRC=/usr/src/linux-headers-2.6.8.1-4-k7 in the directory created by untarring nvidia-kernel-source.

5. Run the nvidia 6629 package (pointing it to the new kernel source path if it asks me too) and cross my fingers. :)

Assuming this works, is there anything you need to after the new driver is installed (other than updating XF86Config-4 as needed and maybe /etc/modules), such as run nvidia-glx-config enable?

I know I can update to nvidia 6629 if I do a dist-upgrade, but I'd prefer not to make *too* many changes to my otherwise stable Warty system.

As you can see, I'm no expert. So any help will be greatly appreciated! :)

---

### Post by Tichondrius on 2005-01-26
I managed to install the 6629 driver by following the steps below. You need to install both the 6629 nvidia-kernel package for your kernel version, and the nvidia-glx package (in this order). The former includes the nvidia kernel module, and the latter includes the X windows driver and libraries. The problem is that the 6629 nvidia-kernel package is only available (pre-compiled) for 2.4 kernels, so you need to create it yourself by compiling the sources from nvidia-kernel-source. 

Note, this worked for me using normal Woody with XFree86, and a 6600GT card. Previously, I used the "vesa" driver, because the stock nvidia-glx package from Ubuntu repositores includes the older driver version, which doesn't support the 6600GT. Now I'm getting about 7500 fps on glxgears with this setup, so everything feels much faster then the vesa driver, but I haven't tried to run any heavy duty games on this machine yet (btw, did anyone get the sound driver to work on Asus A8N-SLI motherboard yet?).


1. Download and install the 2.6.8.1 kernel source package using synaptic/apt:

$ sudo apt-get install linux-source-2.6.8.1

2. Download and install the 6629  [nvidia-kernel-common](http://packages.debian.org/unstable/x11/nvidia-kernel-common) and [nvidia-kernel-source](http://packages.debian.org/unstable/x11/nvidia-kernel-source) packages from debian unstable:

$ sudo dpkg -i nvidia-kernel-common_1.0.6629+1_all.deb
$ sudo dpkg -i nvidia-kernel-source_1.0.6629+1-1_i386.deb

3. Make sure you are added to the src group, by typing "groups". If you are not, do the folowing (you may need to login again for this to take effect):

$ sudo addgroup myusername src

4. Unpack the sources (make sure to delete any previous directories which conflict, like /usr/src/modules/nvidia-kernel and /usr/src/linux-source-2.6.8.1)

$ cd /usr/src
$ tar jxvf linux-source-2.6.8.1.tar.bz2
$ tar zxvf nvidia-kernel-source.tar.gz
$ ln -s linux-source-2.6.8.1 linux

5. We need to compile the kernel now, so I'm assuming you have the pre-requisite packages installed, including the kernel-package, fakeroot, build-essential, etc (this is not a kernel compile tutorial, but I'll still go thru the basic steps to compile and install a new kernel).  If you want to use your current kernel's configuration do this:

$ cd /usr/src/linux
$ cp /boot/config-`uname -r` .config
$ make oldconfig

6. Configure the kernel to not include the Nvidia Riva framebuffer driver (FB_RIVA under Device Drivers->Graphics Support->Support for frame buffer devices), because it might conflict with the new nvidia driver. You can also change any other kernel option you like (assuming you know what you're doing):

$ cd /usr/src/linux
$ make gconfig        # you can substitute gconfig with xconfig or menuconfig

7. Compile the kernel and nvidia module:

$ cd /usr/src/linux
$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version custom1 kernel_image modules_image

8. Install the new kernel and nvidia-kernel packages

$ cd /usr/src
$ sudo dpkg -i kernel-image-2.6.8.1custom1*.deb
$ sudo dpkg -i nvidia-kernel-2.6.8.1custom1*.deb

9. Download and install the 6629 [nvidia-glx](http://packages.debian.org/unstable/x11/nvidia-glx) package from debian unstable (the binary driver and libs for X windows):

$ sudo dpkg -i nvidia-glx_1.0.6629+1-1_i386.deb

10. Change /etc/X11/XF86Config-4 to use the nvidia driver.

11. Reboot into your new kernel.

---

### Post by pseudonym on 2005-01-26
Turns out I didn't need to do anything this drastic. I was able to install the nvidia driver package just using kernel-headers and gcc, as per these instructions -

[http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/](http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/) 

, a very similar version of which is also in a couple of threads in this forum.

Strange thing is, it didn't work for me the first time, which is why I posted here. But it's working now, so I'm not complaining :) .

I did get a warning during the install about rivafb, but I carried on regardless. All my graphics apps run fine, though. Is rivafb supposed to appear in lsmod? It doesn't in mine...

One other thing I'm not completely sure about is nvidia-kernel-common. Is this supposed to be created by the nvidia package/during the module building process? Synaptic shows this package as installed, but for driver version 6111, which I had installed previously using apt-get. I don't expect the 6629 version would show up here, though, seeing as everything was done outside of package management. I tried checking in the installed files of nvidia-kernel-common, but they don't contain any clues about the version. Nor does the nvidia readme mention anything about this being created during the installation. Could this pose a problem do you think eg. some kind of version conflict? If so, can I just uninstall the 6111 nvidia-kernel-common and replace it with a 6629 one?

Thanks.

Btw, my vid card isn't a 6600 but a Ti4400.

---

### Post by Tichondrius on 2005-01-26
[QUOTE=pseudonym]Turns out I didn't need to do anything this drastic. I was able to install the nvidia driver package just using kernel-headers and gcc, as per these instructions -

[http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/](http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/) 

, a very similar version of which is also in a couple of threads in this forum.

Strange thing is, it didn't work for me the first time, which is why I posted here. But it's working now, so I'm not complaining :) .

I did get a warning during the install about rivafb, but I carried on regardless. All my graphics apps run fine, though. Is rivafb supposed to appear in lsmod? It doesn't in mine...

One other thing I'm not completely sure about is nvidia-kernel-common. Is this supposed to be created by the nvidia package/during the module building process? Synaptic shows this package as installed, but for driver version 6111, which I had installed previously using apt-get. I don't expect the 6629 version would show up here, though, seeing as everything was done outside of package management. I tried checking in the installed files of nvidia-kernel-common, but they don't contain any clues about the version. Nor does the nvidia readme mention anything about this being created during the installation. Could this pose a problem do you think eg. some kind of version conflict? If so, can I just uninstall the 6111 nvidia-kernel-common and replace it with a 6629 one?

Thanks.

Btw, my vid card isn't a 6600 but a Ti4400.[/QUOTE]


You can get the nvidia-kernel-common-1.0.6629 from debian unstable as I explained in my post. It includes some configuration files for the drivers, so it's best  to have the same version as your nvidia-kernel-w.x.y.z-1.0.6629 package. In fact, the latter  package depends on nvidia-kernel-common-1.0.6629 and above.  So the dependency chain is like this:

(a) nvidia-glx-1.0.6629  --depends on--> (b)nvidia-kernel-2.6.8.1custom1-1.0.6629 -> (c)nvidia-kernel-common-1.0.6629

So the abbreviated instructions are:
You download (c) as well as nvidia-kernel-source-1.0.6629 (d) from debian unstable and install them. Then you use them to build (b) by compiling the source. You install (b). Then you download and install (a). Simple.

You don't really have to build a new kernel, but you do need to create a nvidia-kernel package (b) for your kernel version (e.g. 2.6.8.1custom1). So it's possible to just use kernel headers, but since I usually build my own kernel anyway, I find it convenient to build both the kernel-image and the nvidia-kernel packages together, using kernel-package (which is a very useful tool as it let you manage kernels like debian packages).  

In the end, we still need three things - the config files (c), the kernel module (b), and the X driver and libs (a). The hardest one is the kernel module (b), which needs to match your kernel (or at least use the same headers). The NVIDIA automated installer script does take perform these steps, but it becomes hard to maintain and upgrade since the changes are not tracked by a package management system like apt (for example, in your case the nvidia installer probably overwrote the old config files, so that' why your setup works even though you still have the nvidia-kernel-common-1.0.6111 package installed). So it's best to use the package system, like in my instructions. That's how the previous driver 6111 from the Ubuntu repositores was installed.

Btw, I also upgraded to 6629 on my main rig, with a 6800 Ultra (agp) which was using 6111 driver before, and I'm seeing a 5-10% performance improvement in doom 3/ut2004.  Similar to the benchmarks in this [article](http://www.anandtech.com/linux/showdoc.aspx?i=2302&p=4).

---

### Post by pseudonym on 2005-01-26
Thanks. I understood your instructions in your original post, though :) But since I didn't build my own kernel they're not that relevant to me (at least, though I'm sure they're great instructions! :) ) .

You say that nvidia-kernel-common should be the same version as nvidia 6629 package. So I should be able to get the 6629 version of nvidia-kernel-common from debian unstable and install it over the 6111 version via apt-get upgrade, rather than having to start over and build a custom kernel, no? I just wanted to check first whether doing this is not going to be a problem...

And rivafb? When building your own kernel you can choose not to include it, but if it's not showing up in my lsmod then it shouldn't cause any problems on my stock kernel machine, should it?...

Thanks.

---

### Post by Tichondrius on 2005-01-26
The nvidia installer script you used already installed the new config files (and overwrote the config files from your installed nvidia-kernel-common-1.0.6111). So in fact your installed nvidia-kernel-common-1.0.6111 is already "upgraded", just not thru apt !

So you can download and install nvidia-kernel-common-1.0.6629, just to make apt know that it's upgraded. But really it doesn't matter.

Regarding the riva-fb driver, it should definetely not show in lsmod, so you're fine. On some systems it mis-detects a new nvidia card for an old riva card and tries to drive it.

---

### Post by pseudonym on 2005-01-26
Cool, thanks! :)

---

### Post by sharkzf6 on 2005-01-27
[QUOTE=daniels]No worries -- enjoy it.  I suppose the other thing you could do is to install nvidia-kernel-source and build a module with linux-headers-$(uname -r) installed.[/QUOTE]
Yeah, this is the way Will Smith did it at Maximum PC when he went to Linux for 6 months. My downer was, after installing unbuntu on an old slapped together P3 rig with a SB live! and GeForce 2 where it worked flawlessly, when I attempted to install it on my main rig, P4 3.0, GeForce 6800 and Audigy sound card, I was greeted with "sound card not found" and "unable to load X"...blah, blah, blah...

I know there are ways to make this work, I just don't know if I'm up to the task. I still have the P3 rig up and running with ubuntu and it's really slick for sure. But now that I'm back on my trusty old XP system with all my high end hardware working flawlessly (6 hour sessions of Counter Strike Source are no problem on this mean box), I'm not so sure I'll go back to unbuntu or any other Linux distro. I don't mind the work because I love working on computers...er, my own anyway, but it gets a little frustrating with Linux.  There's just so many ways to do the same task, it's difficult to find any one sure way to do something like installing new drivers, a task that is a no-brainer in Windows.   :-# 

I spent the good part of last week working on getting Debian Woody working on the old P3 rig, then I found ubuntu which installed and worked flawlessly on the second attempt. So I got very optimistic about running it on the P4.  I got somewhat deflated after it didn't work. On the upside, I found this Knoppix live CD iso which I haven't found a computer that it doesn't work on yet including my P4 rig. That tells me there is a way to get Linux to work with all this high end hardware. Why doesn't somebody put together a distro of Linux that loads and runs as easy on any rig like the Knoppix live CD does.  :? Maybe those guys should do it, they might be able to start an OS revolution! I know I'd be one of the first in line to get it. ;)

---

### Post by Tichondrius on 2005-01-27
Hey, you can install Knoppix permanently on the hard drive if you want - you just need to tell knoppix to install itself - it's in one of the menu options ! 
I must agree Knoppix is the best I've seen at hardware detection, especially video cards and wireless cards.

---

### Post by daniels on 2005-01-27
Hoary should wipe the floor with Knoppix when it comes to hardware detection for video, and already does a very, very good job with wireless.

---

### Post by sharkzf6 on 2005-01-27
[QUOTE=Tichondrius]Hey, you can install Knoppix permanently on the hard drive if you want - you just need to tell knoppix to install itself - it's in one of the menu options ! 
I must agree Knoppix is the best I've seen at hardware detection, especially video cards and wireless cards.[/QUOTE]
No Doubt! I just slapped the thing in and booted it up, didn't bother to check the menu options as I was doing something else everytime I used it...duh. I'll give it a go and see what happens. Thanks. :D

---

### Post by sharkzf6 on 2005-01-27
[QUOTE=daniels]Hoary should wipe the floor with Knoppix when it comes to hardware detection for video, and already does a very, very good job with wireless.[/QUOTE]
Daniels, I realize you're probably one of the most knowledgeable persons in this forum when it comes to getting all this stuff to work so I won't dare dispute anything you say, however, everything I've seen on Hoary indicates it's not a good idea to use it yet so I never bothered to look into it. Is your opinion on this different? 
I know the 6800 will work with Warty/Hoary but what about the Audigy? It was my understanding the Audigy problem is a Linux issue - read 24 bit sound. Am I wrong on that? (I dont' remember if my Audigy sound worked with Knoppix - I'll check it out again). And lastly, how do I get the Hoary iso?
Cheers

---

### Post by daniels on 2005-01-27
Hoary live ISOs are available from [http://cdimage.ubuntu.com/daily-live/;](http://cdimage.ubuntu.com/daily-live/;) right now, it's probably not entirely advisable for everyone to use it as a daily system because of the risk of breakage (e.g. Metacity breaking spectacularly the other day).  However, as much testing as we can get is always appreciated, and helps us improve the system, so you might find it useful to throw in a live CD and see what you can get out if it.  Unfortunately I have no idea about the Audigy -- I have a very nice external amplifier/receiver/speaker set that takes optical SPDIF in, and the integrated sound chipset on my motherboard has optical SPDIF out, which is hard to get wrong ...

---

### Post by Tichondrius on 2005-01-29
> **daniels]Hoary live ISOs are available from [url]http://cdimage.ubuntu.com/daily-live/ said:**
>  right now, it's probably not entirely advisable for everyone to use it as a daily system because of the risk of breakage (e.g. Metacity breaking spectacularly the other day).  However, as much testing as we can get is always appreciated, and helps us improve the system, so you might find it useful to throw in a live CD and see what you can get out if it.  Unfortunately I have no idea about the Audigy -- I have a very nice external amplifier/receiver/speaker set that takes optical SPDIF in, and the integrated sound chipset on my motherboard has optical SPDIF out, which is hard to get wrong ...

I'm going to install Hoary amd64 !  I've been running woody i386 for a couple of months, and really like it (it's my main OS), but since hoary is getting ready it's also a good opportunity to try out the 64 bit stuff......  btw, I've got WinXP running inside VMWare on woody, and everything works including networking and sound, and I think it's really cool, although I'm not yet sure what I need it for exactly.... oh yeah, maybe microsoft money (does linux have finance software which can check your online accounts automatically ?) although that might actually work with a windows emulator.

---

### Post by sharkzf6 on 2005-01-29
> **daniels]Hoary live ISOs are available from [url]http://cdimage.ubuntu.com/daily-live/ said:**
>  right now, it's probably not entirely advisable for everyone to use it as a daily system because of the risk of breakage (e.g. Metacity breaking spectacularly the other day).  However, as much testing as we can get is always appreciated, and helps us improve the system, so you might find it useful to throw in a live CD and see what you can get out if it. Yes, I found the iso's and burned the latest one, 01/27/05 I believe, before I read your post. Hoary did find my 6800, of course, all that meant was it loaded the default 'nv' driver, which is no big deal since the nVidia 3D drivers still must be installed in order to get full 3D acceleration. Why can't the 3D drivers be incorporated in the distro? As for stability, it was definitely a little quirky. I had to reboot several times after using Ctrl-Alt-F1/F7 to switch back and forth between command prompt and GUI login sessions, something I never had any problem doing with other Linux distros. Gnome would report that the panel was already loaded so it wouldn't load a panel which left me with no panel at all, I mean none! Gnome was running but it was just the background color. The only way I could get out was to open a terminal by right clicking on the desktop and issuing a 'halt' or 'reboot' command or just hitting Ctrl-Alt-Del. Also, synaptic and apt-get were always reporting errors telling me the Hoary URLs were not responding or refusing access. That got old quick. As soon as I come up with a sure way to install nVidia drivers (I'm practicing on this system), I'm going to reinstall Warty.>  Unfortunately I have no idea about the Audigy -- I have a very nice external amplifier/receiver/speaker set that takes optical SPDIF in, and the integrated sound chipset on my motherboard has optical SPDIF out, which is hard to get wrong ... For my sound problem, I just put my trusty old SB live card back in my P4 system which seems just fine for LInux. I don't like the idea of having to swap the cards out when I boot Windows, however, right now I'm not booting into Windows much, I'm spending most of my time working with Linux in hopes that I can convince myself to use it as my daily OS. Ultimately, I plan on installing a dedicated hard disk in my main P4 box for dual booting Windows/LInux. Linux as my main OS and XP for gaming. Thanks for the info! Cheers :)

---

### Post by sharkzf6 on 2005-01-29
BTW - How do I stop GDM? Every thing I've read on this subject says to issue a '/etc/xinit.d/ gdm stop' command but all that does is bring up a 'gdm is already running' message. Not to mention I've never seen this '/xinit.d/' directory.
 :-k

---

### Post by sharkzf6 on 2005-01-29
Another thing - sorry for all the questions - when I run the nVidia installer, it returns an error in the nvidia-installer.log file that says ' Performing CC test="cc" '. The first time I ran it, it said I didn't have the gcc package installed so I installed it. It also made reference to having 'cc' in the path. Since Linux doesn't use paths like DOS/Windows (I believe), I figured it was referring to some path set in the compiler gcc or CC. I'm sure daniels knows what this means. How bout it daniels, what the heck is this all about?

I suppose the bottom line is, the nVidia installer is trying to compile a kernel that has the 3D drivers embedded. Apparently it uses the gcc compiler. Since I've never used the gcc myself for anything, there's probably not a 'cc' path set. I'm no programmer but I've been building/using/thrashing computer systems for a long time so I'm making an educated guess here, I may be totally off base. How bout some help here? Thanks.

---

### Post by daniels on 2005-01-29
You'll need to install the 'build-essential' package to compile stuff.

---

### Post by daniels on 2005-01-29
Run 'sudo invoke-rc.d gdm stop' to stop gdm; the reason we don't ship nVidia's drivers by default is because we prefer to use open source drivers where a reasonable alternative exists (aside from the Matrox Parhelia chipset, this is true for all display drivers).

---

### Post by sharkzf6 on 2005-01-29
[quote=daniels]**You'll need to install the 'build-essential' package to compile stuff.[/quote]**Thanks, although I must confess I'm getting a little confused about what apt-get/synaptic is really doing. I thought when you “install” a package with one of these it actually installs the program, however, I'm not so sure that's the case now. For example, I used synaptic to “install” 3D Chess but there's no link to that program and when I search for the file, all that turns up is the archive of it still zipped up.
[QUOTE=daniels]**Run 'sudo invoke-rc.d gdm stop' to stop gdm[/quote]**Thanks
[quote=daniels]**the reason we don't ship nVidia's drivers by default is because we prefer to use open source drivers where a reasonable alternative exists (aside from the Matrox Parhelia chipset, this is true for all display drivers).[/QUOTE]** Yeah, I hear ya, I guess I've spent too much of my life using Windows/DOS. It seems to me that if a set of drivers is available, and the distro installer can probe and detect hardware, that it could also install embedded drivers for said hardware if detected. WOW, wouldn't that be cool... 8-) I realize you could use the argument that it would bloat the distro by having to include so many drivers, but let's face it, we're talking ATI and nVidia here, there are no other players in this arena. ;) I'm assuming this is possible since it does the same thing for sound cards or NIC cards for example. ?

---

### Post by sharkzf6 on 2005-01-29
OK, I "installed" the "build-essential" package you indicated using synaptic, but, as I said in my previous post, I don't think synaptic is actually "installing" the programs. Here's the end of the nvidia-installer.log file:

[i]Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com](ftp://download.nvidia.com))? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/home/<edit out>/<edit out>/linux-source-2.6.10'    as specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/home/<edit out>/<edit out>/linux-source-2.6.10'
-> Performing CC test with CC="cc".
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/i]

Same as before I "installed" the build-essential package. I can't play 3D chess either. :( I suppose the part I missed about all this was, once packages are "installed", you actually have to unzip them to have access to the programs. Once you do that, is there a 'setup' program, or does it just work after being unzipped? I've been brainwashed by Redmond...

**maybe apt-get/synaptic should change the nomenclature to “download” instead of “install”...**

I realize you have much more important things to do beside help a newb like me get my nVidia drivers installed, however, I can't find a "how-to" on this subject that works. Most involve bypassing the nVidia installer altogether and just compiling your own kernel with the drivers embedded. That seems to be just as daunting a task...

---

### Post by pseudonym on 2005-01-29
You need to install the appropriate linux headers for your kernel, via synaptic or apt-get. These let the nvidia installer know how your kernel is configured and thus enable it to compile the driver (although don't ask me to delve too deeply into the specifics :) ).

This 'quick and dirty' method is how I got mine installed - check back in this thread a couple of pages. It's not tracked by package management (like the kernel recompile method is) but you will have an installed and working nvidia 6629 driver at the end of it.

---

### Post by liuter2045 on 2007-05-15
Re: Geforce 6600GT and 6699 drivers..
[Pay Day Loans pollution chemistry physics Girls](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

### Post by senias6163 on 2007-05-15
> **panickedthumb said:**
> try typing glxgears into a terminal and see what average fps you get


[music biology bread Mortgages Cash Advance](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

