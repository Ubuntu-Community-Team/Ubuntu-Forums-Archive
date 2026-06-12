---
title: "Installing wireless drivers problem :("
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by markomk on 2008-12-09
hi, i just found drivers for wireless card, i need some help to install the drivers :( i try but i have a problem :S i use ubuntu few months pls help
btw my kerlen version is 2.6.24-22-generic
--------------------------------------------------------------
INSTALLATION INFO
On the target machine, setup the source/hybrid/build directory

1.  Create a new directory:                 mkdir hybrid_wl
2.  Go to that directory:                   cd hybrid_wl
3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                             tar -xzf <path>/hybrid-portsrc.tar.gz
        64 bit:                             tar -xzf <path>/hybrid-portsrc-x86_64.tar.gz

After untar'ing you should have a src and lib sub directory plus a Linux
2.6 "kbuild" external makefile (Makefile).   The lib sub directory has the pre-built
binary, wlc_hybrid.o_shipped.  

You use the standard Linux 2.6 kernel build system as follows to make a Linux loadable
kernel module (LKM):
------------------------------------------------

tar -xzf <path>/hybrid-portsrc.tar.gz --------path from where?
---------------------------------------------------------

On the target machine, and cd'ed to the directory that contains the Makefile (fragment)

4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

You should now have a LKM, wl.ko inside this directory.
-----------------------------
in lib\modules are 2 kernels :S
2.6.24-19-generic and 2.6.24-22-generic
when i type uname -r command it say 2.6.24-22-generic

----------------------------


On this or a machine with the same kernel version, install the driver.

1.  Validate you don't have loaded (or built into the kernel) the Linux community provided
      driver for Broadcom hardware.  This exists in two forms: either "bcm43xx" or a split form
      of "b43" plus "b43legacy".  If these modules were loaded you would either
        a) rmmod bcm43xx or
        b) rmmod b43; rmmod b43legacy
2.  Make available 802.11 TKIP crypto module:      modprobe ieee80211_crypt_tkip
3.  Insert the Broadcom wl module:                 insmod <path>/wl.ko
-------------------------------
on rmmod bcm4312 command:

rmmod BCM4312
ERROR: Module BCM4312 does not exist in /proc/modules

--
Network controller: Broadcom Corporation BCM4312 802.11b/g
--

---

### Post by Mark Phelps on 2008-12-10
If you browse the Networking subforum, you'll find lots of threads about the Broadcom 4312 and specific steps you need to take to get it to work.

As to your "path" question, the  "path" is the full top-down directory sequence, starting from "/" (root) to the directory containing the file.

So, if you expanded the file into /home/markomk/packages/XXXX
 the tar command would be:

tar -xzf /home/markomk/packages/XXXX/hybrid-portsrc.tar.gz

---

