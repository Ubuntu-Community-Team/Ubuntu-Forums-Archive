---
title: "LinuxDNA"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2009-02-26
Just came across this article about a "High Performance Linux Kernel"
called [LinuxDNA](http://www.linuxdna.com/)

It's a version of a kernel compiled using "Intel C/C++ Compiler" 
[B]
[http://preview.tinyurl.com/cwmum6](http://preview.tinyurl.com/cwmum6)[/B]

They claim to get a 40% speed increase. They site tells you how to compile kernel version 2.6.22. (they were running Gentoo.) It can be used with any Version of Linux and with a more recent kernel with a bit of tweaking.

Just wondering if anyone has tried this yet? (My attempts at Kernel compiling have always failed for one reason or another!) It's a very interesting project.

---

### Post by cmbryan on 2009-02-27
Ditto, I'm really curious about this!  Would it be possible to compile the ubuntu-patched kernel with ICC???

I don't need step-by-step instructions, but I'm sure someone smarter than me could say whether it is remotely possible or not...

---

### Post by thaidog on 2009-02-27
> **solitaire said:**
> Just came across this article about a "High Performance Linux Kernel"
called [LinuxDNA](http://www.linuxdna.com/)

It's a version of a kernel compiled using "Intel C/C++ Compiler" 
[B]
[http://preview.tinyurl.com/cwmum6](http://preview.tinyurl.com/cwmum6)[/B]

They claim to get a 40% speed increase. They site tells you how to compile kernel version 2.6.22. (they were running Gentoo.) It can be used with any Version of Linux and with a more recent kernel with a bit of tweaking.

Just wondering if anyone has tried this yet? (My attempts at Kernel compiling have always failed for one reason or another!) It's a very interesting project.

Glad to hear you are interested in out project :) Let me know if there is anything in particular I can help you with!

---

### Post by thaidog on 2009-02-27
> **cmbryan said:**
> Ditto, I'm really curious about this!  Would it be possible to compile the ubuntu-patched kernel with ICC???

I don't need step-by-step instructions, but I'm sure someone smarter than me could say whether it is remotely possible or not...

Compiling the kernel should be straight forward. Right now we have a "vanilla" 2.6.22 kernel on the mirror simply because it is easier to keep track of our changes alone.

---

### Post by solitaire on 2009-02-27
> **thaidog said:**
> Glad to hear you are interested in out project :) Let me know if there is anything in particular I can help you with!

Thanks

I'm currently away from my main Internet connection so I'll not be able to get the ICC downloaded and installed to play about with kernal building.
  
I've a old laptop that's just waiting for a project to occupy it :D

---

### Post by vemon on 2009-02-27
Is it possible to patch LinuxDNA with Ingo Molnar's real time preempt patch and still be able to compile with the intel compiler?

It would rock to get some speed increase to my 1,2Ghz celeron laptop but I really need the real-time kernel for running JACK and other music production related stuff.

---

### Post by thaidog on 2009-02-27
> **vemon said:**
> Is it possible to patch LinuxDNA with Ingo Molnar's real time preempt patch and still be able to compile with the intel compiler?

It would rock to get some speed increase to my 1,2Ghz celeron laptop but I really need the real-time kernel for running JACK and other music production related stuff.

We have not tested with that patch but I do not see anything that would keep it from working. Other patches we have tested like the desktop ck-sources patch work fine.

---

### Post by mothersh1p on 2009-03-07
> **thaidog said:**
> glad to hear you are interested in out project :) let me know if there is anything in particular i can help you with!

Here is my experience with the Linux-DNA Kernel 2.6.22 (SUSE 11.1, I'm sorry...): Sometimes the computer randomly logs me out without totally freezing (I can log me in again). In menuconfig I'm missing the option "ondemand" as the default cpu-frequency scaling algorithm. Maybe this is a version related issue (I'm a Linux-Newbee). Everything else is working like it should. :)

Edit: It works! I have succesfully compiled a recent version of the Zen-Kernel ([http://www.zen-sources.org](http://www.zen-sources.org)) with icc! Older version didn't work out-of-the-box. 

dmesg:
>Linux version 2.6.29-rc7-zen2 (root@Optimus) (Version >10.1 ) #48 Mon Mar 9 14:40:58 CET 2009

uname -a:
>Linux Optimus 2.6.29-rc7-zen2 #48 Mon Mar 9 14:40:58 >CET 2009 i686 i686 i386 GNU/Linux

(Where is the 10.1 gone!?)

The trick is to replace the file vmlinux compiled with icc with the one compiled with gcc. Remember vmlinux is the uncompressed kernel. Make vmlinux with icc first (make vmlinux HOSTCC=intelwrapper ...). Backup vmlinux somewhere. Make vmlinux with gcc. Override vmlinux with the one we saved and issue make bzImage (with gcc!!!). gcc will hopefully use the (wrong) vmlinux. But it works! It is not necessary to use an old Linux 2.6.22... :). I have tried several optimization flags. IPO is not working!!! Here are my flags: -fno-builtin -O3 -no-prec-div -prefetch -ansi-alias -unroll4 -funroll-loops. Not sure what they all means. But they work. Compilation with ICC is working but the bzImage won't boot. It would be interesting to use the wrapper script with gcc.

---

### Post by mothersh1p on 2009-03-09
I get this error when compiling:

```
376 section headers supported: 100
make[2]: *** [arch/i386/boot/compressed/vmlinux.relocs] Fehler 1
make[1]: *** [arch/i386/boot/compressed/vmlinux] Fehler 2
make: *** [bzImage] Fehler 2

```

Here is the patch:

```
diff --git a/arch/x86/boot/compressed/relocs.c b/arch/x86/boot/compressed/relocs.c
index edaadea..668a48b 100644
--- a/arch/x86/boot/compressed/relocs.c
+++ b/arch/x86/boot/compressed/relocs.c
@@ -10,7 +10,7 @@
#define USE_BSD
#include <endian.h>

-#define MAX_SHDRS 100
+#define MAX_SHDRS 200
#define ARRAY_SIZE(x) (sizeof(x) / sizeof((x)[0]))
static Elf32_Ehdr ehdr;
static Elf32_Shdr shdr[MAX_SHDRS];
```

---

### Post by Yaspoon on 2009-04-06
Hey guys. I am pretty newb to kernel compiling. I have got the kernel sources for linux dna and today I downlloaded ICC 11.0.083 the one they released today and I cannot get it to compile on ubuntu 8.10 I am getting mass errors. The file tree seems to be completely different from that of the guides. it goes /opt/intel/compiler/11.0/083/ and so on is there any way to compile using icc 11.0.083 any help is much appreciated.

---

### Post by mothersh1p on 2009-05-23
Did you tried linux-dna-2.6.29.1.tar from [www.linuxdna.com?](www.linuxdna.com?) It should work with 11.0.083, too. Just change all the paths into opt/intel/compiler/11.0/081/ and so on.

---

