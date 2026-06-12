---
title: "Custom Kernel Issues for Aspire One"
date: 2009-01-27
forum: Hardware
---

### Post by SeanCly10 on 2009-01-27
I just installed the full version of Linux4One on my Aspire One, which included a custom kernel (Linux4One is simply a an install of Hardy, with tweaks specifically for the Aspire One netbook). The install seemed to go fine, but in the process of trying to get the wireless back up and running again, I ran into a new problem, and it's a doozy.

I was trying to compile the install file for madwifi, and I kept getting an error referring to 'makefile_32':

```
make[2]: Entering directory '/usr/src/linux-headers-2.6.28-v15aspire1' /usr/src/linux-headers-2.6.28-v15aspire1/arch/x86/Makefile:41: /usr/src/linux-headers-2.6.28-v15aspire1/arch/x86/Makefile_32.cpu: No such file or directory
```

I have since discovered that this error comes back whenever I try to 'make' anything. Several Google searches, as well as searches on the L41 boards and these, have turned up a few things, but nothing that I can fully understand.

I'd like to be able to keep this custom kernel and fix this error, but I understand that may not be possible. Can someone smarter than me give me a hand figuring this out?

---

### Post by bedenation on 2009-02-05
Encountered the same problem.  It appears to be related to a faulty install script.

While setting up "linux-headers-2.6.27onev6aspire1", install reports the following error "sudo: please use single character options" (skips this step and continues with the install).  

However when you perform the install **with the Aspire wired to the Internet**, and immediately after the reboot, complete the install by downloading and processing the tar.bz2 upgrade file available at 

[http://www.linux4one.it/forum/index.php?topic=307.0](http://www.linux4one.it/forum/index.php?topic=307.0)

Once you have completed this last step, all peripherals (incl. Wireless) should work out of the box !  No need to compile wireless network driver.

---

### Post by pjalegria on 2009-02-05
Have a look at this site...

[http://www.ug.it.usyd.edu.au/~scole/](http://www.ug.it.usyd.edu.au/~scole/)

---

