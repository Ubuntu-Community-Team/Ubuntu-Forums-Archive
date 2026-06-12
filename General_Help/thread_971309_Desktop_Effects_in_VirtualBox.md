---
title: "Desktop Effects in VirtualBox"
date: 2008-11-04
forum: General Help
---

### Post by carmstrong on 2008-11-04
I am running Kubuntu 8.10 on a VM using VirtualBox  i am have tried adding in the desktop effects (desktop cube, etc.) and now it hangs on start up.  I have read online that this may be a graphics limitation because of the VM.  I have installed the guest additions so i have the seamless mode,etc.  I maximized the video memory and still have no luck.  Has anyone tried running desktop effects on a virtual machine? I am just S.O.L?  I get the same response with Ubuntu 8.04.  Thanks.

---

### Post by itisbasi on 2008-11-20
Apparently the video card emulated by virtualbox doesn't yet have the necessary extensions to run compiz...

---

### Post by Therion on 2008-11-20
> **itisbasi said:**
> Apparently the video card emulated by virtualbox doesn't yet have the necessary extensions to run compiz...
Correct.  There is no 3D acceleration support in Virtual Box which I believe is what Compiz needs to perform it's tricks.

---

