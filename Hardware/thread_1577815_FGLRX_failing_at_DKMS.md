---
title: "FGLRX failing at DKMS"
date: 2010-09-19
forum: Hardware
---

### Post by aspiredfang on 2010-09-19
Hi, this morning I wiped the computer a clean sheet and have been having some issues with getting FGLRX back up and running. I run Xubuntu 10.04.1 (on 2.6.32-25 kernel but, the same problem happens with lesser versions) and everything else seems to work fine. I've managed to compile the latest version of Bluefish hiccup free, etc, etc.

More than anything, the fan noise of my graphics card when running like  this is a nightmare! I'm at the end of my Linux knowledge leash when  things like DKMS spit errors at me, please help.

To start, here is the lspci output in relation to my card:
> VGA compatible controller: ATI Technologies Inc Radeon HD 3870
    Subsystem: ATI Technologies Inc Device 2542
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfee0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 8c00 [size=256]
    [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon
The problem whilst trying to install the ATI driver throws up this message from the install script:
> Building for architecture x86_64
Building initial module for 2.6.32-25-generic

Error! Bad return status for module build on kernel: 2.6.32-25-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--configure):Following the trail to the DKMS make log
> DKMS make.log for fglrx-8.771 for kernel 2.6.32-25-generic (x86_64)
Sun Sep 19 18:07:02 BST 2010
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.771/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/firegl_public.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_acpi.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_agp.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_debug.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.o
/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c: In function &#8216;KCL_IOCTL_AllocUserSpace32&#8217;:
/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c:196: error: implicit declaration of function &#8216;compat_alloc_user_space&#8217;
/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c:196: warning: return makes pointer from integer without a cast
make[2]: *** [/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.771/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [kmod_build] Error 2
build failed with return value 2I've tried the open source, x-swat and proprietary driver, installing by Synaptic/Apt-get, the shell script, making the .deb files, purging and then retrying...all with the same result:confused:

I have been scooting around the forums and web for a good few hours now to no avail.

---

### Post by Cuchaz on 2010-09-19
Exact same problem here. I traced the problem down to the build log and it appears the module isn't compiling successfully.

This mailing list post seems to give a reason why, but doesn't provide fix.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2516506.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2516506.html)

Also, the ppa-purge package doesn't work (same problem), so I can't revert back without trying to uninstall the packages myself somehow.

FYI, I'm running Ubuntu on 2.6.32-24-generic with a Radeon Mobility HD 5470.

---

### Post by aspiredfang on 2010-09-19
It's kind of a relief to know other people are in the same boat about this. Still haven't been able to solve the problem here.

It got me thinking about what will happen if the display drivers of xorg get demodularised quite a lot *shivers and prays* These sorts of problems would straight up make certain distro's unusable or seriously nerf the ability to update

---

### Post by Cuchaz on 2010-09-19
Yeah, it's annoying that an update completely broke my graphics acceleration. I was able to get my compy working again by reverting to the ati open source driver. Sadly, for my chipset, that means no Compiz. I'm having a hard time getting Cairo-Dock to work correctly w/ Metacity. I hope they can fix fglrx soon.

---

### Post by dopehouse on 2010-09-19
I finally managed to downgrade from 10.9 to the original 10.4 from ubuntu.


[LIST=1]
[*]First completely "PURGE" the linux-image...-24 and the header files.
[COLOR=Red]Make sure, you have one of the previous kernels installed[/COLOR]
[*]Reboot (didn't work for me without it)
[*]Uninstall all fglrx related packages (fglrx throws an error, ignore this))
[*]Reboot (again, it didn't work for me without it)
[*]XOrg should know complain about missing driver and allow you to start with failsettings for this session
[*]Install the all fglrx packages again (reinstall fglrx package)
[*]Reboot and see if it works
[/LIST]
I hope I didn't forget a step.

Maybe it's relative save to install the linux-image and linux-heades generic packages again (which will reinstall the latest kernel update again, if you don't try to alter the fglrx packages again).

---

### Post by jms-ubuntu-en on 2010-09-20
I got fglrx-8.771 installed by downgrading kernel 2.6.32-25.44_amd64 to previous version 2.6.32-25.43_amd64 by downgrading packages:
linux-headers-2.6.32-25
linux-image-2.6.32-25-generic

I have now :

```
linux-headers-2.6.32-25                           2.6.32-25.43
linux-headers-2.6.32-25-generic                   2.6.32-25.44
linux-image-2.6.32-25-generic                     2.6.32-25.43
linux-libc-dev                                    2.6.32-25.44
```

After rebooting to older kernel fglrx-8.771 installed fine.

---

### Post by kelargo on 2010-09-20
I have this problem.  its really annoying.

how does one perform this purge : "linux-image...-24 and the header files" ?

and I dont have a laptop.. this is a problem with fglrx.

> 
# cat /var/lib/dkms/fglrx/8.723.1/build/make.log
DKMS make.log for fglrx-8.723.1 for kernel 2.6.32-25-generic (x86_64)
Mon Sep 20 21:53:07 EDT 2010
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.723.1/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.o
In file included from /var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:443:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function &#8216;KCL_SetPageCache_Array&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1316: warning: passing argument 1 of &#8216;KCL_ConvertPageToKernelAddress&#8217; makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.h:325: note: expected &#8216;void *&#8217; but argument is of type &#8216;long unsigned int&#8217;
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_acpi.o
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_agp.o
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_debug.o
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.o
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.c: In function &#8216;KCL_IOCTL_AllocUserSpace32&#8217;:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.c:196: error: implicit declaration of function &#8216;compat_alloc_user_space&#8217;
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.c:196: warning: return makes pointer from integer without a cast
make[2]: *** [/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.723.1/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [kmod_build] Error 2
build failed with return value 2





---

### Post by Giraffro on 2010-09-22
A fix has been released for Lucid; the version number is 2:8.723.1-0ubuntu5. If you use either of the Ubuntu-X PPA's, their packages have not been fixed and neither has the official installer from ATI, though it [will be fixed for the next release]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518/comments/53").

The update might not show up straight away depending on which update server you use. I use the UK server and it took a few hours to show up in lucid-proposed. If you can't wait, try changing the download server in Software sources to the main server.

---

### Post by kotnik on 2010-09-22
Got the same problem, and spent an hour trying to fix things. The only solution I found was to downgrade kernel to 2.6.32-21 (by removing all other linux-image packages) and manually install Ati Catalyst. But only Catalyst 10.7 worked, 10.8 and 10.9 could not be installed (the same/similar DKMS error).

Geez, how I wish I never bought Ati.

---

### Post by The J on 2010-09-22
I've been having these same problems with the 2.26.32-xx-Generic kernels on Kubuntu 10.04 64-bit and I was just now able to get the fglrx module to build without having to downgrade kernels.

Here's what I did.  Chances are some kernel developer will start yelling at me for doing this, but oh well. :P

As root, open up the file [FONT="Courier New"]/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/compat.h[/FONT] in a text editor, inserting your version of the kernel in place of mine.  That directory should be correct for both 32-bit and 64-bit systems.  Go to the very botton of the file; you'll see 

```
#endif /* _ASM_X86_COMPAT_H */
```.

Between that line and the curly brace ( **}** ) two lines above it, paste in the following:

```
static inline void __user *compat_alloc_user_space(unsigned long len)
{
	struct pt_regs *regs = task_pt_regs(current);
	return (void __user *)regs->sp - len;
}
```.

(It isn't really necessary that the function go exactly where I said to put it, but this will make sure that you don't accidentally paste it into another function or something like that.)

Now save the file and try reinstalling the fglrx drivers.  My xorg.conf file was messed up and causing problems for me, so check that before you restart X.  With any luck, you should now be rolling in fglrx goodness! :guitar:

I don't think that will hurt anything, but you can remove your changes to that file after you build the module if you want.



You may have noticed that the function I had you paste in looks very similar to another function in there called 'arch_compat_alloc_user_space'.  As far as I can tell, they are exactly the same except for the name and parameter type (unsigned long).  It appears that 'compat_alloc_user_space' was renamed to 'arch_compat_alloc_user_space' for just this version of the kernel, so really we just put the old one back for the ATI module builder to use.  This shouldn't hurt anything since the contents of the two functions are identical.

---

### Post by mambazo on 2010-09-23
I post a solution here. But I was completely wrong. So please ignore this.

---

### Post by mambazo on 2010-09-23
I can verify that this works!

---

### Post by redzed501 on 2010-09-24
> **The J said:**
> I've been having these same problems with the 2.26.32-xx-Generic kernels on Kubuntu 10.04 64-bit and I was just now able to get the fglrx module to build without having to downgrade kernels.

Here's what I did.  Chances are some kernel developer will start yelling at me for doing this, but oh well. :P

As root, open up the file [FONT="Courier New"]/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/compat.h[/FONT] in a text editor, inserting your version of the kernel in place of mine.  That directory should be correct for both 32-bit and 64-bit systems.  Go to the very botton of the file; you'll see 

```
#endif /* _ASM_X86_COMPAT_H */
```.

Between that line and the curly brace ( **}** ) two lines above it, paste in the following:

