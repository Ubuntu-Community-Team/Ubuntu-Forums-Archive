---
title: "Installing Yux"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by death__machine on 2009-03-18
Hi,
I wanted a messenger which would give me webcam, so I searched a bit and I found this software called Yux. Can anyone tell me how to Install it?

Btw when I checked the readme it was empty, so I downloaded Yux again and still the readme was empty.


Thanks

---

### Post by death__machine on 2009-03-19
I am sorry I posted this thread in the wrong sub-forum.
Anyone can help me with this?

---

### Post by Partyboi2 on 2009-03-19
Have you tried using one of the programs available in the Ubuntu repository like Kopete. Or maybe even  [[COLOR=Blue]**Gyachi**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=773802") as an alternative to Yux. I tried downloading yux and it seems to be missing files.

---

### Post by death__machine on 2009-03-19
Hey,
I will download gyachi and check it out.
Thanks.
Umm but how do I install .deb files

---

### Post by death__machine on 2009-03-19
Ok one more thing, Now am confused as I dont remember which ubuntu I installed, amd64 or i386 and gyachi has two different downloads for these two versions..


Edit;
I downloaded the amd64 version and that didnt work then i tried i386 which gave me an error 
dependency not satisfiable: libasound2
what does this mean?

---

### Post by Partyboi2 on 2009-03-19
It means you need to install that package, so search Synaptic (System>Admin>Synaptic Package Manager) for 'libasound2'  and install it,  or you can install it from the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install libasound2
```

---

### Post by death__machine on 2009-03-24
Sorry for the late reply, internet was disconnected....

I installed libasound2
then it says I dont have libgail17 and I cant find that using the package manager or the console.

This is what happens

 sudo apt-get install libgail17
[sudo] password for punk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgail17 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgail18
E: Package libgail17 has no installation candidate

---------
Now where do I get libgail17


Also I already have libgail18

---

### Post by Partyboi2 on 2009-03-24
Try downloading the [[COLOR=Blue]libgail17[/COLOR]]("http://packages.ubuntu.com/dapper/libgail17") deb package from here and installing it.

---

