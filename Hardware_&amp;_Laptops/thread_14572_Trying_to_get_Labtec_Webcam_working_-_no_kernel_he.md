---
title: "Trying to get Labtec Webcam working - no kernel headers?"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by Marquis_de_Carabas on 2005-02-08
I bought a Labtec Webcam the other day. Plug it in and the device manager lists it straight away. The vendor id is 0x46d and the product id is 0x921.

After a bit of searching it seems that [this](http://home.tiscali.dk/tomasgc/labtec/) is the driver I need, but trying to compile it results in the following error:

```
Building SPCA5XX driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/craig/My Downloads/spca532-04012005 modules
make: *** /lib/modules/2.6.8.1-4-686/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

As far as I can tell (and I've never done anything with kernel modules before, so I'm learning as I go) I need to install the kernel headers, but there don't appear to be any kernel headers available for 2.6.8 and installing the latest available headers - 2.6.7 - hasn't made any difference.

Can I get the 2.6.8 headers from somewhere? Do I need Ubuntu-specific headers or can I grab generic Debian ones?

I'd rather not go back to an older kernel version just to get the webcam working, but if that's the only way then I guess I will. But other methods will definitely be appreciated!


[Edit] After finding [this](http://ubuntuforums.org/archive/index.php/t-946.html) page in the archives, I tried searching Synaptic for "2.6.8.1-4" and immediately found the headers. D'oh! It does seem a little counter-intuitive though - searching for "kernel headers" gives 2.6.7 as the most recent version available, which leads one to assume that there are no 2.6.8 headers in the repos.

Anyway, it was all plain sailing after I found the headers - the driver's installed and the webcam's working perfectly.

---

