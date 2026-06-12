---
title: "Reverting to Older Kernel"
date: 2008-08-28
forum: General Help
---

### Post by Unanimated on 2008-08-28
I just had a quick question on reverting to an old kernel. I have -21-generic, and I want -19-generic, but I can't figure out how to do that. Is there a way to do it without formatting my hard drive again?

---

### Post by Crafty Kisses on 2008-08-28
What's exactly the problem, hardware issue or you simply just want a older kernel?

Heres a quick crash course on how to compile a kernel 
```

wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.7.tar.gz
sudo tar jxvf -C /usr/src/linux-2.6.15.7 linux-2.6.15.7.tar.bz2
sudo ln -s /usr/src/linux-2.6.15.7 /usr/src/linux
```Now's the time to patch it if needed and then 
```

cd /usr/src
sudo make menuconfig
sudo make clean && sudo make && sudo make modules_install
sudo mount /boot && sudo make install
sudo module-rebuild rebuild
```Make sure you have your /boot partition mounted
Heres a howto [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

But remember whatever your trying to do, you maybe able to do all those things that you want but I'm scared that you might get undesirable results from getting a kernel from an older version of Ubuntu. Also when you finish compilling the kernel, make sure you link /usr/src/linux back to the latest kernel, otherwise you won't get video driver support and things like that with the new kernel.

---

### Post by Unanimated on 2008-08-28
Well, I'm trying to install VirtualBox, but it can't find the sources for -21-generic, and there are some hardware issues as well. I think it would be easier to downgrade to -19-generic.

---

