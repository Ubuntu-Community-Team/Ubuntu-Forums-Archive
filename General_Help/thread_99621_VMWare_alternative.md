---
title: "VMWare alternative"
date: 2005-12-05
forum: General Help
---

### Post by detyabozhye on 2005-12-05
I need a good free alternative to VMWare. Anybody know any good ones?

---

### Post by Chickenmonger on 2005-12-05
In order of VMWare-likeness:

qemu: [http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)
bochs: [http://bochs.sourceforge.net/](http://bochs.sourceforge.net/)
user mode linux: [http://user-mode-linux.sourceforge.net/](http://user-mode-linux.sourceforge.net/)
wine: [http://www.winehq.com/](http://www.winehq.com/)

There are others that can achieve some level of other-OS compatibility, but I can't think of them offhand.

---

### Post by cilynx on 2005-12-05
Don't forget Xen: [http://www.cl.cam.ac.uk/Research/SRG/netos/xen/](http://www.cl.cam.ac.uk/Research/SRG/netos/xen/)

At the moment, it won't run Windows, but it's good for making a virtual army of Linux boxen.

---

### Post by -DarkMind- on 2005-12-05
qemu may be..

but vmware is the faster (and easier ;) )

---

### Post by detyabozhye on 2005-12-05
Can anyone give me some info on qemu vs bochs? Will they run XP? I have programs unsupported by WINE and CrossOver, so I need something that'll run XP, cuz that's the only Windoze I have left.

---

### Post by detyabozhye on 2005-12-05
[QUOTE=-DarkMind-]qemu may be..

but vmware is the faster (and easier ;) )[/QUOTE]
As in, performance or setup?

---

### Post by -DarkMind- on 2005-12-05
[QUOTE=detyabozhye]As in, performance or setup?[/QUOTE]

in setup is fast why vmware is easy create virtual machines (all with clicks and wizards xD )

qemu is command line only...

i test qemu (with kqemu accelerator module) and vmware in performance...
vmware is a much faster than qemu... try to open photoshop in vmware and then in qemu ... :)


and now appear vmware 5.5 :D i download the trial (i not found a serial :oops: ) but works very good






pd: i not speak english very well :oops:

---

### Post by detyabozhye on 2005-12-05
What about bochs? How fast is that one? And will it run XP?

---

### Post by -DarkMind- on 2005-12-05
faster to slower

1. vmware (proprietary)

2. Qemu with kqemu module (qemu open-source, kqemu module is not opendource)

3. Qemu (open-source)

4.- Bochs (open-source)


the best way to verify this is trying (or reading google xD )


:)

---

### Post by detyabozhye on 2005-12-05
K, thanks, I'll try Qemu then, I went and did read a little about Qemu vs Bochs on Google. :)

---

### Post by detyabozhye on 2005-12-06
Um, I checked out the instructions on Qemu and VMWare, and I think dual-booting is a faster choice for now (meaning setup).

---

### Post by risknet on 2005-12-06
Also, try to use Parallels Workstaton beta 4.
This is a virtualizer just like VMWare not an emulator.

Althought this is a commercial product, this will cost a lot less than VMWare.

I am using it for using Windows 2000 sp4 as a guest os on my Linux box, and it is really good in terms of performance.

You can get a beta 4 for 30 day trial from [www.parallels.com](www.parallels.com)

= risknet =

---

### Post by detyabozhye on 2005-12-06
Can I install Windoze on it as I would on a regular comp instead of making images and stuff? I could play around with making images and all that if only I had the time. If I can make it work the way I would on a real PC, I would probably try it then.

---

### Post by ned.b on 2005-12-06
Xen 3.0 

