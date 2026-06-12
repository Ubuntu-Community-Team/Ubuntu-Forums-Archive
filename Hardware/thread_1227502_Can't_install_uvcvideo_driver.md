---
title: "Can't install uvcvideo driver"
date: 2009-07-30
forum: Hardware
---

### Post by aj_the_first on 2009-07-30
I would prefer to just get uvcvideo driver in synaptic package manager, but it isn't there.
So I downloaded the tarball, extracted the files, cd to the folder, and then make install and this is what I get:
 
root@Linus:/home/aj/Desktop/uvcvideo-da81aafb9c5d# make install
make -C /home/aj/Desktop/uvcvideo-da81aafb9c5d/v4l install
make[1]: Entering directory `/home/aj/Desktop/uvcvideo-da81aafb9c5d/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.24-24-generic/kernel/drivers/media/video:
 
-e 
Removing obsolete files from /lib/modules/2.6.24-24-generic/kernel/drivers/media/dvb/cinergyT2:
 
-e 
Removing obsolete files from /lib/modules/2.6.24-24-generic/kernel/drivers/media/dvb/frontends:
 
 
Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB
I'll try to remove old/obsolete LUM files from /lib/modules/2.6.24-24-generic/ubuntu/media:
Installing kernel modules under /lib/modules/2.6.24-24-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.24-24-generic 
make -C firmware install
make[2]: Entering directory `/home/aj/Desktop/uvcvideo-da81aafb9c5d/v4l/firmware'
CC ihex2fw
../../linux/firmware/ihex2fw.c:12:20: error: stdint.h: No such file or directory
../../linux/firmware/ihex2fw.c:13:23: error: arpa/inet.h: No such file or directory
../../linux/firmware/ihex2fw.c:14:19: error: stdio.h: No such file or directory
../../linux/firmware/ihex2fw.c:15:19: error: errno.h: No such file or directory
../../linux/firmware/ihex2fw.c:16:23: error: sys/types.h: No such file or directory
../../linux/firmware/ihex2fw.c:17:22: error: sys/stat.h: No such file or directory
../../linux/firmware/ihex2fw.c:18:22: error: sys/mman.h: No such file or directory
../../linux/firmware/ihex2fw.c:19:19: error: fcntl.h: No such file or directory
../../linux/firmware/ihex2fw.c:20:20: error: string.h: No such file or directory
../../linux/firmware/ihex2fw.c:21:20: error: unistd.h: No such file or directory
../../linux/firmware/ihex2fw.c:22:20: error: stdlib.h: No such file or directory
../../linux/firmware/ihex2fw.c:24:20: error: getopt.h: No such file or directory
../../linux/firmware/ihex2fw.c:29: error: expected specifier-qualifier-list before 'uint32_t'
../../linux/firmware/ihex2fw.c:37: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'nybble'
../../linux/firmware/ihex2fw.c:45: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'hex'
../../linux/firmware/ihex2fw.c:52: error: expected ')' before '*' token
../../linux/firmware/ihex2fw.c: In function 'usage':
../../linux/firmware/ihex2fw.c:61: warning: implicit declaration of function 'fprintf'
../../linux/firmware/ihex2fw.c:61: warning: incompatible implicit declaration of built-in function 'fprintf'
../../linux/firmware/ihex2fw.c:61: error: 'stderr' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:61: error: (Each undeclared identifier is reported only once
../../linux/firmware/ihex2fw.c:61: error: for each function it appears in.)
../../linux/firmware/ihex2fw.c: In function 'main':
../../linux/firmware/ihex2fw.c:72: error: storage size of 'st' isn't known
../../linux/firmware/ihex2fw.c:73: error: 'uint8_t' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:73: error: 'data' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:76: warning: implicit declaration of function 'getopt'
../../linux/firmware/ihex2fw.c:89: error: 'optind' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:92: warning: implicit declaration of function 'strcmp'
../../linux/firmware/ihex2fw.c:95: warning: implicit declaration of function 'open'
../../linux/firmware/ihex2fw.c:95: error: 'O_RDONLY' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:97: warning: incompatible implicit declaration of built-in function 'fprintf'
../../linux/firmware/ihex2fw.c:97: error: 'stderr' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:98: warning: implicit declaration of function 'strerror'
../../linux/firmware/ihex2fw.c:98: error: 'errno' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:98: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
../../linux/firmware/ihex2fw.c:101: warning: implicit declaration of function 'fstat'
../../linux/firmware/ihex2fw.c:102: warning: implicit declaration of function 'perror'
../../linux/firmware/ihex2fw.c:105: warning: implicit declaration of function 'mmap'
../../linux/firmware/ihex2fw.c:105: error: 'NULL' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:105: error: 'PROT_READ' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:105: error: 'MAP_SHARED' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:106: error: 'MAP_FAILED' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:114: error: 'O_TRUNC' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:114: error: 'O_CREAT' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:114: error: 'O_WRONLY' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:116: warning: incompatible implicit declaration of built-in function 'fprintf'
../../linux/firmware/ihex2fw.c:117: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
../../linux/firmware/ihex2fw.c:120: warning: implicit declaration of function 'process_ihex'
../../linux/firmware/ihex2fw.c:72: warning: unused variable 'st'
../../linux/firmware/ihex2fw.c: At top level:
../../linux/firmware/ihex2fw.c:127: error: expected ')' before '*' token
../../linux/firmware/ihex2fw.c: In function 'file_record':
../../linux/firmware/ihex2fw.c:244: error: 'struct ihex_binrec' has no member named 'addr'
../../linux/firmware/ihex2fw.c:244: error: 'struct ihex_binrec' has no member named 'addr'
../../linux/firmware/ihex2fw.c: In function 'output_records':
../../linux/firmware/ihex2fw.c:257: error: 'uint16_t' undeclared (first use in this function)
../../linux/firmware/ihex2fw.c:257: error: expected ';' before 'writelen'
../../linux/firmware/ihex2fw.c:259: error: 'struct ihex_binrec' has no member named 'addr'
../../linux/firmware/ihex2fw.c:259: warning: implicit declaration of function 'htonl'
../../linux/firmware/ihex2fw.c:259: error: 'struct ihex_binrec' has no member named 'addr'
../../linux/firmware/ihex2fw.c:260: error: 'struct ihex_binrec' has no member named 'len'
../../linux/firmware/ihex2fw.c:260: warning: implicit declaration of function 'htons'
../../linux/firmware/ihex2fw.c:260: error: 'struct ihex_binrec' has no member named 'len'
../../linux/firmware/ihex2fw.c:261: warning: implicit declaration of function 'write'
../../linux/firmware/ihex2fw.c:261: error: 'struct ihex_binrec' has no member named 'addr'
../../linux/firmware/ihex2fw.c:261: error: 'writelen' undeclared (first use in this function)
make[2]: *** [ihex2fw] Error 1
make[2]: Leaving directory `/home/aj/Desktop/uvcvideo-da81aafb9c5d/v4l/firmware'
make[1]: *** [firmware_install] Error 2
make[1]: Leaving directory `/home/aj/Desktop/uvcvideo-da81aafb9c5d/v4l'
make: *** [install] Error 2
root@Linus:/home/aj/Desktop/uvcvideo-da81aafb9c5d# 
 
 
I've run this loop, downloading and extracting and doing the make install and make all numerous times, this most recent above I did it actually from the root instead of just a sudo as I had read that sometimes uvcvideo gets a bit irritated with just a sudo command and not done from root.
Obviously it made no difference in my case.
I had this camera (Logitech quickcam communicator delux: ID 046d:0992 ) working in Intrepid and Jaunty, but recently backdated to Hardy for the proprietary video driver (ATI: flgrx) that is no longer supported by later kernels. And now I am having issues getting the uvcdriver to install.
qc-usb is not the driver I need by the way, I have checked with this specific cam, and it is said to work perfectly with uvcvideo driver, which I assume is correct since it is default in Jaunty and intrepid, and this cam was plug and play in those distros...
... just gotta get Hardy to use it now...
Any recommendations on how to fix this string of endless errors or what they mean?