```
static inline void __user *compat_alloc_user_space(unsigned long len)
{
	struct pt_regs *regs = task_pt_regs(current);
	return (void __user *)regs->sp - len;
}
```.

(It isn't really necessary that the function go exactly where I said to put it, but this will make sure that you don't accidentally paste it into another function or something like that.)

Now save the file and try reinstalling the fglrx drivers.  My xorg.conf file was messed up and causing problems for me, so check that before you restart X.  With any luck, you should now be rolling in fglrx goodness! :guitar:

I don't think that will hurt anything, but you can remove your changes to that file after you build the module if you want.



You may have noticed that the function I had you paste in looks very similar to another function in there called 'arch_compat_alloc_user_space'.  As far as I can tell, they are exactly the same except for the name and parameter type (unsigned long).  It appears that 'compat_alloc_user_space' was renamed to 'arch_compat_alloc_user_space' for just this version of the kernel, so really we just put the old one back for the ATI module builder to use.  This shouldn't hurt anything since the contents of the two functions are identical.

yes thx ... your solution works fine ... ubuntu 10.04.1 amd64 linux-image-2.6.35-22-generic

---

### Post by kotnik on 2010-09-27
> **The J said:**
> I've been having these same problems with the 2.26.32-xx-Generic kernels on Kubuntu 10.04 64-bit and I was just now able to get the fglrx module to build without having to downgrade kernels.

