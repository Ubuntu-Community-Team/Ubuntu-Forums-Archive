---
title: "FGLRX Module Assistant problem"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by juxtaposed on 2007-06-08
I tried to use module-assistant to get my ATI X200 (or something like that) Integrated graphics working, but when I do "build" in module-assistant. It worked a few weeks ago, but I reinstalled.

I'm on Debian Sid (too scared to ask in the debian forums for fear of getting yelled at, i've heard bad things) with 2.6.21-1-k7.

Here is what I think is the major error thing in module-assistant:
 FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol 'paravirt_ops'

I've googled it ([here is what I got]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg352953.html")), but all I can find is that I should patch something with something, which I have no idea how to do.

---

### Post by angryfirelord on 2007-06-08
I don't think you need to use module assistant. Just use the fglrx drivers.

[http://ubuntuforums.org/showthread.php?p=1975329]("http://ubuntuforums.org/showthread.php?p=1975329")

The people on the Debian forums are very knowledgeable, but don't worry about getting yelled at. If you do, it's usually by only 1 or 2 hardcore "do it yourself, rtfm" people. I should know because I'm registered there.

---

### Post by juxtaposed on 2007-06-08
> I don't think you need to use module assistant. Just use the fglrx drivers.

Whenever I installed fglrx, I had to do something to enable it or something. In ubuntu it was easy (restricted drivers manager :D), though a little harder with debian (module assistant). 

> The people on the Debian forums are very knowledgeable, but don't worry about getting yelled at. If you do, it's usually by only 1 or 2 hardcore "do it yourself, rtfm" people. I should know because I'm registered there.

I'm signed up there too, have been for a few years. I just don't like asking questions there, as i've heard so many things about them being elitest; I havn't seen it, but before I go to post a question, I always think about that, then post here or something.

---

### Post by neptho on 2007-06-08
What kernel are you using with Sid?

The modules incuded with Debian are fairly old; and I had no end of issues with them when I was running Etch.  I'd suggest, as mentioned, that you grab the latest script/archive from ATI/AMD, and run as follows:

sh name_of_at_driver.sh --buildpkg Debian/Sid

Then dpkg -i the kernel module and the kernel-src dpkgs.

You'll find fglrx.tar.bz2 in /usr/src
tar jxvf fglrx.tar.bz2; cd flgrx; sh make.sh
mkdir -p /lib/modules/`uname -r`/misc
cp fglrx.ko /lib/modules/`uname -r`/misc
depmod -ae

Then, rmmod fglrx; modprobe fglrx, and look at your dmesg. 

Good luck!

---

### Post by juxtaposed on 2007-06-08
> What kernel are you using with Sid?

2.6.21-1-k7

> I'd suggest, as mentioned, that you grab the latest script/archive from ATI/AMD, and run as follows:

I'm a little afraid of doing anything with those, as I messed up my install with it (though not the one where it makes .deb files, the normal install).

> sh name_of_at_driver.sh --buildpkg Debian/Sid

Then dpkg -i the kernel module and the kernel-src dpkgs.

You'll find fglrx.tar.bz2 in /usr/src
tar jxvf fglrx.tar.bz2; cd flgrx; sh make.sh
mkdir -p /lib/modules/`uname -r`/misc
cp fglrx.ko /lib/modules/`uname -r`/misc
depmod -ae

Then, rmmod fglrx; modprobe fglrx, and look at your dmesg.

Good luck!


I'd try that, though I don't know anything about modprobe, dmesg, or rmmod. I'll google them and see if I can find out though... If so, i'll probably try that :)

---

### Post by angryfirelord on 2007-06-08
> **juxtaposed said:**
> Whenever I installed fglrx, I had to do something to enable it or something. In ubuntu it was easy (restricted drivers manager :D), though a little harder with debian (module assistant).
You can:

1) Run ** dpkg-reconfigure xserver-xorg ** and select fglrx as your driver or

2) Go into your xorg.conf and under Driver, make it say "fglrx".

---

### Post by juxtaposed on 2007-06-08
> **angryfirelord said:**
> You can:

1) Run ** dpkg-reconfigure xserver-xorg ** and select fglrx as your driver or

2) Go into your xorg.conf and under Driver, make it say "fglrx".

Section "Device"
	Identifier	"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

though I dont have 3d:

patrick@debian:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).

patrick@debian:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

It's just like when I did this before, only then I could use module assistant to build the kernel module or whatever it is to make it work.

---

### Post by neptho on 2007-06-08
You're using the .21 kernel.  That breaks the fglrx module because they've removed SEVERAL macros.

Recompile the module (fglrx) after [applying this patch](http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.35.5-for-2.6.20.patch) to your fglrx sources (should be in /usr/src/modules/fglrx):

cd /usr/src/modules/fglrx; wget [http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.35.5-for-2.6.20.patch;](http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.35.5-for-2.6.20.patch;) patch -p0 < fglrx-8.35.5-for-2.6.20.patch; sh make.sh, then follow my other instructions above.

---

### Post by juxtaposed on 2007-06-08
I did one part of that and a part of it failed, but an other part seemed to work.

```
debian:/usr/src/modules/fglrx# patch -p0 < fglrx-8.35.5-for-2.6.20.patch
patching file firegl_public.c
Hunk #1 succeeded at 121 (offset 2 lines).
Hunk #2 FAILED at 207.
Hunk #3 succeeded at 4384 (offset -22 lines).
Hunk #4 FAILED at 5010.
Hunk #5 succeeded at 5206 (offset -16 lines).
2 out of 5 hunks FAILED -- saving rejects to file firegl_public.c.rej
debian:/usr/src/modules/fglrx# 

```

