---
title: "Drivers for AMD (ATI) Radeon HD 5670 in Ubuntu 12.04 LTS (Precise Pangolin)."
date: 2012-06-20
forum: Hardware
---

### Post by przemnet on 2012-06-20
Hello,

I've got problems with my AMD (ATI) Radeon HD 5670 in Ubuntu 12.04 LTS (Precise Pangolin).

I had 2GB of RAM (DDR2, PC6400, 800MHz), I added another 2GB so now I have 4GB (2x2GB) and I'm not able to install fglrx drivers. When I had 2GB of RAM I was not able to install drivers downloaded from ATI website according to these instructions [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide) but properitary drivers proposed by system were working fine (version with "post-release updates" did not work, but the other one was ok).

Now I'm not able to use any drivers proposed by system and I can't install drivers from ATI website- packages are built succesfully but during their instalation I got some errors.

Even when Ubuntu was starting from Live CD, there were some errors related to graphics card.

Did anyone succesfully installed ATI drivers in Ubuntu 12.04 LTS (Precise Pangolin)??? I checked the forum, but did not find any answer in below posts:

* # [SOLVED] Help with Radeon HD 5670 *
[http://ubuntuforums.org/showthread.php?t=1673024](http://ubuntuforums.org/showthread.php?t=1673024)
* # No display rotation with ATI Radeon HD 5670 *
[http://ubuntuforums.org/showthread.php?t=1691906](http://ubuntuforums.org/showthread.php?t=1691906)
* # ATI Radeon HD 5670 Mouse Lag*
[http://ubuntuforums.org/showthread.php?t=1537566](http://ubuntuforums.org/showthread.php?t=1537566)
* # XFX Radeon HD 5670 Won't work on ubuntu (not supported?) *
[http://ubuntuforums.org/showthread.php?t=1419962&page=4](http://ubuntuforums.org/showthread.php?t=1419962&page=4) (Claus 7)
* # Ubuntu 11.04 + Radeon 5670 + fglrx = slow. *
[http://ubuntuforums.org/showthread.php?t=1787310](http://ubuntuforums.org/showthread.php?t=1787310)
* # 11.04 - Dual HD5670's but only one at a time?*
[http://ubuntuforums.org/showthread.php?t=1768260](http://ubuntuforums.org/showthread.php?t=1768260)
* # Video Card Woes (HD 5670)*
[http://ubuntuforums.org/showthread.php?t=1424082](http://ubuntuforums.org/showthread.php?t=1424082)
* # XFX Radeon HD 5670 Won't work on ubuntu (not supported?)*
[http://ubuntuforums.org/showthread.php?t=1419962](http://ubuntuforums.org/showthread.php?t=1419962)

Looking forward,
Przemek.

---

### Post by Yellow Pasque on 2012-06-20
> **przemnet said:**
> packages are built successfully but during their installation I got some errors.

Works fine for me. Post the errors.

---

### Post by przemnet on 2012-06-22
Hello Temüjin,

Today I'm planning to make a fresh install so once I do it I'll post the logs.

Looking forward,
Przemek.

---

### Post by przemnet on 2012-06-22
Hello Temüjin,

below you can find output from generation and installation of fglrx packages:

```
**przemek@pc:~/Documents/ATI/driver_12_4$ chmod +x amd-driver-installer-12-4-x86.x86_64.run **
**przemek@pc:~/Documents/ATI/driver_12_4$ sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise**
Created directory fglrx-install.V09SGe
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-8.961.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/precise
Package /home/przemek/Documents/ATI/driver_12_4/fglrx_8.961-0ubuntu1_i386.deb has been successfully generated
Package /home/przemek/Documents/ATI/driver_12_4/fglrx-dev_8.961-0ubuntu1_i386.deb has been successfully generated
Package /home/przemek/Documents/ATI/driver_12_4/fglrx-amdcccle_8.961-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.V09SGe
przemek@pc:~/Documents/ATI/driver_12_4$ ls -l
total 149956
-rwxr-xr-x 1 przemek przemek 108360519 Jun 19 14:49 amd-driver-installer-12-4-x86.x86_64.run
-rw-r--r-- 1 przemek przemek  39228984 Jun 22 19:55 fglrx_8.961-0ubuntu1_i386.deb
-rw-r--r-- 1 przemek przemek   5887782 Jun 22 19:55 fglrx-amdcccle_8.961-0ubuntu1_i386.deb
-rw-r--r-- 1 przemek przemek     63406 Jun 22 19:55 fglrx-dev_8.961-0ubuntu1_i386.deb
-rw-rw-r-- 1 przemek przemek      1587 Jun 22 19:55 fglrx-installer_8.961-0ubuntu1_i386.changes
przemek@pc:~/Documents/ATI/driver_12_4$ sudo dpkg -i fglrx*.deb
[sudo] password for przemek: 
Selecting previously unselected package fglrx.
(Reading database ... 172029 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.961-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.961-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.961-0ubuntu1_i386.deb) ...
Setting up fglrx (2:8.961-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.961 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-25-generic-pae
Building for architecture i686
Building initial module for 3.2.0-25-generic-pae
[COLOR=Red]** Error! Bad return status for module build on kernel: 3.2.0-25-generic-pae (i686)**[/COLOR]
[COLOR=Red]** Consult /var/lib/dkms/fglrx/8.961/build/make.log for more information.**[/COLOR]
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.961-0ubuntu1) ...
Setting up fglrx-dev (2:8.961-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
**przemek@pc:~/Documents/ATI/driver_12_4$ sudo amdconfig --initial -f**
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0
przemek@pc:~/Documents/ATI/driver_12_4$ 

```It looks like there was error during module build.

And content of /var/lib/dkms/fglrx/8.961/build/make.log
```
DKMS make.log for fglrx-8.961 for kernel 3.2.0-25-generic-pae (i686)
Fri Jun 22 19:55:45 CEST 2012
AMD kernel module generator version 2.1
make.sh: 390: [: 1: unexpected operator
make.sh: 396: [: 1: unexpected operator
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.2.0-25-generic-pae/build SUBDIRS=/var/lib/dkms/fglrx/8.961/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic-pae'
  CC [M]  /var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.c: In function &#8216;KCL_fpu_begin&#8217;:
/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.c:5812:28: error: &#8216;TS_USEDFPU&#8217; undeclared (first use in this function)
/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.c:5812:28: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/var/lib/dkms/fglrx/8.961/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.961/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic-pae'
make: *** [kmod_build] Error 2
build failed with return value 2
```Do you know how to solve this issue?

Looking forward,
Przemek.

---

### Post by Yellow Pasque on 2012-06-22
[http://ubuntuforums.org/showthread.php?t=1969827](http://ubuntuforums.org/showthread.php?t=1969827)

---

### Post by przemnet on 2012-06-23
Hello Temüjin,

I followed instructions from your post, there were no errors during installation of generated *.deb packages, but unfortunately after I boot up the system, black or violet screen appears again...

Do you have any other ideas? What logs can I check?

Looking forward,
Przemek.

P.S. When I boot up from Live CD I get the following errors on screen (they appear very fast)

```
Failed to allocate
* <something that I did not manage to copy>*

[drm:radeon_ttm_backedn_bind] *ERROR* failed to bind 1280 pages at 0x00000000
radeon 0000:01:00.0: object _init failed for 
* <something that I did not manage to copy>*
```I don't know how to display them because /var/log/messages file does not exist and they do not appear in /var/log/Xorg.0.log

---

### Post by Yellow Pasque on 2012-06-23
Make sure you continue to follow the instructions on the wiki page about generating xorg.conf

Also, if the error still comes up, you may need to blaklist open-source radeon module and then reboot:
```
echo "blacklist radeon" | sudo tee -a /etc/modprobe.d/blacklist-radeon.conf
sudo depmod -a
```

---

### Post by przemnet on 2012-06-24
Hello Temüjin,

thanks for your tips. Unfortunatelly still drivers do not work...

Right after I install drivers and execute ```
sudo amdconfig --initial -f
``` fglrxinfo output and xorg.conf (before this command there was no /etc/X11/xorg.conf) are as follows:```
**przemek@pc:~/catalyst12.4$ sudo amdconfig --initial -f**
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-1
**przemek@pc:~/catalyst12.4$ cat /etc/X11/xorg.conf**
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

**przemek@pc:~/catalyst12.4$ fglrxinfo** 
display: :0  screen: 0
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 1.4 (2.1 Mesa 8.0.2)

przemek@pc:~/catalyst12.4$ 

```

I moved xorg.conf file to see if it causes problems, but after ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disabled
``` the problem was still present- black or violet screen.

After xorg.conf restoration ```
sudo mv /etc/X11/xorg.conf.disabled /etc/X11/xorg.conf
``` I tried to tune it according to wiki ```
sudo amdconfig --tls=0

sudo amdconfig --acpi-services=off
``` but without success...

Blacklisting radeon modules also did not help...

Ofcourse when I remove 2GB RAM and leave 2GB- system boots normally and fglrxinfo looks very good:```
**przemek@pc:~$ fglrxinfo **
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.2.11631 Compatibility Profile Context

**przemek@pc:~$ fgl_glxgears **
Using GLX_SGIX_pbuffer
3178 frames in 5.0 seconds = 635.600 FPS
4172 frames in 5.0 seconds = 834.400 FPS
4163 frames in 5.0 seconds = 832.600 FPS
4153 frames in 5.0 seconds = 830.600 FPS
4165 frames in 5.0 seconds = 833.000 FPS
4152 frames in 5.0 seconds = 830.400 FPS
4141 frames in 5.0 seconds = 828.200 FPS
4160 frames in 5.0 seconds = 832.000 FPS
4162 frames in 5.0 seconds = 832.400 FPS
^C
przemek@pc:~$ 


```

Problem is present only when 4GB are inserted...

It's not RAM issue, because I've got Windows 7 installed as well and it works fine, 4GB of memory are visible in the system. Besides when I installed Backtrack 5 which is based on Ubuntu 10.04 LTS, 12.4 catalyst drivers were working correctly with 4GB RAM inserted.

Used kernel should support 4GB of RAM```
przemek@pc:~$ uname -r
3.2.0-25-generic-**pae**
przemek@pc:~$
```


Maybe any other ideas???

Looking forward,
Przemek.

---

### Post by przemnet on 2012-06-26
Anyone? Any ideas???

What else can I do, should I open a bug report for Ubuntu? If yes, can I have short instructions how to do it?

Looking forward,
Przemek.

---

### Post by przemnet on 2012-07-03
Hello Experts,

I've installed the newest kernel avalible in repos (**3.2.0-26-generic-pae**), uninstalled old and installed the newest version of Catalyst drivers (**version 12.6**- this time I did not have to install the patch [http://phoronix.com/forums/showthread.php?68922-Patch-to-compile-fgrlx-module-on-Linux-3-3-rc4-with-x86-32-bit-arch](http://phoronix.com/forums/showthread.php?68922-Patch-to-compile-fgrlx-module-on-Linux-3-3-rc4-with-x86-32-bit-arch)) but unfortunatelly situation is still the same- violet screen...

Here [http://ubuntuone.com/1aFILwwVLV9f6jMqUdjDTN](http://ubuntuone.com/1aFILwwVLV9f6jMqUdjDTN) you can find logs (/var/log folder) that were collected via root console in recovery mode (still can not switch to other consoles with Ctrl+Alt+F1...F6):
- in folder _4GB_12_4_ there are logs collected when 4GB are inserted with 12.4 Catalyst drivers installed
- in folder _4GB_NO_12_4_fglrx_ there are logs when 4GB are inserted and 12.4 Catalyst drivers were removed
- in folder _4GB_12_6_ there are logs collected when 4GB are inserted with 12.6 Catalyst drivers installed

Could you have a look on provided logs- I'll appreciate your advices.

Looking forward,
Przemek.

---

### Post by przemnet on 2012-07-20
Hello Everyone!

Problem is SOLVED!

As per recommendation from fglrx bugtracker- **BIOS upgrade on my motherboard (Gigabyte GA-MA69G-S3H) was the solution!** I upgraded to the newest version which is F8E. I was able to install latest Catalyst 12.6 drivers succesfully.

I had problems with upgradeing BIOS from Windows XP and Windows 7, but upgrade directly from BIOS with Q FLASH worked perfectly! To do it, just download BIOS from Gigabyte site, extract the archive, copy BIOS file to USB stick, plug USB stick into computer, reboot system, hit "End" button during startup and select BIOS upgrade from HDD- you can find lots of videos on YouTube about that.

Many thanks for your help and support!

Looking forward,
Przemek.

P.S. I wanted to edit my initial post to put solution there (to avoid going through full discussion to search the answer), but I can not do it...

---