Here's what I did.  Chances are some kernel developer will start yelling at me for doing this, but oh well. :P

As root, open up the file [FONT="Courier New"]/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/compat.h[/FONT] in a text editor, inserting your version of the kernel in place of mine.  That directory should be correct for both 32-bit and 64-bit systems.  Go to the very botton of the file; you'll see 

```
#endif /* _ASM_X86_COMPAT_H */
```.

Between that line and the curly brace ( **}** ) two lines above it, paste in the following:

```
static inline void __user *compat_alloc_user_space(unsigned long len)
{
	struct pt_regs *regs = task_pt_regs(current);
	return (void __user *)regs->sp - len;
}
```.

(It isn't really necessary that the function go exactly where I said to put it, but this will make sure that you don't accidentally paste it into another function or something like that.)

Now save the file and try reinstalling the fglrx drivers.  My xorg.conf file was messed up and causing problems for me, so check that before you restart X.  With any luck, you should now be rolling in fglrx goodness! :guitar:

I don't think that will hurt anything, but you can remove your changes to that file after you build the module if you want.



You may have noticed that the function I had you paste in looks very similar to another function in there called 'arch_compat_alloc_user_space'.  As far as I can tell, they are exactly the same except for the name and parameter type (unsigned long).  It appears that 'compat_alloc_user_space' was renamed to 'arch_compat_alloc_user_space' for just this version of the kernel, so really we just put the old one back for the ATI module builder to use.  This shouldn't hurt anything since the contents of the two functions are identical.

