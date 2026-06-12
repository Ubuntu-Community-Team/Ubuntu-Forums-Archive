---
title: "Cant install ati drivers for old ati 9600 gfx card"
date: 2010-04-10
forum: Hardware
---

### Post by leothlon on 2010-04-10
First of i'm not sure if i posted this in right section :/ hope i did.

But to the problem:
i recently installed ubuntu on this old comp because i havn't used ubuntu verry much and its been quite a while sens i did i wanted to play around with it to learn some more before i swich my maincomp over to it.
but when i tried to run heroes of newerth it just flash the screen black and i get:
```
"simon@simon-ubuntu:~/HoN$ sh hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: ARB_shader_objects not available."
```

so i figured it was most likly a driver issue and downloaded the driver from ati "ati-driver-installer-9-3-x86.x86_64.run" 
and when i try to install it i get this:

```
simon@simon-ubuntu:~/Downloads$ sudo sh ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.V4Vja4                                           
Verifying archive integrity... All good.                                         
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................                                                                                            
==================================================                                                                                                               
 ATI Technologies Linux Driver Installer/Packager                                                                                                                
==================================================                                                                                                               

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro                                              

Removing temporary directory: fglrx-install.V4Vja4
simon@simon-ubuntu:~/Downloads$ --iscurrentdistro
--iscurrentdistro: command not found             
```


and the driver wont install, i got the advices to go into system > administration > hardware drivers   but the window that comes up is empty so there is no driver i can download from there, i guess it might be because the gfx card is so old? its a ati radeon 9600 after all :)

now i am woundering what is the problem and how do i fix it? there must be some way to install the drivers...

remember that i am not a pro at ubunto or linux in general so try to break it down to not to complicated steps :D

thanks in advance!

---

### Post by rtilson on 2010-04-10
Ati switched the 9600 to legacy status in the 9.3 release which seems you are trying to install. So technically those drivers should work. 

I would try looking in synaptic package manager for a packages called xorg-driver-fglrx check it and it will mark all packages that are needed. This way might work better than installing from ATI installer.

---

### Post by jsp21c on 2010-04-10
Hi check the article I wrote a couple of days ago. [http://ubuntuforums.org/showthread.php?t=1450647](http://ubuntuforums.org/showthread.php?t=1450647)

If ATI publish a .run type linux driver for your card you might be lucky.

UPDATE;  I've taken a look at the ATI site and they do indeed publish a .run type file, "ati-driver-installer-9-3 etc .run" . Hopefully you can install this driver using the method which worked for me (follow the link above).

---

### Post by leothlon on 2010-04-10
thanks for the awnsers.

downloaded xorg-driver-fglrx from package manager, unfortunatly it still didn't allow me to run the driver install file. and game would still just flash black and then dissapear :/

and jsp21c the problem is that my card is so old the ati dont update drivers for it anymore so the drivers there dont work on new ubuntu versions :/
according to something i found in a guide somewhere.


also found this somewhere
> "Before attempting to install the ATI Proprietary Linux driver, the following soft-
ware must be installed:
&#8226; POSIX Shared Memory (/dev/shm) support is required for 3D apps
&#8226; glibc version 2.2 or 2.3
&#8226; Linux kernel 2.6 or higher
&#8226; XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4"


and

> "&#8226; The following packages must be installed in order for the CatalystTM Linux
driver to install and work properly:
&#8226; XFree86-Mesa-libGL
&#8226; libstdc++
&#8226; libgcc
&#8226; XFree86-libs
&#8226; fontconfig
&#8226; freetype
&#8226; zlib
&#8226; gcc"

---

### Post by leothlon on 2010-04-10
actually now when i tried to start the game i got:

warning: The VAD has been replaced by a hack pending a complete rewrite
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Crash log saved as '/home/simon/.Heroes of Newerth/game/crash_0.3.1.0_01.log'
Segmentation fault

so i guess we atleast got past the shader problem :D

---

