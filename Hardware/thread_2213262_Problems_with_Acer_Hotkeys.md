---
title: "Problems with Acer Hotkeys"
date: 2014-03-25
forum: Hardware
---

### Post by cespuny on 2014-03-25
Hi all, 


I have a problem with hotkeys for my laptop Acer Travelmate 292Lmi. 
When installing the module I get the following error. 


```


FATAL: Error inserting acerhk (/ lib/modules/3.2.0-60-generic/updates/dkms/acerhk.ko): Invalid module format 

```


I read on some forum that this module is not compatible with newer versions of the kernel! 
Without this my wifi card doesn't work :cry: 


Does anyone have any idea how to fix it? 


I add the last lines of dmesg, maybe it helps! 


```


[34.473093] ipw2200: Failed to send POWER_MODE: Command timed out. 
[36.400040] eth0: no IPv6 routers present 
[769.784252] acerhk: disagrees acerca version of symbol module_layout 
[2597.710429] acerhk: disagrees acerca version of symbol module_layout 

```


Thank you very much!

---

### Post by cespuny on 2014-03-28
No one??  :cry::cry::cry:

---

### Post by bapoumba on 2014-03-28
Not that I have any experience with this..

Looks like you are on Precise, how did you install acerhk ?

Looking at the error, may be that the module has not been compiled with the same gcc version as your kernel :
[http://forums.gentoo.org/viewtopic-t-424927-view-previous.html?sid=c6e96b4ace29bee47725c1bfa81a3000](http://forums.gentoo.org/viewtopic-t-424927-view-previous.html?sid=c6e96b4ace29bee47725c1bfa81a3000)

Is there a module compatible with your kernel ? To find your kernel version and the gcc version you are using :
```
uname -r
gcc -v
```

---

### Post by cespuny on 2014-03-28
Hello Bapoumba, thanks for your reply!

Yes, I'm using Lubuntu 12.04 (Precise Pangolin)

I installed acerhk following this instructions:
[http://askubuntu.com/questions/166328/acer-laptop-intel-2200bg-wireless-disabled-by-hardware-switch-irrespective-o](http://askubuntu.com/questions/166328/acer-laptop-intel-2200bg-wireless-disabled-by-hardware-switch-irrespective-o)

But when I try to execute point 3) I get the "[COLOR=#000000][FONT=Ubuntu Mono]Invalid module format"[/FONT][/COLOR] error.

The result of uname & gcc is:

```
cespuny@Portatil:/usr/src/acerhk-0.5.35$ uname -r
3.2.0-60-generic
cespuny@Portatil:/usr/src/acerhk-0.5.35$ gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 

```

Thank you very much!!!

---

### Post by bapoumba on 2014-03-28
From here : [https://launchpad.net/acerhk](https://launchpad.net/acerhk), the last version is from 2009, so I guess that is the problem. Looks more up to date here : [http://sourceforge.net/projects/acerhkgui/](http://sourceforge.net/projects/acerhkgui/), with a support thread here : [http://ubuntuforums.org/showthread.php?t=1059704](http://ubuntuforums.org/showthread.php?t=1059704).

---

### Post by cespuny on 2014-04-02
I found a hardcore solution!!

Putting a piece of tape over the pin that deactivates the card I have disabled the fisical button and now I can connect to wireless nets!!

---

### Post by bapoumba on 2014-04-02
> **cespuny said:**
> I found a hardcore solution!!

Putting a piece of tape over the pin that deactivates the card I have disabled the fisical button and now I can connect to wireless nets!!

Lol, hardcore solutions FTW!

---

