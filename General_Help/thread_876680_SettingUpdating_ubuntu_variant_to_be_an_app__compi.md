---
title: "Setting/Updating ubuntu variant to be an app  compiler"
date: 2008-08-01
forum: General Help
---

### Post by kurotsuki on 2008-08-01
Hi,
I'm new on ubuntu. From my point of view, ubuntu is good enough for an average user. It just that one thing make me a little lost when adding third party applications. Specially when they don't provide binary installation for my architecture (currently I use Hardy Heron x64) and only provide source code to compile.

My problem is, it seems ubuntu does not, by default, install any package necessary to compile most of those source codes. Or at least, It does not work when I try to ./configure -> make -> make install. When configuring, I got an error message about bash or something (the configure file using #! /bin/sh if I'm not mistaken). Since I'm new on linux thing, anyone can guide me?

And, if I want to do this kind of installation for various applications, is there any dev package I need to install? If yes, which ones?

---

### Post by Sef on 2008-08-01
> ...and only provide source code to compile.

My problem is, it seems ubuntu does not, by default, install any package necessary to compile most of those source codes.

To compile, build-essential needs to be installed.

Applications > Accessories > Terminal

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by kurotsuki on 2008-08-01
not working with errors like:

```
g++-4.2:
  Depends: gcc-4.2 (=4.2.3-2ubuntu6) but 4.2.3-2ubuntu7 is to be installed
  Depends: gcc-4.2-base (=4.2.3-2ubuntu6) but 4.2.3-2ubuntu7 is to be installed
```

any other error similiar like this error.

FYI, currently I'm trying using Hardy Heron on i386 architecture (on my office) to test the compile process. but the build-essential update itself already failed. Is there any work arround for this dependency compatibility issue?

---

### Post by theravenproject on 2008-08-01
Try going into System->Admin->Synaptic Package Manager and then click on the search button (Upper Right on the Toolbar-Paper and Magnifier widget) and when the search box comes up type in build essential and then click search...It will find the package for you.  Select the build essential package and then select Install and when you do a box will come up and tell you that in order to install Build Essential, you have to install these other packages (Dependencies)..click on mark...it will go back to the regular box, no click on Apply and it should install it okay!  If so then exit out...if not then take detailed note of the exact error and report back.

---

### Post by kurotsuki on 2008-08-01
I've got the following error from synaptic manager:

```
build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
```

---

### Post by theravenproject on 2008-08-01
Okay, repeat the search process for those two packages then and install them-g++ and libc-dev make sure they are the latest ones and then once installed try going back and trying to install Build Essential via Synaptic again.

---

### Post by kurotsuki on 2008-08-08
> **theravenproject said:**
> Okay, repeat the search process for those two packages then and install them-g++ and libc-dev make sure they are the latest ones and then once installed try going back and trying to install Build Essential via Synaptic again.

OK. I think I found my problem. My repository mirror were outdated. I chose different mirror and try apt-get install build-essential and they work fine :)

thanks for the support :)

---