[http://www.xensource.com/](http://www.xensource.com/)

looks interesting

Ned

---

### Post by Griffin3 on 2005-12-06
risknet: I looked all over the parallels.com site, and could not find any pricing information, other than a notice that if you fill out a full feedback form, you get 10% off. Where did you get the information about the price being lower than VMWare? And, do you happen to know what that price may be?

---

### Post by pheitman on 2005-12-06
Of course now the VMWare VMPlayer is free. You can install WinXP on it assuming that you have a license for XP and you use the hacks that are documented to boot from a CD and install on top of an existing image...

---

### Post by risknet on 2005-12-06
Hi Grinffin3,

I have never heard of this Parallels Workstation before until I read an article of it from Linux Format UK magazine.   I am not sure if this price is a targeted price for the final release version, but I found the price info from [http://www.hotscripts.com/Detailed/54315.html](http://www.hotscripts.com/Detailed/54315.html).

99 USD is still a good value for this kind of real virtualizer product.   You can get 10% off if you submit some feedbacks from your experience.  
I have been using it for 3 weeks now with 2 months trial license, and I am pretty happy with its performance.   Their technical support is very good too. 

I am running Windows 2000 sp4 in Parallels workstation on Ubuntu 5.10 in HP pavilion ze4610us laptop (704mb ram).  I use Win2k for MS Money 2003 pro and Cisco VPN client for my corporate server connection.

---

### Post by foxiness on 2005-12-21
ded from /usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:28:
/usr/lib/Parallels/Drivers/Hypervisor/hypervisor.h:28:25: error: ./linux/slab.h: Too many levels of symbolic links
In file included from /usr/lib/Parallels/Drivers/Hypervisor/hypervisor.h:36,
                 from /usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:28:
/usr/lib/Parallels/Drivers/Hypervisor/hypvmstate.h:69: error: field &#8216;list&#8217; has incomplete type
In file included from /usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:28:
/usr/lib/Parallels/Drivers/Hypervisor/hypervisor.h:125: error: syntax error before &#8216;kmem_cache_t&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypervisor.h:125: warning: no semicolon at end of struct or union
/usr/lib/Parallels/Drivers/Hypervisor/hypervisor.h:136: error: syntax error before &#8216;}&#8217; token
/usr/lib/Parallels/Drivers/Hypervisor/hypervisor.h:136: warning: empty declaration
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:34: error: syntax error before &#8216;appLock&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:34: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;appLock&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:34: error: &#8216;SPIN_LOCK_UNLOCKED&#8217; undeclared here (not in a function)
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:34: warning: data definition has no type or storage class
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: In function &#8216;appIncCounter&#8217;:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:50: warning: implicit declaration of function &#8216;spin_lock&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:54: warning: implicit declaration of function &#8216;spin_unlock&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: In function &#8216;appDecCounter&#8217;:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:65: warning: implicit declaration of function &#8216;BUG&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: In function &#8216;init_module&#8217;:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:74: error: invalid use of undefined type &#8216;struct hypervisor_state_t&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:75: error: invalid use of undefined type &#8216;struct hypervisor_state_t&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:76: error: invalid use of undefined type &#8216;struct hypervisor_state_t&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:77: error: invalid use of undefined type &#8216;struct hypervisor_state_t&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:80: warning: implicit declaration of function &#8216;kmalloc&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:80: error: &#8216;GFP_KERNEL&#8217; undeclared (first use in this function)
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:83: warning: implicit declaration of function &#8216;memset&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: In function &#8216;cleanup_module&#8217;:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:126: warning: implicit declaration of function &#8216;kfree&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: At top level:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:132: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:132: warning: parameter names (without types) in function declaration
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:132: warning: data definition has no type or storage class
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:133: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:133: warning: parameter names (without types) in function declaration
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:133: warning: data definition has no type or storage class
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:134: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:134: warning: parameter names (without types) in function declaration
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:134: warning: data definition has no type or storage class
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: In function &#8216;hyper_wrap_smp_processor_id&#8217;:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:138: warning: implicit declaration of function &#8216;smp_processor_id&#8217;
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c: In function &#8216;hyper_wrap_page_to_pfn&#8217;:
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:142: error: &#8216;mem_map&#8217; undeclared (first use in this function)
/usr/lib/Parallels/Drivers/Hypervisor/hypmain.c:143: warning: control reaches end of non-void function
make[4]: *** [/usr/lib/Parallels/Drivers/Hypervisor/hypmain.o] Error 1
make[3]: *** [_module_/usr/lib/Parallels/Drivers/Hypervisor] Error 2
make[3]: Leaving directory `/usr/src/linux-source-2.6.12'
make[2]: *** [hypervisor] Error 2
make[2]: Leaving directory `/usr/lib/Parallels/Drivers/Hypervisor'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/lib/Parallels/Drivers'
make: *** [all-recursive] Error 1

[/CODE]

this after apear after this command, Parallels-config

Parallels-2.0.1514-Lin.deb

---

