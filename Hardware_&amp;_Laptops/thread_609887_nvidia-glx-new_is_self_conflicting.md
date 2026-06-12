---
title: "nvidia-glx-new is self conflicting"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by NickArgyle on 2007-11-11
I am not able to install nvidia-glx-new. The package conflicts with nvidia-glx, but that is a major problem because nvidia-glx is one of the files included in this package. Thus, the package won't install. I have heard that this was fixed in gutsy, but I am still running feisty and this really needs to be fixed. 
What can I do to get the package installed? Will I have to compile the drivers from nvidia's website to use my card? I don't want to revert to the old nvidia-glx because my card is not fully supported.

---

### Post by NickArgyle on 2007-11-12
Anyone??? Tried recompiling the package myself and changing the conflicting file, but that failed miserably. I compiled wrong and now I am incapable of running any packaging system. Apt, Aptitude, and Dpkg are all broken. Anything I want I have to compile from source :-(   
Looks like I should just install gutsy

---

### Post by jocko on 2007-11-12
Just uninstall nvidia-glx before you try to install nvidia-glx-new.
You can not have two different versions installed.

What do you mean with nvidia-glx is one of the files included in nvidia-glx-new?
They are different packages, which provides different versions of the nvidia driver, you are not supposed to have both.

---

### Post by NickArgyle on 2007-11-13
> **jocko said:**
> Just uninstall nvidia-glx before you try to install nvidia-glx-new.
You can not have two different versions installed.

What do you mean with nvidia-glx is one of the files included in nvidia-glx-new?
They are different packages, which provides different versions of the nvidia driver, you are not supposed to have both.

This is from the control file for the nvidia-glx-new deb package:


Conflicts: nvidia-glx-src, nvidia-glx, nvidia-glx-legacy
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video

Notice that the package provides nvidia-glx, but conflicts with it at the same time.

---

### Post by jocko on 2007-11-15
> **NickArgyle said:**
> This is from the control file for the nvidia-glx-new deb package:


Conflicts: nvidia-glx-src, nvidia-glx, nvidia-glx-legacy
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video

Notice that the package provides nvidia-glx, but conflicts with it at the same time.

Have you even tried to do what I suggested?
You need to uninstall the package nvidia-glx in order to install nvidia-glx-new.
As they provide DIFFERENT versions of nvidias driver they cannot coexist.
Me and lots of other people have nvidia-glx-new installed and working fine, despite this apparent self-conflict you think you have found.

---

### Post by NickArgyle on 2007-11-16
> **jocko said:**
> Have you even tried to do what I suggested?
You need to uninstall the package nvidia-glx in order to install nvidia-glx-new.
As they provide DIFFERENT versions of nvidias driver they cannot coexist.
Me and lots of other people have nvidia-glx-new installed and working fine, despite this apparent self-conflict you think you have found.

Yes, I did uninstall nvidia-glx, completely. Look, I posted the actual congif file for the deb package and the confliction is right there.

---

### Post by jocko on 2007-11-17
So how comes it works just fine for me (and lots of other people), then?
I'm not saying you are wrong about the contents of the control file.
I have the same **apparent** conflict in mine, but nvidia-glx-new installs just fine and apt-get does not try to install nvidia-glx, even if it is listed as a dependency.

It worked fine for me in feisty and It still works fine in gutsy, so I think your problem must be caused by something else.
Sometimes a complete reinstall is quicker and easier than trying to find out what's wrong and fixing it.
My advice to you is to backup your /home directory and either reinstall a feisty or install gutsy.

---

### Post by jespdj on 2007-11-17
> **NickArgyle said:**
> This is from the control file for the nvidia-glx-new deb package:


Conflicts: nvidia-glx-src, nvidia-glx, nvidia-glx-legacy
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video

Notice that the package provides nvidia-glx, but conflicts with it at the same time.

"Provides" does **not** mean that it depends on the package nvidia-glx, or that you need nvidia-glx to install it. It means that nvidia-glx-new can be used as a replacement for nvidia-glx. It means: "nvidia-glx-new provides the same software / services as nvidia-glx".

---