I am also confirming that this works, in my case with Catalyst 10.9 and 2.6.32-25-generic kernel.

But, if you first encounter problems with libGL.so.1.2 segfaulting, remove /etc/X11/xorg.conf and regenerate it with aticonfig --initial, and reboot afterwards. It should work fine then.

Thanks, The J.

---

### Post by DLohner on 2010-09-29
You can also add a patch to dkms.

Just create a new patch file named fglrx-2.6.32-24.patch (e.g.) in /usr/src/fglrx-<your fglrx version>/patches/ with the following code:

```

--- a/kcl_ioctl.c.orig
+++ b/kcl_ioctl.c
@@ -193,7 +193,7 @@ void ATI_API_CALL KCL_IOCTL_UnregisterConversion32(unsigned int cmd)
  */
 void* ATI_API_CALL KCL_IOCTL_AllocUserSpace32(long size)
 {
-    return compat_alloc_user_space(size);
+    return arch_compat_alloc_user_space(size);
 }
 
 #endif // __x86_64__

```Then edit the file dkms.conf in /usr/src/fglrx-<your fglrx-version>/ and add these two lines:

```

PATCH[2]="fglrx-2.6.32-24.patch"
PATCH_MATCH[2]="^2.6.32\-(2[4-9]+|[3-9][0-9]+)\-generic$"

```(Be sure to use the correct file name for your patch) If PATCH[2] is already defined, just choose the next free integer for the array index.

This way, you don't have to touch the kernel sources.

---

### Post by funnyperson1 on 2010-09-30
I'd like to confirm that The J's solution worked for me as well.  Thanks for the fix.  Hopefully ATI has this straightened out for the next release.

---

### Post by Abadon_ on 2010-09-30
I'm with Kubuntu lucid kernel 2.6.32-25-generic #44-Ubuntu and ATI Radeon HD 4330.

**lspci**

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series


> cat /usr/share/ati/fglrx-install.log 
Errors during DKMS module removal
Errors during DKMS module removal

