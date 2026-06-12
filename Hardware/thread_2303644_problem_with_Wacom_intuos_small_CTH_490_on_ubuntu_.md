---
title: "problem with Wacom intuos small CTH 490 on ubuntu 14.04 LTS"
date: 2015-11-20
forum: Hardware
---

### Post by nikoszr on 2015-11-20
I used several methods to make the tablet work and be recognised by the system but all have failed. 
I used the instruction on this video to update the grub: [https://www.youtube.com/watch?v=FMM0n_fuqlA&feature=youtu.be](https://www.youtube.com/watch?v=FMM0n_fuqlA&feature=youtu.be)
It didn't work and what's more I can't re-update any more the grub to the initial setting as the "save" button is disabled after the sudo update-grub. 
Then I tried to follow these instructions: [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver)
The ppa method doesn't work as well and the "compiling the driver manually" and the [COLOR=#333333][FONT=Ubuntu]./configure returned errors. ("[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]You should make sure that "./configure" and "make" aren't returning errors. If they are, you can try googling for the error text, or asking in the ubuntuforums support thread at [/FONT][/COLOR][http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)")
Is there someone who could help me solve the problem?
Please note, I am new linux user, and not a native english speaker. 
Thank you

---

### Post by mörgæs on 2015-11-20
Hi, welcome to the fora.

A brief googling yields this: 
[http://askubuntu.com/questions/670766/wacom-intuos-art-cth-490-does-not-work-ubuntu-15-04](http://askubuntu.com/questions/670766/wacom-intuos-art-cth-490-does-not-work-ubuntu-15-04)

The developers are aware of the problem.

As this is a new tablet I would try 15.10 first. Wacom is generally speaking well supported in Buntu but old software is a pain.

---

### Post by nikoszr on 2015-11-21
Well, thanks for replying
I checked my device's ID in [http://linuxwacom.sourceforge.net/wiki/index.php/Device_IDs](http://linuxwacom.sourceforge.net/wiki/index.php/Device_IDs) 
My device is almost at the end of the list (056a:033c CTH 490) but I can't make sense if it is suported or not. What does this "expected" is supposed to mean? 
Also when I plug in the devise and I use lsusb the device is detected by the system but It just doesn't work.

---

### Post by mörgæs on 2015-11-21
It means that support is expected in kernel 4.4, which is not generally available as of now. 

14.04 is far behind and it seems that 15.10 is not even new enough. 

If you are into some experimenting you could try the (young and probably unstable) 4.4 kernel but it could take some manual work.

---

### Post by nikoszr on 2015-11-21
OMG this is horrible! Very disapponting! I just bought this tablet, just few days ago, and I don't seem to be able  to work with it in the near future!.... If I had known there were problems with ubuntu I wouldn't have bought it or at least I would have done a more thorough research on the internet about its compatibility with ubuntu. But having seen there are already drivers for wacom within ubuntu I didn't even think about such a possibility!... 
I don't really know how to experiment with kernel.. I'm not a pc exepert. Perhaps with some guidence I could manage to do it... But it depends on how complicated is that, and how risky for my system and data etc.

---

### Post by mörgæs on 2015-11-22
> **nikoszr said:**
> But having seen there are already drivers for wacom within ubuntu...

Please post a link if you have found something for the 490.

---

### Post by nikoszr on 2015-11-22
I'm not sure about what you mean. 
What I mean is that I just saw the "wacom tablet" icon within the "system settings" of ubuntu and it has never occured to me that it would be so compilcated for a system to recognise and run a touch-tablet! Honestly, if I had imagined I would have made a research on the internet before buying.

---

### Post by nikoszr on 2015-11-22
I have also tried pluging it in through booting by a 15.10 ubuntu live cd but as you've already guessed it still isn't recognised.

---

### Post by mörgæs on 2015-11-22
You can see the Wacom icon as Ubuntu acknowledging Wacom's good intentions to support the Linux environment. There would not be an icon for a Linux-hostile company.

However, regarding new tablets there could be a delay from the drivers are written until they are *generally *available to the public, first of all they have to go through quality checks. You can ask in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") how to run kernel 4.4 though it's not part of the official Ubuntu release yet, it may be perfectly stable on your system though not on all hardware configurations out there.

---

### Post by nikoszr on 2015-11-22
Yes, I see all those things now... 
I don't really know what to do, I'm so confused. Perhaps I'll do what you recomend, although I'm not sure if I am able to do it in case its something complicated and difficult.  
Thanks for your support anyway!

---

### Post by zeke2135 on 2015-11-22
There is a way short of updating the kernel to get this model working. You can compile and install a new kernel module. The source code is available on SourceForge. I believe it is supported on kernels 3.17 and later. I have kernel 3.19 and it works with a CTH 690, which is the larger version. Unfortunately the version available on the web site does not seem to work with the wireless accessory (purchased separately). There are several steps, but they are pretty straightforward, at least on my setup. To me that seems much less difficult and less risky than installing a brand-new kernel. If you are interested in trying that, I can post the steps I used to install.

---

### Post by nikoszr on 2015-11-23
Hello, thanks for replying.
> **zeke2135 said:**
>  I believe it is supported on kernels 3.17 and later. I have kernel 3.19 and it works with a CTH 690, which is the larger version.
My kernel is 3.13.Do you think it will work? Is there a way to check it out?

---

### Post by zeke2135 on 2015-11-23
I don't know if it will work w/ kernel 3.13. The pre-release version mentioned on the [linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") mailing list  specified 3.17 or later. I don't know if the current released version supports earlier kernels. The current 0.30.1 version is [here]("http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/"). You would need to compile and install it. I believe you have 14.04? In that case you can also upgrade your kernel to 3.19 using the [LTSEnablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). Note that you would have to recompile and install the input-wacom kernel module each time your kernel is updated if you install it from sourceforge.

---

### Post by nikoszr on 2015-11-24
Well.. I've already tried some things described here: [http://linuxwacom.sourceforge.net/wiki/index.php/Input-wacom](http://linuxwacom.sourceforge.net/wiki/index.php/Input-wacom)  and here: [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) and unless I made some mistake these didn't work for me either.  
So I've already tried the procedure you suggest (but I didn't remember the terminology). So I suppose those drivers and kernel modules are not supporting earlier kernels like mine. 
So do you think I should upgrade kernel to 3.19 and try again? I have ubuntu 14.04. I'm not quite sure of what do I have to do form the things described in the LTSEnablement Stack. Could you give me some guidence/advice? Thank you.

---

### Post by zeke2135 on 2015-11-24
When I tried the installation it didn't work w/o an additional step. The sudo make install put the built kernel module into /lib/modules/<kernel version>/extra/wacom.ko and using shell commands to load the module didn't seem to work. I had to copy the installed kernel module to /lib/modules/<kernel version/kernel/drivers/hid/wacom.ko and reboot. 

As far as updating the kernel, I'm not an expert and I can't really tell you what you should do or give you any guidance that would be better than the information in the link I gave you. It's up to you what you're comfortable with.

---

### Post by mörgæs on 2015-11-24
Here are some guys running [kernel 4.4]("http://ubuntuforums.org/showthread.php?t=2303120"). If the posts continue to be positive you could give it a try.

---

### Post by nikoszr on 2015-11-24
Well I upgraded succesfully and easily to kernel 3.19 (I followed the procedure as described here in the last post: [http://askubuntu.com/questions/598483/how-can-i-use-kernel-3-19-in-14-04-now](http://askubuntu.com/questions/598483/how-can-i-use-kernel-3-19-in-14-04-now)). 
But then when I tried to compile and install the kernel module I got the following errors in the end of the line:

checking for pkg-config... /usr/bin/pkg-config 
checking pkg-config is at least version 0.9.0... yes 
checking if gcc -std=gnu99 supports -Werror=unknown-warning-option... no 
checking if gcc -std=gnu99 supports -Werror=unused-command-line-argument... no 
checking if gcc -std=gnu99 supports -Wall... yes 
checking if gcc -std=gnu99 supports -Wpointer-arith... yes 
checking if gcc -std=gnu99 supports -Wmissing-declarations... yes 
checking if gcc -std=gnu99 supports -Wformat=2... yes 
checking if gcc -std=gnu99 supports -Wstrict-prototypes... yes 
checking if gcc -std=gnu99 supports -Wmissing-prototypes... yes 
checking if gcc -std=gnu99 supports -Wnested-externs... yes 
checking if gcc -std=gnu99 supports -Wbad-function-cast... yes 
checking if gcc -std=gnu99 supports -Wold-style-definition... yes 
checking if gcc -std=gnu99 supports -Wdeclaration-after-statement... yes 
checking if gcc -std=gnu99 supports -Wunused... yes 
checking if gcc -std=gnu99 supports -Wuninitialized... yes 
checking if gcc -std=gnu99 supports -Wshadow... yes 
checking if gcc -std=gnu99 supports -Wmissing-noreturn... yes 
checking if gcc -std=gnu99 supports -Wmissing-format-attribute... yes 
checking if gcc -std=gnu99 supports -Wredundant-decls... yes 
checking if gcc -std=gnu99 supports -Wlogical-op... yes 
checking if gcc -std=gnu99 supports -Werror=implicit... yes 
checking if gcc -std=gnu99 supports -Werror=nonnull... yes 
checking if gcc -std=gnu99 supports -Werror=init-self... yes 
checking if gcc -std=gnu99 supports -Werror=main... yes 
checking if gcc -std=gnu99 supports -Werror=missing-braces... yes 
checking if gcc -std=gnu99 supports -Werror=sequence-point... yes 
checking if gcc -std=gnu99 supports -Werror=return-type... yes 
checking if gcc -std=gnu99 supports -Werror=trigraphs... yes 
checking if gcc -std=gnu99 supports -Werror=array-bounds... yes 
checking if gcc -std=gnu99 supports -Werror=write-strings... yes 
checking if gcc -std=gnu99 supports -Werror=address... yes 
checking if gcc -std=gnu99 supports -Werror=int-to-pointer-cast... yes 
checking if gcc -std=gnu99 supports -Werror=pointer-to-int-cast... yes 
checking if gcc -std=gnu99 supports -pedantic... yes 
checking if gcc -std=gnu99 supports -Werror... yes 
checking if gcc -std=gnu99 supports -Werror=attributes... yes 
Package xorg-macros was not found in the pkg-config search path. 
Perhaps you should add the directory containing `xorg-macros.pc' 
to the PKG_CONFIG_PATH environment variable 
No package 'xorg-macros' found 
checking whether make supports nested variables... (cached) yes 
checking for doxygen... no 
configure: WARNING: doxygen not found - documentation targets will be skipped 
checking for rint in -lm... yes 
checking for XORG... no 
configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met: 

No package 'xorg-server' found 
No package 'xproto' found 
No package 'xext' found 
No package 'kbproto' found 
No package 'inputproto' found 
No package 'randrproto' found 

Consider adjusting the PKG_CONFIG_PATH environment variable if you 
installed software in a non-standard prefix. 

Alternatively, you may set the environment variables XORG_CFLAGS 
and XORG_LIBS to avoid the need to call pkg-config. 
See the pkg-config man page for more details. 

So I guess the last thing that remains is to update to 4.4?

---

### Post by mörgæs on 2016-01-25
Kernel 4.4 is now available in Buntu 16.04. 
Remember the usual warnings: 16.04 is still under development so don't expect it to be completely stable.

---