And then I did the next command:

```

debian:/usr/src/modules/fglrx# sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /usr/src/linux-headers-2.6.21-1-k7 SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.21-1-k7'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
In file included from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:336:
/usr/src/modules/fglrx/drmP.h:126:1: warning: "DRM_DEBUG_CODE" redefined
/usr/src/modules/fglrx/firegl_public.c:180:1: warning: this is the location of the previous definition
/usr/src/modules/fglrx/firegl_public.c:454: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;firegl_stub_open&#8217;:
/usr/src/modules/fglrx/firegl_public.c:577: warning: assignment discards qualifiers from pointer target type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pci_find_device&#8217;:
/usr/src/modules/fglrx/firegl_public.c:1777: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:470)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_do_mmap&#8217;:
/usr/src/modules/fglrx/firegl_public.c:1887: warning: assignment makes pointer from integer without a cast
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_request_irq&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2640: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_smp_call_function&#8217;:
/usr/src/modules/fglrx/firegl_public.c:4085: warning: passing argument 1 of &#8216;smp_call_function&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:4899: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_ExecuteAtLevel&#8217;:
/usr/src/modules/fglrx/firegl_public.c:4758: warning: &#8216;flags&#8217; may be used uninitialized in this function
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol 'paravirt_ops'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.21-1-k7'
make: *** [kmod_build] Error 2
build failed with return value 2


```

Which is similar, of not the same thing, as the module-assistant error.

---

### Post by neptho on 2007-06-09
> **juxtaposed said:**
> I did one part of that and a part of it failed, but an other part seemed to work.

```
debian:/usr/src/modules/fglrx# patch -p0 < fglrx-8.35.5-for-2.6.20.patch
patching file firegl_public.c
Hunk #1 succeeded at 121 (offset 2 lines).
Hunk #2 FAILED at 207.
Hunk #3 succeeded at 4384 (offset -22 lines).
Hunk #4 FAILED at 5010.
Hunk #5 succeeded at 5206 (offset -16 lines).
2 out of 5 hunks FAILED -- saving rejects to file firegl_public.c.rej
debian:/usr/src/modules/fglrx# 

```

That patch is against 8.35.5; Debian ships with 8.27, if memory serves.  If you want to use that patch, you'll have to look at the .rej files and try to hand-patch it together.

> **juxtaposed said:**
> And then I did the next command:

```

debian:/usr/src/modules/fglrx# sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /usr/src/linux-headers-2.6.21-1-k7 SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.21-1-k7'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
In file included from /usr/src/modules/fglrx/drm_proc.h:41,
                 from /usr/src/modules/fglrx/firegl_public.c:336:
/usr/src/modules/fglrx/drmP.h:126:1: warning: "DRM_DEBUG_CODE" redefined
/usr/src/modules/fglrx/firegl_public.c:180:1: warning: this is the location of the previous definition
/usr/src/modules/fglrx/firegl_public.c:454: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;firegl_stub_open&#8217;:
/usr/src/modules/fglrx/firegl_public.c:577: warning: assignment discards qualifiers from pointer target type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pci_find_device&#8217;:
/usr/src/modules/fglrx/firegl_public.c:1777: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:470)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_do_mmap&#8217;:
/usr/src/modules/fglrx/firegl_public.c:1887: warning: assignment makes pointer from integer without a cast
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_request_irq&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2640: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_smp_call_function&#8217;:
/usr/src/modules/fglrx/firegl_public.c:4085: warning: passing argument 1 of &#8216;smp_call_function&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:4899: warning: &#8216;kmem_cache_t&#8217; is deprecated
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_ExecuteAtLevel&#8217;:
/usr/src/modules/fglrx/firegl_public.c:4758: warning: &#8216;flags&#8217; may be used uninitialized in this function
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol 'paravirt_ops'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.21-1-k7'
make: *** [kmod_build] Error 2
build failed with return value 2


```

Which is similar, of not the same thing, as the module-assistant error.

Yeah, afraid it's not going to be fun or easy to make the default debian fglrx work; your best bet is to install the version available at ATI's site.  I can't help, anymore, as I've moved to Ubuntu, where it "just works."  Sorry.  :(

---

### Post by juxtaposed on 2007-06-09
> That patch is against 8.35.5; Debian ships with 8.27, if memory serves. If you want to use that patch, you'll have to look at the .rej files and try to hand-patch it together.


That sounds hard, complicated, and prone to error :/

> Yeah, afraid it's not going to be fun or easy to make the default debian fglrx work; your best bet is to install the version available at ATI's site.

I guess i'll have to try that then :/

> I can't help, anymore, as I've moved to Ubuntu, where it "just works." Sorry. 

Yea, everything just works in ubuntu; though I find debian faster, so I continue to use it.

Thanks for your help, I hope I can get the one from the site working :)

---

### Post by angryfirelord on 2007-06-14
It's now probably due to ATI being behind the times. Sid moves rather fast, which is one the reason I like Ubuntu, it fills the gap between Testing and Unstable.

---

### Post by angryfirelord on 2007-06-17
Ok, here's how I got it in Lenny (no guarantee in Sid):

In a terminal as root, run these commands:
```
apt-get install module-assistant
m-a prepare
m-a a-i fglrx
dpkg-reconfigure xserver-xorg

```
Before you say you already tried that, there was an issue with the fglrx drivers in Lenny. However, on forums.debian.net, I reported that it was working for me, so I think an update got slipped in there.

---

