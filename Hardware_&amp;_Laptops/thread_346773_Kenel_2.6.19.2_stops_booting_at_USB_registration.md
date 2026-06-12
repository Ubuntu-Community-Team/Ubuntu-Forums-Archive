---
title: "Kenel 2.6.19.2 stops booting at USB registration"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by Mipsel on 2007-01-26
Hello!

I just wanted to compile a 2.6.19.2 kernel so that I can get pommed working on my macbook (cor 2 duo). 

I am using edgy eft (i386)

I have downlaoded the src, than used the old config from the original edgy eft kernel and did a make oldconfig. Then created the deb packages with make-kpkg --initrd --revision 3 kernel_image kernel_headers 
Everything compiled and I installed the both packages and edited my /etc/lilo.conf:

boot=/dev/sda7
default=Ubuntu
map=/boot/map
delay=20

image=/boot/vmlinuz-2.6.19.2 initrd=/boot/initrd.img-2.6.19.2 
root=/dev/sda7
label=2.6.19

image=/boot/vmlinuz-2.6.17-10-generic initrd=/boot/initrd.img-2.6.17-10-generic 
root=/dev/sda7
label=Ubuntu
read-only

So then I rebooted to start the new kernel, but it just stops with this screen: [http://mipsel.dyndns.org/files/11698172641--CIMG1284.JPG](http://mipsel.dyndns.org/files/11698172641--CIMG1284.JPG)

I guess the problem has something to do that the kernel can't mount dev,sys,proc but where is the problem? The original kernel works without a problem.

Thanks for any hint!

Bye,
Mips

---

### Post by mustang on 2007-01-26
> **Mipsel said:**
> Hello!

I have downlaoded the src, than used the old config from the original edgy eft kernel and did a make oldconfig. Then created the deb packages with make-kpkg --initrd --revision 3 kernel_image kernel_headers 
Everything compiled and I installed the both packages and edited my /etc/lilo.conf:


That's interesting because I followed the same process and I did not run into any errors. Howvever, I have the first generation core duo macbook and I'm using grub (which probably doesn't matter in this case).

What you could try doing is using the .config file posted on the gentoo macbook wiki. This one is for 2.6.19.2

[https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.19/config](https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.19/config)

---

