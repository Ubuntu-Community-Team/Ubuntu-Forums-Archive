---
title: "Zen-Sources Kernel"
date: 2008-11-11
forum: General Help
---

### Post by sdjcwcba on 2008-11-11
Hello!

I am currently trying to get HDAPS (i.e actually disk parking) working on my X61 tablet. 

Since I can't wait any longer for 2.6.28 :) I imagine the best course would be to install a [www.zen-sources.org]("www.zen-sources.org") kernel. 

After I have downloaded the 2.6.28rc4 kernel (patch?) from that website -> I come to the end of my Linux knowledge :KS

I would be trying this with a Intrepid install (so kernel 2.6.27x I guess).

Any tips? :)

Thanks a lot,
Joe

---

### Post by sdjcwcba on 2008-11-12
Mini bump!

---

### Post by sdjcwcba on 2008-11-13
major bumpage

---

### Post by Tilgovi on 2008-11-14
Here is a quick rough guide to building the zen kernel.
These are the steps I followed, which was a discovery process. If anyone sees any problem or a better work flow please enlighten.

However, as of the last time I rebuilt this the disk protection patches seemed to have been removed. Since disk protection is coming in 2.6.28 the zen sources don't apply that as a separate patch anymore. I haven't actually gotten the new interface in 2.6.28 working, but maybe it's already possible. Please post if you do this!

Also, as of the time I wrote this I'm unable to access the zen-sources.org domain. It seems to not be responding, which makes me sad because I'm having troubles with the Intrepid kernel I just upgraded to.

From a terminal, do roughly the following:

1. Make sure you have git installed
```
sudo aptitude install git-core
```

2. Clone the zen sources repository
First, cd to the directory where you want to check out the source. Then
```
git clone git://zen-sources.org/zen/kernel/zen.git zen-sources
```

3. cd into the directory you repository you just cloned and check out the desired tag. For example: v2.6.28-rc3-zen1 (make sure to check out a -zen(n) tag).
```
git checkout -b local-v2.6.28-rc3-zen1 v2.6.28-rc3-zen1
```

4. follow the steps in the "Tool's you'll need" of the Ubuntu wiki Kernel/Compile page to get kernel build tools
[https://help.ubuntu.com/community/Kernel/Compile#Tools%20you%27ll%20need](https://help.ubuntu.com/community/Kernel/Compile#Tools%20you%27ll%20need)

5. copy the configuration of the ubuntu kernel as a starting point
```
cp /boot/config-`uname -r` .
```

now do ```
make oldconfig
``` to be prompted about the new features the zen patches introduce or just do ```
make config
``` and explore yourself. I recommend the former and then the latter.

6. This is optional. If you have more than 1 processor or core you can compile the kernel in parallel by doing this
```
export CONCURRENCY_LEVEL=3
```
The recommended number for CONCURRENCY_LEVEL is 1 + the number of cores you have.

7. Finally, build the packages.
```
fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```

If all goes well the .deb files should be in the parent directory where you checked out the sources. They can be installed with the command
```
sudo dpkg -i linux-image-2.6.28-rc3-zen1
``` and similarly for the headers file.

Good luck!

-Randall

---

