---
title: "remove old kernels"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by orange-wedge on 2009-10-22
So after a handful of kernel upgrades with 9.04, my boot partition has gotten pretty full.

Here's a pretty long one-liner to remove the old kernels:
```
 r=`uname -r`; for i in `aptitude search linux | grep linux-image-.*-generic | grep -v $r | awk '{print $2}'`; do apt-get remove $i; done

```

The "grep $r -v" will prevent you from removing your current kernel, but still be very careful with this command.

---

### Post by earthpigg on 2009-10-22
you would probably want to either run this command from a root terminal, or try throwing 'sudo' in there.

this will give you a root terminal, from which the above command can be run as-is:
```

sudo su
```

be super duper careful when doing anything in a root terminal.

in fact, if you cannot dissect the above command and put it together understanding every part of it, my personal advice would be not to use it and to instead just search synaptic for 'kernel' and/or 'linux' and be sure not to remove the kernel that the command 'uname -a' gives you as the currently used kernel.

but, to each his own - choice is what Ubuntu is all about :D

either way you do it, after you remove the kernel you 'should' edit /boot/grub/menu.lst to remove the entries pointing to the old kernels that you have removed.



if all this is greek to you and you aren't really hurting for space on your / partition, then just leave it be. having multiple kernels installed isn't going to slow down your system any, and since there is a chance that a certain piece of hardware will work on an older kernel but not on the latest and greatest one (see: [http://en.wikipedia.org/wiki/Software_regression](http://en.wikipedia.org/wiki/Software_regression) ), it is generally a good idea to keep 2 or 3 kernels installed in my humble opinion.

---

### Post by orange-wedge on 2009-10-22
you aren't talking greek.  i'm the author of the line.  :)

in my searching for a solution, i decided to post the method i determined to work.  since we are approaching 9.10 i thought it might be nice to clean-up the systems i maintain.

well that's the beauty of this one-liner, it runs the remove with "apt-get" so that it removes the kernel entries from menu.lst

---

