---
title: "Help compiling kernel 2.6.33"
date: 2010-03-11
forum: Hardware
---

### Post by bruno9779 on 2010-03-11
I need to compile the latest kernel, to have (finally) decent support for my K10 thermal-sensors.

Now, I can download the kernel source and compile it fine, but then I always have some module missing.

Is there a way to extrapolate the current kernel's menuconfig or gconfig, so I can only add the thermal sensor's module when recompiling?

thanks

PS: I have been following this howto : [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)

---

### Post by Dedoimedo on 2010-03-11
Are you looking for the configuration file, it should be in your sources directory .config. Or under /proc/config.gz for the current running kernel.

You can manually edit the .config file and recompile.

Dedoimedo

---

### Post by bruno9779 on 2010-03-11
great. In the source folder as you said.

```
sudo find / -name .config
/usr/src/linux-2.6.32.2/.config
/usr/src/linux-headers-2.6.31-20-generic/.config
/usr/src/linux-headers-2.6.31-19-generic/.config
/root/.config
/home/bruno/.config
/var/lib/gdm/.config

```

There is another thing I need an explanation about: linux-headers.

When I compile the kernel myself, I don't see this being created. Do I have to do it manually somehow?

---

### Post by Dedoimedo on 2010-03-11
I am not sure what you're asking.

You can find the kernel headers in the repos for your running kernel as well as other versions. This allows you to compile modules even for a non-running kernel.

What's in your Makefile?

Probably: make -C /lib/modules/$(shell uname -r)/build M=$(PWD)

You can change this and hard-code the version you want to use.

I hope we're transmitting on the same wavelength.


Cheers,
Dedoimedo

---

### Post by bruno9779 on 2010-03-11
I am not completely sure myself.
I am trying to make sure I am not overlooking anything, as it is the first time I compile a kernel because I need to.
I have done it before out of curiosity and fun, but while bootable, my kernels have been full of issues.

I have to wait till tonight after work to try and compile it, I'll post back

---

### Post by Ayuthia on 2010-03-11
If you are just looking for k10temp, you might try this [thread]("http://ubuntuforums.org/showthread.php?t=1287819&highlight=k10").  It just supplies the k10temp module.  That way you don't have to figure out how to configure the kernel and compile it.

This might be the better way so that you don't have to worry about breaking anything else when you compile your kernel.

---

### Post by bruno9779 on 2010-03-11
> **Ayuthia said:**
> If you are just looking for k10temp, you might try this [thread]("http://ubuntuforums.org/showthread.php?t=1287819&highlight=k10").  It just supplies the k10temp module.  That way you don't have to figure out how to configure the kernel and compile it.

This might be the better way so that you don't have to worry about breaking anything else when you compile your kernel.

I have been doing that at every kernel upgrade.

it is annoying enough to recompile the drivers, but it would be worth it if the WORKED. I f you look deep into it in lm-sensors website, you'll see that the module for k10 sensors is deprecated, as it gives results so inaccurate, that can almost be considered random.

I don't want a workaround, I want the latest kernel on my system, and I want it to be configured exactly as my current one, plus k10 support

---

### Post by Ayuthia on 2010-03-11
You might try this [guide]("http://ubuntuforums.org/showthread.php?t=311158").  It should help get you kernel built.  

However, if you want to use your guide, you will need to copy the .config from your current linux-header and place it in the 2.6.33 source (I would backup the 2.6.33 .config before copying over it).  Then you can update the .config file:
```
sudo make oldconfig
```
It should ask you some questions about new things that are being added and one of them should be about k10temp.  Once that is complete, you should be able to do the normal make commands.

As for the linux-headers, if you want those, you need to find the Ubuntu way of compiling the kernel like this [guide]("https://help.ubuntu.com/community/Kernel/Compile").  That guide is old, but it creates the .deb files like Ubuntu does it.  However, the 2.6.33 source is pretty much the same thing.  I use Gentoo and build my own kernels.  I generally just download the kernel source and place it in /usr/src and build it there.  /lib/modules/`uname -r`/build will then point to /usr/src/linux-2.6.33 instead of linux-headers-2.6.XX.

I hope that helps.

---

### Post by Objekt on 2010-03-11
Clueless n00b question: other than including something specialized, like the K10 module, what benefit is there to compiling one's own kernel?  I haven't the slightest idea how to compile a kernel, and have never felt it necessary to try.

---

