---
title: "How do I prepare ePSXe and PCSX executables?"
date: 2008-10-10
forum: General Help
---

### Post by r2rX on 2008-10-10
Greetz guys.

As Linux is installed and operating nicely, i've been trying to load up two PSX emulators; ePSXe and PCSX.

Now, i've downloaded the emulators and necessary plugins myself. I've created folders and organized everything nicely.

But if I try execute ePSXe, nothing happens. If I try run PCSX, it tells me that I need to configure the plugins (in the emu) but does not proceed from this screen and exits. When running PCSX again, it shows the same window and then quits.

So far, i've not found anything to help me with PCSX. As for ePSXe, i've encountered a few pages that have helped people (alot of pages from this forum :p) but the method hasn't helped me.

So, how do I prepare the ePSXe executable (whether there are lib packages, other misc command lines etc)? Also, how can I get PCSX working?

.....i'd appreciate the assistance, as well as saying thank you for the patience. :)

r2rX  :D

---

### Post by Meow27 on 2008-10-11
installation guide for epsxe:
[http://ubuntuforums.org/showthread.php?t=612021&highlight=psx+install](http://ubuntuforums.org/showthread.php?t=612021&highlight=psx+install)

installation guide for psx
[http://ubuntuforums.org/showthread.php?t=394097](http://ubuntuforums.org/showthread.php?t=394097)

---

### Post by r2rX on 2008-10-11
Hey Meow27.

The guides you've posted are some of those that i've already read....but i'll try again.

Cheers for the reply.

r2rX  :)

---

### Post by Meow27 on 2008-10-11
well, according to the guide, you were supposed to use the terminal to run them (epsxe)
you should have scph1001.bin (the bios) in the bios folder


ill try to go through the guide again (i reinstalled hardy 2 months ago)

---

### Post by r2rX on 2008-10-12
Hey agian, Meow27.

I've followed the instructions. Basically, i've already made my own folder, and put the emulator (and plugins) in their repsective folders.

All I need to do is decompress the epsxe executable.

So, I ran:

```

sudo aptitude install upx-ucl-beta
```

and

```

r2rxsu@r2rx:~/Desktop/epsxe$ sudo upx -d epsxe
                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
    657368 <-    149019   22.67%    linux/386    epsxe

Unpacked 1 file.
```

So everything should be fine. But the executable refuses to run, returning this error:

```
r2rxsu@r2rx:~/Desktop/epsxe$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

I thought that, perhaps, I need to install the libgtx1.2 library, using:

```
sudo apt-get install libgtk1.2
```

But I get the following:

```
r2rxsu@r2rx:~/Desktop/epsxe$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Does this not imply that the libraries are installed? So if they are, why won't ePSXe use them? 

Oh, I also thought that maybe the libaries necessary are the 32-bit libraries (as I'm using Ubuntu Hardy 8.04.1 x64), so i'd tried:

```
sudo apt-get install ia32-libs
```

It tells me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

NOTE: Now ePSXe is saying this:

```
r2rxsu@r2rx:~/Desktop/epsxe$ ./epsxe
./epsxe: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory
```

pSX is also saying this:

```
r2rxsu@r2rx:~/Desktop/pSX$ ./pSX 
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
```

PCSX is also saying this:
```
r2rxsu@r2rx:~/Desktop/Pcsx$ ./pcsx
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
Segmentation fault
```


I have a feeling that all these issues are around the fact that the 32bit 'lib' libraries are not present/installed. I need all the lib-related 32bit files.....where can I get them and how do I install them? It'll most likely work after this has been done.

r2rX  :)

---

### Post by r2rX on 2008-10-24
Update: Everything is working fine now; PCSX, pSX and ePSXe!!!

There were libraries missing so i've added them and everything works a charm!!

r2rX  :)

---

### Post by jerome1232 on 2008-10-24
In the future this may be of great help to you, it has for me getlibs:[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

It can automatically get the 32 bit libraries and/or 64 bit libraries you need for the executable that you run getlibs on. Makes installing 32 progs on 64 bit 10x less stressful when your missing an unknown library.

---

