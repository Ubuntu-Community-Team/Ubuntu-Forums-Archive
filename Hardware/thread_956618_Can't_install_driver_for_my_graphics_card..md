---
title: "Can't install driver for my graphics card."
date: 2008-10-23
forum: Hardware
---

### Post by psyoptic on 2008-10-23
I have an ATI Radeon HD 4850 graphics card and was trying to install the drivers using the manual method in this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide).

Everything seems fine, until I try to install the .debs packages. This is the message I get in Terminal:

```
dpkg: error processing xorg-driver-fglrx_8.532-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.532-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.532-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.532-0ubuntu1_i386.deb
 fglrx-kernel-source_8.532-0ubuntu1_i386.deb
 fglrx-amdcccle_8.532-0ubuntu1_i386.deb
```

The guide states that if an error occurs during this process, it is usually because of a dependency of the amdccle package on 32 bit libraries while I have a 64 bit installation. It says to type these commands in Terminal to fix the problem:

sudo apt-get install -f 

and then

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.522*.deb fglrx-kernel-source_8.522-0*.deb fglrx-amdcccle_8.522-0*.deb 

At which point I get this error:
```
dpkg: error processing xorg-driver-fglrx_8.522*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.522-0*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.522-0*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.522*.deb
 fglrx-kernel-source_8.522-0*.deb
 fglrx-amdcccle_8.522-0*.deb
```

What exactly does that mean? I'm also experiencing a lot of display flickering now. Does this have anything to do with what I just did? Any help would be appreciated.

---

### Post by psyoptic on 2008-10-23
Bump.

No one's ever had any trouble installing this card before?

---

### Post by ardvark71 on 2008-10-23
Hi...

Did you try installing the fglrx driver through Synaptic before this? :confused:

Best Regards...

---

### Post by psyoptic on 2008-10-23
> **ardvark71 said:**
> Hi...

Did you try installing the fglrx driver through Synaptic before this? :confused:

Best Regards...

Not sure... but every thread about my video card suggested that installing the card manually was the best solution.

Envyng doesn't work either since the card is fairly recent.

---

### Post by psyoptic on 2008-10-24
Bump.

I'd really appreciate any feedback on this. This whole thing's been a nightmare for me. I hope everything else in Ubuntu isn't as complicated as this. If it is, I might consider reverting back to Windows : (

---

### Post by ardvark71 on 2008-10-25
> **psyoptic said:**
> Bump.

I'd really appreciate any feedback on this. This whole thing's been a nightmare for me. I hope everything else in Ubuntu isn't as complicated as this. If it is, I might consider reverting back to Windows : (

Hi...

I honestly don't know what else to suggest apart from researching and then buying a card that is more compatible with Ubuntu as well as seeing if you can download the fglrx driver from Synaptic. :( I know Nvidia cards do better overall with Ubuntu than ATI.

However, I'm assuming a paid quite a bit for your card and purchasing another one is not going to be on the agenda.

I'm sorry I couldn't be more help. :(

Best Regards...

---

### Post by Yashiro on 2008-10-25
The manual method works.

If you mess up reset Xorg to defaults and do it again. ```
sudo dpkg-reconfigure xserver-xorg
```

This time READ the text of the lines you are putting in and adjust any errors in numbering. 
ie change instances of 532 or 522 that are in the guide with numbers that match your files. 

**The guide has typos.**

It's a pain in the *** but once done, the drivers work OK and do all the usual compiz stuff.

Running Ubunutu 8.04, Catalyst 8.9 on an Asus 4850.
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.7979 Release
```


An easier solution might be to install 8.10 (Intrepid).
There will be no 3d with that driver yet though, I suspect.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)
might help too.

---

### Post by ardvark71 on 2008-10-25
Hi...

Thanks, Yashiro. It's nice to know the card works. :)

Best Regards...

---

