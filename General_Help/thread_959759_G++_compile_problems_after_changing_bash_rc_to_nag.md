---
title: "G++ compile problems after changing bash rc to nag variant"
date: 2008-10-26
forum: General Help
---

### Post by SolStis451 on 2008-10-26
Hi, im new to these forums so not sure if this is under the right catagory.

Am undertaking a computational modeling module at university and am using ubuntu terminal to log on to the linux server from home.  In a recent example we have had to edit the bashrc to enable compilation with NAG routines.  

The following is typed in to the console to edit the bash and then to check a nag example...

- [...@...]$ cd
- [...@...]$ cp.bashrc bashrc_old
- [...@...]$ cp /tmp/nag/bashrc_phymat ~/.bashrc
- [...@...]$ source ~/.bashrc
- [...@...]$ nexample d01ajc

*terminal output from example *

- [...@...]$

Now the problem, after doing this, at a later date i went back to some of the previous written programes and tried to compile them using:

- [...@...]$ g++ *prog.out prog.cpp*

but am now getting the following error:

[jxf419@phymat2 compphys]$ g++ 4.out 4.cpp

4.out: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/../../../../lib64/crt1.o:(.text+0x0): first defined here
4.out: In function `_fini':
(.fini+0x0): multiple definition of `_fini'
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/../../../../lib64/crti.o:(.fini+0x0): first defined here
4.out:(.rodata+0x0): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/../../../../lib64/crt1.o:(.rodata.cst4+0x0): first defined here
4.out: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/../../../../lib64/crt1.o:(.data+0x0): first defined here
4.out:(.rodata+0x8): multiple definition of `__dso_handle'
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/crtbegin.o:(.rodata+0x0): first defined here
4.out: In function `_init':
(.init+0x0): multiple definition of `_init'
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/../../../../lib64/crti.o:(.init+0x0): first defined here
/tmp/ccs0C0XO.o: In function `main':
4.cpp:(.text+0x6c): multiple definition of `main'
4.out:(.text+0x144): first defined here
/usr/lib/gcc/x86_64-redhat-linux/4.1.2/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
4.out:(.dtors+0x8): first defined here
collect2: ld returned 1 exit status
[jxf419@phymat2 compphys]$ 

but before it worked fine.  I have tried reinstating the original bashrc from the copy saved at the beginning  (bashrc_old) but did not succeed and am still getting the same error!

Any assistance with this would be greatly appreciated.

Thanks

Sol

---

