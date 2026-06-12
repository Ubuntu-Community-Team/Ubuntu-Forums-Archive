---
title: "ATI 9700 Pro Drivers"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by Cobra78 on 2005-08-15
So, i'm sorry for my terrible english.

I ensure that i've searched the forum but don't find anithyng about my problem (maybe because i'm newbie in Linux world and don't know how to make a good search)

The problem is that wen i write "Driver "fgrlx"" in xorg.conf, xserver  dosen't start with the error "no device found".

I also tried to installa Ati driver, following many guides on this forum, but i get this error in fgrlx-install.log

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
Makefile:50: *** mixed implicit and normal rules.  Stop.
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.



Someon had any idea?

---

### Post by PeP on 2005-08-15
what kerenel version do you use
(uname -r)
what version(s) of linux-restricted-modules do you have? 
if it doesn't match, install the right linux-image // linux-restricted-modules to make it match.

(linux-restricted-modules are not available for all the kernel builds by ubuntu)

---

### Post by Cobra78 on 2005-08-15
So, i have:

kernel 2.6.10-5-386

linux-restricted-modules-2.6.10-5-386 version 2.6.10.5-1

linux-restricted-modules-386 version 2.6.10.7

linux-image-2.6.10-5-386 version 2.6.10-34.3

linux-image-386 version 2.6.10.7


Whath i need to make to solve the problem?

---