### Post by Ayuthia on 2010-03-11
> **Objekt said:**
> Clueless n00b question: other than including something specialized, like the K10 module, what benefit is there to compiling one's own kernel?  I haven't the slightest idea how to compile a kernel, and have never felt it necessary to try.

Usually one would update a kernel if there is something hardware specific that has either been created (like the k10temp module) or updated such has KMS (kernel mode setting--I think) support for the ATI graphics card.

Some people like to customize the kernel so that it only contains the information needed for their computer instead of having it be generic for most computers.  There is some discussions that it will make their computer faster, but I am not for sure if it really would make it significantly faster.

I would say that for most people, creating your own kernel is not needed.

---

### Post by Dayofswords on 2010-03-11
ahhhh 2.6.33

want that gamecube and wii support huh lol

---

### Post by bruno9779 on 2010-03-11
> **Ayuthia said:**
> You might try this [guide]("http://ubuntuforums.org/showthread.php?t=311158").  It should help get you kernel built.  

However, if you want to use your guide, you will need to copy the .config from your current linux-header and place it in the 2.6.33 source (I would backup the 2.6.33 .config before copying over it).  Then you can update the .config file:
```
sudo make oldconfig
```
It should ask you some questions about new things that are being added and one of them should be about k10temp.  Once that is complete, you should be able to do the normal make commands.

As for the linux-headers, if you want those, you need to find the Ubuntu way of compiling the kernel like this [guide]("https://help.ubuntu.com/community/Kernel/Compile").  That guide is old, but it creates the .deb files like Ubuntu does it.  However, the 2.6.33 source is pretty much the same thing.  I use Gentoo and build my own kernels.  I generally just download the kernel source and place it in /usr/src and build it there.  /lib/modules/`uname -r`/build will then point to /usr/src/linux-2.6.33 instead of linux-headers-2.6.XX.

I hope that helps.

:KS:KS:KS:KS:KS

Exactly the info I was looking for. I didn't know enough to make the right question, but this covers every doubt I had this far.
Down to the action now.

Many thanks.

@ Dayofswords

Thanks for letting me know of GC and Wii support! gotta try them out! (duh, I don't own any GC or Wii game...)

---

### Post by bruno9779 on 2010-03-12
For the record, there is an issue with the kernel-package version.

The one from repo (11.015) gives the following error:

```
This is kernel package version 11.015.
echo "The UTS Release version in include/linux/version.h"; echo "	   \"\" "; echo "does not match current version:"; echo "	   \"2.6.33-k10\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/version.h
	   "" 
does not match current version:
	   "2.6.33-k10" 
Please correct this.
make[1]: *** [debian/stamp/install/linux-image-2.6.33-k10] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.33'
make: *** [kernel_image] Error 2

```

I have found some bugs reports about it ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=561569)), and the workaroud is installing the newest kernel-package.
I have only found 11.033 for debian squeeze ([http://packages.debian.org/squeeze/all/kernel-package/download](http://packages.debian.org/squeeze/all/kernel-package/download)), and it works fine.

Now I am waiting for the compiling to finish...

---

### Post by bruno9779 on 2010-03-12
Well, it failed.

following this instructions should have given me 2 .deb, but instead I got only one.

Installing it partially fails at the postinst.d part.

The system boots with a string of errors and in low graphics mode because the Nvidia module fails. After a few attempts I have removed the kernel, and will try again in a while

---

### Post by fuzzyk.k on 2010-03-12
I believe i support the writer too

---

### Post by Ayuthia on 2010-03-12
> **bruno9779 said:**
> Well, it failed.

following this instructions should have given me 2 .deb, but instead I got only one.

Installing it partially fails at the postinst.d part.

The system boots with a string of errors and in low graphics mode because the Nvidia module fails. After a few attempts I have removed the kernel, and will try again in a while

I ended up moving /etc/kernel/postinst.d/nvidia-common to my home directory and ran it again and it worked.  I don't have an NVidia card in this laptop so it was not an issue for me but from your message, it looks like it wasn't an issue there either.  You will be left at the console prompt until you can rebuild the NVidia driver.

I did get both the header and the image .deb when I ran mine though.  As for the NVidia module failing, that is expected.  You will most likely have to download the driver from the NVidia site because I think that some changes were needed to make it work with 2.6.33 but I could be wrong (ATI had that problem). 

Basically any kernel module (like the Broadcom STA module or NVidia) that you had to install through Ubuntu, you will have to download manually and build.

---

