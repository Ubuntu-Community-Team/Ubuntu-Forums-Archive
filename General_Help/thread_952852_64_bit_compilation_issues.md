---
title: "64 bit compilation issues"
date: 2008-10-19
forum: General Help
---

### Post by sippyCUP on 2008-10-19
I'm trying to make a piece of software for class (SCALE5.1, a code from a national lab) and have successfully done it on Ubuntu 8.04 32bit. However, I have installed Xubuntu 8.04 x64 on my desktop and am having 64-bit specific problems. Here is what I've done so far:

```
sudo make configure
sudo ./installscale
```

Here is a snippet of the errors from the install log file:

```
making install in nitawl...
Date and Time Sun Oct 19 11:08:51 EDT 2008
/opt/intel/fce/10.1.018/bin/ifort -o nitawl nitawl.o  -i-static -L/opt/SCALE5.1/Linux_2/lib -lnitawl -lscale
ld: i386 architecture of input file `/opt/SCALE5.1/Linux_2/lib/libscale.a(getnam.o)' is incompatible with i386:x86-64 output
ld: i386 architecture of input file `/opt/SCALE5.1/Linux_2/lib/libscale.a(machname.o)' is incompatible with i386:x86-64 outp$
ld: i386 architecture of input file `/opt/SCALE5.1/Linux_2/lib/libscale.a(getmtm.o)' is incompatible with i386:x86-64 output
make[2]: *** [nitawl] Error 1
making install in xsdrn...
Date and Time Sun Oct 19 11:08:51 EDT 2008
/opt/intel/fce/10.1.018/bin/ifort -o xsdrn xsdrn.o  -i-static -L/opt/SCALE5.1/Linux_2/lib -lxsdrn -lscale
ld: i386 architecture of input file `/opt/SCALE5.1/Linux_2/lib/libscale.a(getnam.o)' is incompatible with i386:x86-64 output
ld: i386 architecture of input file `/opt/SCALE5.1/Linux_2/lib/libscale.a(machname.o)' is incompatible with i386:x86-64 outp$
ld: i386 architecture of input file `/opt/SCALE5.1/Linux_2/lib/libscale.a(getmtm.o)' is incompatible with i386:x86-64 output
make[2]: *** [xsdrn] Error 1
```

I don't really know where the config files are that make uses, though I can see that it's an issue with ld and 64bit operation. I really want to get this up and running, otherwise I'll have to resort to Window for this computer.

Any ideas?

Thanks for your time,
Eric

---