---

### Post by aj_the_first on 2009-07-31
I know there has to be a way to install uvcvideo driver in Hardy.  Can I get some help?

---

### Post by aj_the_first on 2009-07-31
update:
When I check the needed driver it outputs nothing.
Check it out:
aj@Linus:~$ lsusb
Bus 006 Device 004: ID 046d:0992 Logitech, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
aj@Linus:~$ dmesg | grep 046d:0992
aj@Linus:~$ 

I should get some sort of response from dmesg should I not?  that is what this thread says:
[http://ubuntuforums.org/showthread.php?t=1211371](http://ubuntuforums.org/showthread.php?t=1211371)

Please I need some help on this

---

### Post by aj_the_first on 2009-08-05
Does no one have any suggestions as to how to fix this?  I am stuck in Iraq and I just want to video chat with my wife, and I can't get the computer to recognize any video devices.  Yet the mic in the camera works fine.  Even the people at berlios have said nothing.  
Why does it work perfectly in Intrepid and Jaunty but not in Hardy?  What are the defaults for Jaunty?

---

### Post by jldiaz29 on 2011-09-13
Hello there,
I have exactly the same problem with this...

I did this one in a terminal:

git clone git://linuxtv.org/media_build.git --*something installed*
cd media_build --*folder created*
./build -- *i don't know what does that mean*
make install -- *this give a mistake*

this is the mistake:


make[2]: Entering directory `/home/jldiaz/media_build/v4l/firmware'
make[2]: *** No rule to make target `../../linux/firmware/ihex2fw.c', needed by `ihex2fw'. Stop.
make[2]: Leaving directory `/home/jldiaz/media_build/v4l/firmware'
make[1]: *** [firmware_install] Error 2
make[1]: Leaving directory `/home/jldiaz/media_build/v4l'
make: *** [install] Error 2
root@ubuntu:/home/jldiaz/media_build# 


Please some help with this.

Cheers!
Jose

---

