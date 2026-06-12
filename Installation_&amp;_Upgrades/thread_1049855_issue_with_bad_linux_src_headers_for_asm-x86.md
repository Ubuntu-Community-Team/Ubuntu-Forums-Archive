---
title: "issue with ?bad? linux src headers for asm-x86?"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by omnialive on 2009-01-25
I run a VMWare virtual machine on my Ubuntu box (only way I like to deal with Windows when I need). It had been working fine then my VM started giving me BSOD (shocker!) and I was having some reading timeouts from my DVD-RW drive.

So, I upgraded to 8.10. Everything looked good. Obviously, with the new kernel, I have to "reconfigure" the VMPlayer, which means building certain core components based off of the current kernel.

To get to the point, the build fails rather quickly when it says it cannot find the asm/semaphore.h file. I investigate and they are right! There is not file or link there! I find that the file in the "asm" directory is supposed to be a link to a file under "/usr/src/linux-headers-2.6.27-9/include/asm-x86" called semaphore.h. The only problem is that when I go to confirm that the file is there, this is what I find when I do an "ls -l semaphore.h":

/usr/src/linux-headers-2.6.27-9/include/asm-x86$ ls -l semaphore.h 
lrwxrwxrwx 1 root root 11 2009-01-24 23:57 semaphore.h -> semaphore.h

Anyone run into this problem? I am burnt until I can get a good copy of semaphore.h for asm-x86. I humbly lay myself prostrate at your knowing Ubuntu feet! ](*,)

---

### Post by jbro on 2009-01-25
I had this same problem when trying to build a kernel driver for my webcam. It seems that the kernel headers changed between 2.6.24 and 2.6.27. Apparently, not everyone has updated their software for kernel 2.6.27. You might try downgrading your kernel to 2.6.24 until vendors update their stuff for the new headers.

Regards,
Jay

---

### Post by omnialive on 2009-01-25
I'll try downgrading and see where that gets me. Thanks!

---

