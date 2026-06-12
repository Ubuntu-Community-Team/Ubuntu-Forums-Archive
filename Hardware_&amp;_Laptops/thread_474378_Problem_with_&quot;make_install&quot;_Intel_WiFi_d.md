---
title: "Problem with &quot;make install&quot; Intel WiFi driver"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by PositronLaser on 2007-06-15
When I try installing intel wifi driver and type "make install," I get this error message:
> root@Flanker:~/Desktop/iwlwifi-0.0.30# make install
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'.  Stop.
When I do what it suggests (typing 'make=SHELL=/bin/bash'), I get this error message:
> Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source'
make: *** [compatible/kversion] Error 1

Could somebody explain to me what this means and what I should do to fix it?
Thanks,

---

### Post by aquavitae on 2007-06-15
Why are you trying to compile the drivers - can't you get them on synaptic?

If you do need to compile from source: did you run ./configure first?

---

### Post by PositronLaser on 2007-06-15
I did run ./configure first but it did not work.

---

### Post by lamadredelsapo on 2007-06-15
What does "I did run ./configure first but it did not work." mean? Post output please.

---

### Post by PositronLaser on 2007-06-15
Here is what it says when I type ./configure
> bash: ./configure: No such file or directory
The iwlwifi does not have any configure script.

---

### Post by PositronLaser on 2007-06-15
Bump

---

### Post by Ptero-4 on 2007-06-15
First ensure to get build-essential (it`s on your ubuntu CD) using:
```
sudo aptitude install build-essential
```
And then if ./configure still doesn`t work type ./autogen.sh instead.

---

### Post by PositronLaser on 2007-06-15
I already install build-essential when installing NVIDIA driver.
When I try ./autogen.sh, I get this:
> bash: ./autogen.sh: No such file or directory
I think the clue is in "Kernel makefile not found". I try installing kernel-source, kernel-devel and kernel-dev but they are not available.

---

### Post by Bachstelze on 2007-06-15
```
sudo dpkg-reconfigure dash
```

It will ask if you want to use Dash, say **no**. Then logout, log back in and try again.

---

### Post by PositronLaser on 2007-06-15
I tried it but it gives me the same error "Kernel Makefile not found"

---

### Post by PositronLaser on 2007-06-15
Bump

---

### Post by PositronLaser on 2007-06-15
Bump

---

### Post by jhauris on 2007-06-16
Hello!

First off, Positron, it's considered pretty obnoxious to bump a post every hour, and sometimes people will refuse to help you based on such behavior. I know it's frustrating to not be able to get something working, but sometimes a little patience can go a long way.

That being said, I am writing this from Feisty using the iwl4965 driver from intel. What I ended up doing was downloading the kernel sources from kernel.org (click the F to get the full sources). I then downloaded the mac80211 patch from the intel site (intellinuxwireless.org), along with the latest iwl driver (one was released friday, 6/15).

I compiled the vanilla sources ("make menuconfig", then "make-kpg --initrd --append-to-version=-something kernel_image kernel_headers"). I created the firmware directory (I don't know why I had to do this, maybe I built the package incorrectly?): mkdir /lib/firmware/2.6.21.5-something. Then I installed the new kernel (dpkg -i linux-image-2.6.21.5-something<tab>, repeat for linux-headers).

I booted into the new kernel, an then unpacked the mac80211 tar, ran make, then make patch_kernel. I booted into the old kernel, removed the new kernel I had built, ran 'rm -r /lib/modules/2.6.21.5-something' and reran make menuconfig on the source. I selected the new mac80211 to be built as a module, and set the old mac80211 to not be built. To do this, you have to clear the other things that depend on that first, I just cleared all the wireless stuff from devices->networking, I think.

I booted into the new kernel, unpacked the iwlwifi tar, and ran make, then make install, then ./load, and I was good to go.

The reason I did all this was because I believe that the mac80211 module in the ubuntu kernel is old/not the right one. I tried to patch the ubuntu sources, but had no luck, so I thought I'd just upgrade to the latest kernel anyway. Everything else works fantastically, except the display issues. 


Problems:
For some reason, I'm having some weird display issues; after running make install, I have display issues: I can't go to virtual terminals (ctrl-alt-F1), and the boot splash gets corrupted. I think it's a resolution issue, but I don't know why it's happening. I changed the Makefile for iwlwifi from depmod -A to -a, but it still happens. I'm still debugging. It would be nice if we could get an Ubuntu package for this driver.

If anyone has a solution to this, or any corrections to the above, I'd be most appreciative.

-Jon

---

### Post by PositronLaser on 2007-06-16
Thanks, I will try it right now. Thanks for your help.

---

### Post by 7echno7im on 2007-06-26
After you run ./configure, does it complete successfully?  Are there dependencies missing to complete the ./configure?  For instance I was just compiliing a make for BASE.  I am so use to running on to the next step I didn't realize that it said it needed flex to continue.  I could not *make* because i needed flex.   Run ./configure again, what are the last few lines it say?  Missing dependencies?

---

### Post by Loranga on 2008-03-23
There is no ./configure to run, and the documentation says that it should be just to cd into iwlwifi-1.2.25 and run make (as a normal user). I get the problem already at "make", (have of course not tried "make install")

I have installed the full kernel source (if i chose the correct package), but still the same problems.

This with iwlwifi-1.2.25

---

### Post by octoberdan on 2008-04-05
Perhaps this will assist you? [http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)

---

### Post by crabpot8 on 2008-06-07
Thanks to octoberdan above, I was having similar problem and ran this in terminal right before I ran make - cleared up the exact error that Positron was having:


sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/source
make

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Checking kernel compatibility in:
	/lib/modules/2.6.24-18-generic/source//
grep: /lib/modules/2.6.24-18-generic/source//drivers/base/core.c: No such file or directory
grep: /lib/modules/2.6.24-18-generic/source//fs/debugfs/inode.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires device_rename compat
   - Requires debugfs_rename() compat
Building compatibility version in 'compatible/' directory:
Copying compatible/ from modified/...done
 + Applying: patches/debugfs_rename.patch
	diff -urp origin/net/mac80211/debugfs_netdev.c new/net/mac80211/debugfs_netdev.c
:guitar:

---

