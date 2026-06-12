---
title: "Yet Another Lenovo Active Protection System Thread"
date: 2008-10-16
forum: Hardware
---

### Post by sdjcwcba on 2008-10-16
Hi,

I am currently following the advice at [http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS") to get it working on my X61 tablet with Ubuntu 8.04.1 (everything else works great!). 

My problem is that since I have 2.6.24 (which has some issues with the kernel patch) I am trying to use the Zen-Sources kernel.  

However the kernels don't seem to be .tar.bz2 but rather .patch.bz2 meaning the     ```
# tar jxf 2.6.27-rc7-zen3.patch.bz2 
```     just reports back with an error complaining about it not being a tar file. 

I therefore tried bunzip2 and tried extracting the patch to /usr/src/linux however /linux is a file, not a directory. Is there anyway to get around this? :(

Thanks a lot,
Joe

EDIT: UPDATE PLEASE SEE BELOW

---

### Post by sdjcwcba on 2008-10-17
I am not 100% sure on the bumping rules but for now...TTP :KS

---

### Post by sdjcwcba on 2008-10-17
A quick update:

I followed the instructions at [http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html]("http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html") and the the GNOME applet seems to be indicating that the hard drive is stopping correctly (any way to confirm this?)

Only problem is this new kernel has broken wireless/sound. Did I do something wrong or is this expected? Either way...anyway to fix it? :)

Thanks :KS

Joe

---

### Post by sdjcwcba on 2008-10-18
24 hour bump :)

---

