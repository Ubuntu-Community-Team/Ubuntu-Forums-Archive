---
title: "3D acceleration in virtualbox crashes VM at ubuntu login screen"
date: 2011-11-21
forum: Hardware
---

### Post by lolzers on 2011-11-21
I decided to install guest additions, which went fine, and then I went to the options for virtualbox and checked 3d acceleration. Then I started up ubuntu, got to the login screen, and then virtualbox crashed and made windows pop up an error. I ran dxdiag, and there was no errors. How can I fix this?

---

### Post by An Sanct on 2011-11-21
To explain what happened, I will tell it like this (as if that VM was a real machine...)

You installed the OS, then you installed the graphics drivers (that kinda failed ...), shut down the machine and inserted a powerful 3D GPU unit, expecting it to work.

You wouldn't do it that way with a real machine and also you shouldn't do it so with a VM. So, shutdown your VM, uncheck 3D support. Run the VM, if it loads, uninstall the guest additions. Shutdown your machine again. check the 3D support now and run the VM. It should run normally, now install the additions again. Problem should be fixed now :)

PS. I consider it a bad idea to play with HW settings ***after*** you install the guest OS.

---

