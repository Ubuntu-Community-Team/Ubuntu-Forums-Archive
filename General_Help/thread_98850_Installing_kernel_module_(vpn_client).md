---
title: "Installing kernel module (vpn client)"
date: 2005-12-04
forum: General Help
---

### Post by mherring on 2005-12-04
I'm trying to install a Cisco vpn client on 5.10---this client wants to build a kernel module and thus the kernel source is required.

Using Synaptic, I installed the full kernel source to match my kernel (2.6.12-10)

On the first attempt, the installer complained about not being able to find gcc-3.4.  I have solved similar issues by simply installing the appropriate compiler.  (5.10 comes with gcc-4 and I have also installed 3.3)

After installing gcc-3.4 (Using Synaptic), the vpn installer issues extensive complaints about not being able to find header files in the kernel source directory.  Many of these are actually there, which leads me to believe that this particular setup winds up looking in the wrong path.

Assuming that my vpn installer actually needs gcc-3.4, then would I expect that version to also work with the kernel source files.  Alternatively, is it possible that I should just link to gcc-4?

(This vpn installer worked fine on 5.04)

---

### Post by schdefan on 2005-12-04
after installing the kernel-source you need to run make in /usr/src/linux
to build dependencies for a few seconds. Then you can abort with strg c

you should be able to compile the kernel module now.
schdefan

---

### Post by mherring on 2005-12-04
Interesting-----

Tried this and it did not work---it starts out and cannot find many of the **.h files

Here's the beginning of the complaining----a quick check shows that at least some of the files ARE there---in */include/linux.  Further clue:  I cannot find a directory named "sys" anywhere in the */src/linux directory or subs.

???
<<output of attempt to run make>>
mherring@Ath:~$ su
Password:
root@Ath:/home/mherring# cd /usr/src/linux
root@Ath:/usr/src/linux# make
Makefile:485: .config: No such file or directory
  CHK     include/linux/version.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/3.4.5/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/3.4.5/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/limits.h:122:61: limits.h: No such file or directory
<<snipped>>

---

### Post by schdefan on 2005-12-04
oh sorry forgot the .config file.
You will find the config file to your kernel in /boot
In my case it is /boot/config-2.6.12-9-386
copy the config file to /usr/src/linux with
> sudo cp /boot/config-$(uname -r) /usr/src/linux/config
Then run make in /usr/src/linux for a few seconds again.

schdefan

---

### Post by williamx on 2005-12-05
I have the exact same problem.. Have installed new source and linux-headers, and have copied the .config file and tried to make the kernel for a few secs.

But when I try to install the VPN, this comes out:

Making module
make -C /lib/modules/2.6.12-10-powerpc/build SUBDIRS=/home/william/install/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-powerpc'
  CC [M]  /home/william/install/vpnclient/linuxcniapi.o
In file included from /home/william/install/vpnclient/linuxcniapi.c:30:
/home/william/install/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:429: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:437: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:446: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:452: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:459: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:462: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:465: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:472: warning: `regparm' attribute directive ignored
In file included from /home/william/install/vpnclient/linuxcniapi.c:31:
/home/william/install/vpnclient/unixcniapi.h:38: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/unixcniapi.h:39: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:43: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:55: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:97: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:134: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:194: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:233: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:291: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:403: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:504: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/linuxcniapi.c:543: warning: `regparm' attribute directive ignored
  CC [M]  /home/william/install/vpnclient/frag.o
In file included from /home/william/install/vpnclient/frag.c:16:
/home/william/install/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:429: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:437: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:446: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:452: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:459: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:462: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:465: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:472: warning: `regparm' attribute directive ignored
  CC [M]  /home/william/install/vpnclient/IPSecDrvOS_linux.o
In file included from /home/william/install/vpnclient/IPSecDrvOS_linux.c:21:
/home/william/install/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:429: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:437: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:446: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:452: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:459: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:462: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:465: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:472: warning: `regparm' attribute directive ignored
In file included from /home/william/install/vpnclient/IPSecDrvOS_linux.c:22:
/home/william/install/vpnclient/IPSecDrvOSFunctions.h:64: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOSFunctions.h:65: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOSFunctions.h:74: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOSFunctions.h:75: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOSFunctions.h:76: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOSFunctions.h:77: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOS_linux.c:39: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOS_linux.c:57: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOS_linux.c:133: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOS_linux.c:166: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOS_linux.c:191: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/IPSecDrvOS_linux.c:231: warning: `regparm' attribute directive ignored
  CC [M]  /home/william/install/vpnclient/interceptor.o
In file included from /home/william/install/vpnclient/interceptor.c:33:
/home/william/install/vpnclient/Cniapi.h:220: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:225: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:233: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:238: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:245: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:249: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:334: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:338: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:341: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:347: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:351: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:357: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:364: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:371: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:375: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:380: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:386: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:390: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:395: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:400: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:404: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:408: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:413: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:417: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:420: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:423: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:429: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:432: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:437: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:446: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:452: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:459: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:462: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:465: warning: `regparm' attribute directive ignored
/home/william/install/vpnclient/Cniapi.h:472: warning: `regparm' attribute directive ignored
  LD [M]  /home/william/install/vpnclient/cisco_ipsec.o
ld: /home/william/install/vpnclient/libdriver.so: Relocations in generic ELF (EM: 3)
/home/william/install/vpnclient/libdriver.so: could not read symbols: File in wrong format
make[2]: *** [/home/william/install/vpnclient/cisco_ipsec.o] Error 1
make[1]: *** [_module_/home/william/install/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-powerpc'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


Any idea?

---

### Post by schdefan on 2005-12-05
Regparam is not set in the Ubuntu kernels.
You will need to compile a new kernel yourself. with regparm or maybe you can find a version where regparm is not required.
```
$cat /boot/config-$(uname -r) | grep REGP
# CONFIG_REGPARM is not set
```
schdefan

---

### Post by schdefan on 2005-12-05
in the wiki there are some [howtos of kernel compilation]("https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28CategoryKernel%29")

schdefan

---

### Post by mherring on 2005-12-05
Schdefan;
thanks for all the inputs--- a quick glance at your last link tells me I probably have the wrong setup for kernel sources.  I will start over and report back.
Your help is very much appreciated

---

### Post by schdefan on 2005-12-06
ok. no problem.

schdefan

---

### Post by mherring on 2005-12-08
All fixed...
Thanks to help from this group, I used the instuctions on the wiki to set up the kernel build environment.  Then the vpn installed without a hitch.

A question remains:  With 5.04, I never had to go thru this.  Did something change in 5.10, or did I simply miss an installation step?

Some issues with the instructions on the wiki--I will post separately.

---

