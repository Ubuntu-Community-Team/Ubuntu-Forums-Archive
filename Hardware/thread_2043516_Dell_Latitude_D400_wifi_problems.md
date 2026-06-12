---
title: "Dell Latitude D400 wifi problems"
date: 2012-08-16
forum: Hardware
---

### Post by joco1500 on 2012-08-16
Hello.

I have a dell latitude d400 and it had windows xp on it, i hated it.

i tried to install 12.04 and the proseser isn't compatible,

then i went down to 6.04 because i had that on a usb already.
it worked but the wifi dident connect.

then i went to 9.something and the wifi still dident work.

could someone please give me a "buntu that will work out of the box without any configuration. 

but anything will help.

---

### Post by ahallubuntu on 2012-08-16
I highly suggest you stick with the newer, supported versions of Ubuntu.  Ubuntu 10.04 LTS should work well for this laptop, but you need to get the 32 bit version.  12.04 LTS should work as well - just get the 32 bit version, not the 64 bit version.  I have installed Ubuntu 12.04 on older CPUs than the one in your Dell laptop.

---

### Post by Tobeus on 2012-08-17
There is one limitation of some older laptops that I have run into myself with the newer versions of Ubuntu.  I don't remember when the change was made, but the newer versions require PAE or Physical Address Extension, which allows the 32-bit processors to address more than 4GB of ram.  My old sony wouldn't take the 12.04 image because it did not have PAE capabilities.

Just ignore me if you are not having this issue, but if you are receiving something along the lines of:

```

This kernel requires the following features not present on the CPU:
pae

Unable to boot - please use a kernel appropriate for your CPU.

```Try installing lubuntu or xubuntu, because they default to the non-PAE kernel.  Even if you are not having this specific error, you could still try those two versions.  They are built more for the older systems anyway, providing more lightweight interfaces and whatnot.

Reference:  [http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p](http://askubuntu.com/questions/117744/how-can-i-install-12-04-on-a-non-pae-cpu-error-kernel-requires-features-not-p)

Good luck!

-Tobeus

---

