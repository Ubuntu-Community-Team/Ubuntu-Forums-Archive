---
title: "Ubuntu or Intel card drivers?"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by DirtDawg on 2007-01-01
I have an Intel graphics card which is using the default drivers that come with Ubuntu. Here's the relevant xorg.conf file:
```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
```

The driver is listed as i810. But I found a Linux ready driver [here]("http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?strstate=live&productid=865&dwnldid=7485&agr=y&lang=eng&prdmap=865"). Should I install the driver from the Intel site for better performance, or will that seriously risk screwing my system up?

BTW, I asked about this in [this]("http://ubuntuforums.org/showthread.php?t=329148") thread as well, but this is a seperate issue and in a better place in the forum.

Thanks.

---

### Post by DirtDawg on 2007-01-02
Okay, well this seems like a relatively smple question to answer, but i guess it isnt. I'm going to try installing the driver and see what happens. I hope i dont screw up my install.

---

### Post by DJ_Peng on 2007-01-06
I'm curious to hear what results you got with it.

---

### Post by DirtDawg on 2007-01-06
Oh right. I thought I did that.

I was asked a couple questions, then told:
```
"The script will now compile the agpgart module and DRM kernel modules for your machine."
```
And this was the result:
```

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

The dri log it refers to says this:
```
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/dirtdawg/installs/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:139: *** Cannot find a kernel config file.  Stop.
```

Having no experience whatsoever with kernels, I gave up quickly. I am certain now, however, that I am having several problems with the default i810 driver. Still, I am not sure this driver would improve anything.

Of course suggestions or insight would be graciously welcome.

---

### Post by Chipmaster on 2007-01-08
I'm also having this issue.  Here's the output from my terminal when I attempt to install this driver:

```
patrick@Hs239-STU01:~/Desktop/dripkg$ sudo sh install.sh 
/bin/ed
/usr/bin/awk
/usr/bin/sort
/usr/bin/md5sum
[: 1072: ==: unexpected operator
[: 1072: ==: unexpected operator
[: 1072: ==: unexpected operator
[: 1072: ==: unexpected operator
[: 1072: ==: unexpected operator


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver: 

Driver Name    : gdg
Description    : Intel 830M/845G/852GM/855GM/865G/GDG Driver
Architecture   : I386
Build Date     : 20040426
Kernel Module  : gdg

Optional Information

Driver Version      :  
Special Description :  

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Select from the following options:

  1. Install driver (default)
  2. Uninstall driver

Enter reponse [1-2], or CTRL-C to exit
1
[: 1161: ==: unexpected operator
[: 1273: ==: unexpected operator









DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the [: 1273: ==: unexpected operator
DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


[: 1273: ==: unexpected operator
[: 1273: ==: unexpected operator

Compiling DRM module...install.sh: 1273: Syntax error: Bad fd number
```

I also located [these](http://intellinuxgraphics.org/download.html) drivers, but was unable to find where cvs saved the 3d packages.

---

### Post by DirtDawg on 2007-01-08
> **Chipmaster said:**
> I'm also having this issue.  Here's the output from my terminal when I attempt to install this driver:

I also located [these](http://intellinuxgraphics.org/download.html) drivers, but was unable to find where cvs saved the 3d packages.


You might be interested to know, the biggest problems I was running into were with 3D apps. Apparently, lots of 3D programs require a set of drivers to run what's known as XGL. Unfortunately, these drivers are not available for Intel cards.

However, there is an alternative called AIGLX, which I gather to be a sort of open-source XGL. InEdgy, AIGLX is installed by default, but I don't believe it's enabled. If you're using Dapper, the process is tougher, but doable, as I learned [here]("http://www.ubuntuforums.org/showthread.php?t=329148").

Anyway, installing AIGLX solved most (maybe all?) of the issues I was having and I didn't have to break my system to install it. Take a look. Hope this helps.

Good luck.

---

