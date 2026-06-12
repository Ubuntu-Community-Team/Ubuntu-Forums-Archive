---
title: "Compile Kernel MODULE??!!"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2006-09-06
I am posting this as a sort of followup to a previous problem.  I have a Fujitsu Lifebook T4010 with Ubuntu Dapper 6.06 LTS installed on it.  I want to use my SD Card reader, but it doesn't work at all.  I posted on this forum, and then contacted the company of the card reader thats on my notebook, O2 Micro.  They actually got back really quickly and sent me the open source of thier driver... ENTER NEW PROBLEM!

When I try to compile the drivers, it aborts with errors because it is looking for the directory '/lib/modules/2.6.15-26-386/build', which isn't there!  Well, the '/lib/modules/2.6.15-26-386' directory is there, but not the build directory!  How do I get this directory?????  I really want these drivers to work!

---

### Post by smelly_sox on 2006-09-07
Free advice from not-an-expert follows:
Usually U need the kernel source installed to build &/or modify additional kernel modules. 
In terminal 
*cat /proc/sys/kernel/osrelease*
Mine returns *2.6.15-26-386*

So if I open Synpatic & search for '2.6.15' I get a list of all the linux; headers, images, modules & source. Now I could be very wrong but if you install the matching headers & source, then your driver installation should work.

Perhaps you should google "build driver linux", "build driver debian", "build driver ubuntu", "compile driver linux" etc....

Regards

---

### Post by tseliot on 2006-09-07
Can you post the full ouput of the error?

and btw you should install:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by ghstzr0 on 2006-09-08
Ok, I finally got the '/lib/modules/2.6.15-26-386/build' directory to appear and so I tried to run make on the driver source again, but still an error... here's the output:

```

$ make -f Makefile.inside

gcc -c -O2 -Wall -D_X86_ -DTASKLET_MBX__ -DMBX_CHANGE_IDEHANDLER  -g -mregparm=3 -fno-common  -I/lib/modules/'uname-r'/build/include -I/lib/modules/'uname-r'/build/drivers/scsi -I`pwd` -Iinclude -IConan -IConan/idver -IConan/_generic -IConan/sm -IConan/SonyMS -IConan/ata -IConan/SRam -IConan/SonyMS/include -IConan/mmc -IConan/mmc/header -IConan/mmc/O2Test -IConan/mmc/intrface/common -IConan/MS2 WdmLib.c -o WdmLib.o

In file included from include/wdm.h:46,

                 from WdmLib.c:18:

/media/GHOSTKEYII/OpenSource/mbx-v2.6.x/winif.h:62: warning: conflicting types for built-in function ‘memcpy’

/media/GHOSTKEYII/OpenSource/mbx-v2.6.x/winif.h:63: warning: conflicting types for built-in function ‘memset’

In file included from include/wdm.h:47,

                 from WdmLib.c:18:

include/ConstDef.h:37:1: warning: "_X86_" redefined

<command line>:1:1: warning: this is the location of the previous definition

include/ConstDef.h:844:1: warning: "__declspec" redefined

include/ConstDef.h:843:1: warning: this is the location of the previous definition

In file included from include/wdm.h:54,

                 from WdmLib.c:18:

include/ntdef.h:265:1: warning: "FASTCALL" redefined

In file included from include/wdm.h:47,

                 from WdmLib.c:18:

include/ConstDef.h:98:1: warning: this is the location of the previous definition

In file included from include/wdm.h:54,

                 from WdmLib.c:18:

include/ntdef.h:290:1: warning: "NTSYSAPI" redefined

In file included from include/wdm.h:47,

                 from WdmLib.c:18:

include/ConstDef.h:810:1: warning: this is the location of the previous definition

In file included from WdmLib.c:18:

include/wdm.h:536:1: warning: "NTKERNELAPI" redefined

In file included from include/wdm.h:47,

                 from WdmLib.c:18:

include/ConstDef.h:96:1: warning: this is the location of the previous definition

In file included from WdmLib.c:18:

include/wdm.h:6209:1: warning: "_DECL_HAL_KE_IMPORT" redefined

In file included from include/wdm.h:47,

                 from WdmLib.c:18:

include/ConstDef.h:146:1: warning: this is the location of the previous definition

make: *** No rule to make target `Conan/SRam/SRam.c', needed by `Conan/SRam/SRam.o'.  Stop.

```

As you can see, the error is at the bottom there, it looks as if its missing some target int the file 'Makfile.inside'.  Any ideas??

---

