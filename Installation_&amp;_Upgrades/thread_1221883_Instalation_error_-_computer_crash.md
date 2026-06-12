---
title: "Instalation error - computer crash"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by ataias on 2009-07-24
Hello! I'm installing blender on the command line when my computer crashed. So It shows error messages and I cannot install blender. And now? I can install other programs. The only trouble is the blender. When I use the apt-get, it shows the same message.

```

ataias @ ataias-desktop: ~ $ sudo dpkg - configure-a  
 Setting libdc1394-22 (2.0.2-1) ...  
 dpkg (sub-process): impossible to perform post-installation script: Error in executable format  
 dpkg: error processing libdc1394-22 (- configure):  
  sub-process post-installation script returned error exit status of 2  
 Setting up ttf-dejavu-extra (2.28-1) ...  
 dpkg (sub-process): impossible to perform post-installation script: Error in executable format  
 dpkg: error processing ttf-dejavu-extra (- configure):  
  sub-process post-installation script returned error exit status of 2  
 Setting libftgl2 (2.1.3 ~ RC5-2) ...  
 dpkg (sub-process): impossible to perform post-installation script: Error in executable format  
 dpkg: error processing libftgl2 (- configure):  
  sub-process post-installation script returned error exit status of 2  
 dpkg: dependency problems prevent configuration of ttf-dejavu to:  
  depends on ttf-dejavu ttf-dejavu-extra, however:  
   Package ttf-dejavu-extra is not configured yet.  
 dpkg: error processing ttf-dejavu (- configure):  
  problems of dependency - leaving unconfigured  
 dpkg: dependency problems prevent configuration of the blender:  
  blender depends on libdc1394-22, but:  
   Package libdc1394-22 is not configured yet.  
  depends on libftgl2 blender (> = 2.1.3-RC5), however:  
   Libftgl2 package is not configured yet.  
  blender depends on ttf-dejavu, but:  
   Package ttf-dejavu is not configured yet.  
 dpkg: error processing blender (- configure):  
  problems of dependency - leaving unconfigured  
 Errors were found during processing:  
  libdc1394-22  
  ttf-dejavu-extra  
  libftgl2  
  ttf-dejavu  
  blender

```

---

### Post by dstew on 2009-07-24
Did you make a syntax error in the command? I think it should be```
sudo dpkg --configure -a
```There should be two hyphens in front of "configure", and a space between --configure and -a.

---

### Post by Ratscallion on 2009-07-24
> **dstew said:**
> Did you make a syntax error in the command? I think it should be```
sudo dpkg --configure -a
```There should be two hyphens in front of "configure", and a space between --configure and -a.
+1 Ditto

---

### Post by ataias on 2009-07-24
I tried many times. The error hold on. (I don't maked syntax error, It was a copy error)

---

### Post by Ratscallion on 2009-07-25
So you still get the error, even with ```
sudo dpkg --configure -a
``` ?

---

### Post by khelben1979 on 2009-07-25
Try
```
sudo apt-get -f install
```

or
[blender.org - Get Blender]("http://www.blender.org/download/get-blender/")

---

### Post by ataias on 2009-07-25
I tried the commands but the error is holding on. Thank you very much. As unable to fix, I'll reinstall ubuntu

---

### Post by Ratscallion on 2009-07-26
No no no! Don't do that!

---

### Post by khelben1979 on 2009-07-26
> **Ratscallion said:**
> No no no! Don't do that!

I agree. There is no need for that.

---

