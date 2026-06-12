---
title: "Old Laptop, Would Ubuntu Work?"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by Taino on 2005-05-27
.

---

### Post by 23meg on 2005-05-27
i'm afraid the installer requires at least 32mb of ram, thus you don't have much chance with this config.

---

### Post by Taino on 2005-05-27
.

---

### Post by 23meg on 2005-05-27
sure, you can. people are running linux on things as varied as ipods, cellphones and pocket computers.. also do a google search for "damn small linux" and see if it suits your needs.

---

### Post by fastluck on 2005-05-29
[QUOTE=Taino]
Its a Toshiba Satellite Pro 440CS model
has a P75mhz Cpu
24mb Ram
800mb Harddisk
And has a CD Rom drive.
[/QUOTE]

It would run just about any of the large distros.  The 24 MB Ram you quoted is barely enough to guarantee you a fairly clean install.  Will it boot from CD?

If it were mine, I'd go with Debian.  I'm not sure if Sarge has a 486 distro--it probably does.  If it does and you can connect it to the internet, that would be the easiest way to go.  Then you can use apt-get to install just what you need to keep it small.  I'd give it a 128MB swap disk, that leaves you just under 600 MB for system+data.  Once you get everything installed, make sure to strip the debugging information for all the binaries to free up as much space as possible.

Also, instead of installing gcc-utils, go with busybox.  Much smaller and includes just about everything you'll need.

Or, go to linux.org and search for minimalist floppy-based 486 systems.  When you have one installed, get the book "Linux from Scratch" (or print it out from online) and build your system from the ground up. 

But what you're looking to do is going to take you awhile...There's no modern distro I'm aware of that will give you a turnkey system.

Fastluck

---

### Post by GOwin on 2005-05-30
I suggest you try feather linux.

Too bad Ubuntu can't run on it.

---

### Post by Zonkle on 2005-11-22
There are small linux such as Puppy: [http://www.goosee.com/puppy/](http://www.goosee.com/puppy/)
And damn small linux: [http://damnsmalllinux.org](http://damnsmalllinux.org)

Tell us what happens :)

Cya ;)

---

