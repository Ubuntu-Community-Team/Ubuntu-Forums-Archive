---
title: "Custom Kernel and Ubuntu Repository Compatibility"
date: 2008-04-23
forum: Hardware
---

### Post by pzearfoss on 2008-04-23
After I installed 4GB of memory in my laptop, I discovered that the generic 32-bit kernel did not support CONFIG_HIGHMEM4G parameter when it was compiled.  So, I'm planning to make a custom build of the kernel with the high memory options enabled, so I can address all 4 gigs.  My question is whether this will cause compatibility issues with the updater and other repositories.  

(I don't think it will, but I don't wanna take any chances either).

Thanks!

---

### Post by Yellow Pasque on 2008-04-23
I rolled a custom kernel on my 64-bit machine because I wanted hardware monitoring and the module needed a 2.6.24 kernel. The only issue I ran into was Ubuntu modifying my grub menu whenever it installed an update to the old kernel (which I kept for backup purposes).

Overall, I was very pleased with the result. The custom kernel was relatively smaller than the Ubuntu stock kernel (because I removed all unnecessary hardware drivers) and it used significantly less CPU.

What guide are you following?

---

### Post by pzearfoss on 2008-04-24
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

That's the doc I used.  I compiled it ok, but I still haven't solved my 4GB memory problem.

---

### Post by Yellow Pasque on 2008-04-24
I'm assuming you've looked for hardware memory mapping options in your BIOS. If so, I'd recommend "upgrading" to a 64-bit install if you really feel you'll need 4GB of RAM.

Let me know if you're interested and we'll get your thread moved to the x86-64 forum and help you through it. The process isn't too painful if you have a backup of your personal data (hopefully, everything you need is in your home folder). You can even resize your partitions and have both 32 and 64 bit Ubuntu's on your disk if you're not ready to do a full upgrade.

---

### Post by pzearfoss on 2008-04-24
Feel free to move the post to wherever is best, I'm really in a bind, having done everything I can think of so far.  

Unfortunately, 64-bit isn't an option.  The processor is a Core Duo, not core 2, so the 64 bit processing is disabled.  I looked thru my bios for the memory mapping, I didn't find the option for it (toshiba laptop).  The processor has the PAE flag set in /proc/cpuinfo, which leads me to believe that the machine should be capable of using 36 bit addressing instead of 32.

---

### Post by pzearfoss on 2008-04-24
An additional note.  

Since it's a laptop the graphics memory is shared, so I realize I won't get the full 4G for system use.  I'd be happy at this point with 3.5 (the graphics shouldn't eat more than 128M).  

The laptop model is Toshiba Satellite A105-s4284.  Bios rev 6.0.

---

