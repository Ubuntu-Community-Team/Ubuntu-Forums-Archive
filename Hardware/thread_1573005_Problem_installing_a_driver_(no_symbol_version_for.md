---
title: "Problem installing a driver (no symbol version for module_layout)"
date: 2010-09-12
forum: Hardware
---

### Post by orion188 on 2010-09-12
Hay guys,

I've downloaded driver files for a recently purchased hardware. They claim on their website that the driver files are up to date. But these are the results I get when try to install it on my Ubuntu 9.10 (uname -r -> 2.6.31-14-generic):

[B]>sudo insmod foo.ko
insmod: error inserting 'foo.ko': -1 Invalid module format

>dmesg
[28405.478898] foo: no symbol version for module_layout

>modinfo foo.ko
filename:       foo.ko
license:         GPL
author:          bar Team
vermagic:      2.6.18-4-686 SMP mod_unload 686 REGPARM gcc-4.1
depends:        
[/B]
After googling on the web, I did not find any clear info about what this "module_layout" means and how it should be solved. My own guess is that it has to do with version incompatibility (although the error messages are a little bit different). 

So what I tried to do was to compile the source files of this driver against linux-headers (current version, i.e.  2.6.31-14-generic). But there are again lots of problems, such as "function xxx wants 2 input arguments, provided 3 , lab lab lab" and other ones which I think show that it's not possible to compile them with current headers.

so the questions:

1- What does that module_layout thing mean and isn't it possible to deal with  the already-built modules and install them without messing with the source code?

2- If I have to start from the source, which version of the linux headers should I download? Or better to ask are the headers enough or should I also download the rest of the linux source files? Where can I find these files?

Thanks in advance for your kind help.

P.S: I've also tried **modprobe** (even **-f**) with no success. But the weird thing is that during my several attempts, only once **modprobe** was successful, and I could see my module in **lsmod**! But after doing a **modprobe -r** (to find out if this is repeatable), it never happened again!

---

### Post by dino99 on 2010-09-12
which hardware is it exactly ?

---

### Post by orion188 on 2010-09-12
Thanks for your reply.

It's a DAC (Digital to Analog Converter) card from Advantech.
The product page is [this]("http://www.advantech.com.tw/products/12-bit-4-ch-Analog-Output-PCI-Card-with-16-ch-DI-O/mod_1-2MLH3S.aspx") & the drivers (source and packages) are located [here]("http://support.advantech.com.tw/support/DownloadSRDetail.aspx?SR_ID=1-41GHVV&Doc_Source=Download") (You can also find the 2 specific modules attached to this post).

Looking forward

---