Creating symlink /var/lib/dkms/fglrx/8.723/source ->
                 /usr/src/fglrx-8.723

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.723/build; sh make.sh --nohints --uname_r=2.6.32-24-generic --norootcheck......(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.723 with DKMS
[Error] Kernel Module : Removing fglrx-8.723 from DKMS

------------------------------
Deleting module version: 8.723
completely from the DKMS tree.
------------------------------
Done.


> genko@abadon:~$ **glxinfo** 
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
genko@abadon:~$ **glxgears** 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
genko@abadon:~$ 


I try and this:

> Got the same problem, and spent an hour trying to fix things. The only solution I found was to downgrade kernel to 2.6.32-21 (by removing all other linux-image packages) and manually install Ati Catalyst. But only Catalyst 10.7 worked, 10.8 and 10.9 could not be installed (the same/similar DKMS error).

but without success. Any ideas?

---

### Post by alphacrucis2 on 2010-10-01
AMD have issued a hot fix for Catalyst 10.9 to address this problem. Read here:

[ATI Catalyst™ Linux Driver broken after Linux kernel security update ]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

---

### Post by nickleus on 2010-10-01
> **alphacrucis2 said:**
> AMD have issued a hot fix for Catalyst 10.9 to address this problem. Read here:

[ATI Catalyst™ Linux Driver broken after Linux kernel security update ]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

thanks! that fixed everything!

---

### Post by logan85 on 2010-10-03
the hotfix works for me too...
thanks!

---

### Post by Abadon_ on 2010-10-04
> **alphacrucis2 said:**
> AMD have issued a hot fix for Catalyst 10.9 to address this problem. Read here:

[ATI Catalyst™ Linux Driver broken after Linux kernel security update ]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

The information provided did not solve my problem. :(

Can anyone that for who this works to explain in more details how exactlly insttal and configure this patch. Maybe I make something wrong

---

### Post by Abadon_ on 2010-10-06
> **alphacrucis2 said:**
> AMD have issued a hot fix for Catalyst 10.9 to address this problem. Read here:

[ATI Catalyst™ Linux Driver broken after Linux kernel security update ]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

How this working and for me. I remove from /usr/src/linux-headers-2.6.32-25-generic/arch/x86/include/asm/compat.h 

> static inline void __user *compat_alloc_user_space(unsigned long len)
{
	struct pt_regs *regs = task_pt_regs(current);
	return (void __user *)regs->sp - len;
}

For more information about this lines read previues posts in this topic.

---

### Post by crazyfuturamanoob on 2010-10-18
> **The J said:**
> I've been having these same problems with the 2.26.32-xx-Generic kernels on Kubuntu 10.04 64-bit and I was just now able to get the fglrx module to build without having to downgrade kernels.

Here's what I did.  Chances are some kernel developer will start yelling at me for doing this, but oh well. :P

As root, open up the file [FONT="Courier New"]/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/compat.h[/FONT] in a text editor, inserting your version of the kernel in place of mine.  That directory should be correct for both 32-bit and 64-bit systems.  Go to the very botton of the file; you'll see 

```
#endif /* _ASM_X86_COMPAT_H */
```.

Between that line and the curly brace ( **}** ) two lines above it, paste in the following:

```
static inline void __user *compat_alloc_user_space(unsigned long len)
{
	struct pt_regs *regs = task_pt_regs(current);
	return (void __user *)regs->sp - len;
}
```.

(It isn't really necessary that the function go exactly where I said to put it, but this will make sure that you don't accidentally paste it into another function or something like that.)

Now save the file and try reinstalling the fglrx drivers.  My xorg.conf file was messed up and causing problems for me, so check that before you restart X.  With any luck, you should now be rolling in fglrx goodness! :guitar:

I don't think that will hurt anything, but you can remove your changes to that file after you build the module if you want.



You may have noticed that the function I had you paste in looks very similar to another function in there called 'arch_compat_alloc_user_space'.  As far as I can tell, they are exactly the same except for the name and parameter type (unsigned long).  It appears that 'compat_alloc_user_space' was renamed to 'arch_compat_alloc_user_space' for just this version of the kernel, so really we just put the old one back for the ATI module builder to use.  This shouldn't hurt anything since the contents of the two functions are identical.

I did that and the drivers started working. Thanks! You are awesome. :)

---

### Post by mads65 on 2010-10-26
Thank you 'The J', your solution worked for me as well.

OS: Mint 9 32-bit
Kernel release: 2.6.32-25-generic
Catalyst 10.10 (ati-driver-installer-10-10-x86.x86_64.run)

By the way after installation I saw this reply from 'alphacrucis2':
" AMD have issued a hot fix for Catalyst 10.9 to address this problem...
[ATI Catalyst™ Linux Driver broken after Linux kernel security update]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx") ".

Three people have so far replied to the above post, two say it has solved their problem and one says it hasn't. Is this hot fix related to this issue? Description talks about "reduced performance" and "system crashes on boot up" which are not exactly what this thread is about.

Any way, thanks again for your genuine solution.

---

### Post by jdalt on 2010-10-27
Catalyst 10.10 fixes the problem. The DKMS/kernel fix applies to Catalyst 10.9. This should no longer be an issue.

---

### Post by mads65 on 2010-10-27
> **jdalt said:**
> Catalyst 10.10 fixes the problem. The DKMS/kernel fix applies to Catalyst 10.9. This should no longer be an issue.


Thank you. Yes it does. I don't know what I did wrong previously, but I did a fresh install of the driver and can confirm that Catalyst 10.10 works without any problems. My kernel: 2.6.32-25-generic

---

