---
title: "ASUS F7Sr - Cannot start X Server"
date: 2009-02-14
forum: Hardware
---

### Post by Sladdin on 2009-02-14
Hello

I've installed Ubuntu 8.10 today and I downloaded the Ubuntu 8.10 alternate CD and installed it, but when Ubuntu boots up I just get dropped to the command shell.

When I enter the command "**sudo ****startx**" I get

```
Fatal server error:
no screens found
giving up.
xinit: Connection refused(errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/user/.Xauthority
```

And the specs on my laptop is
Intel D T2390
ATI Radeon Mobility HD2400
4GB RAM, 320GB Harddrive.

Would like to get Linux installed since I've given up on MicrSith , so anyone who is able and willing to help me?:)

Regards Sladd

---

### Post by Sladdin on 2009-02-15
:confused:Anyone

---

### Post by sibnick on 2009-04-24
You can't use 4G RAM without building custom linux kernel on Asus F7SR. See discussion and patches on
[http://bugzilla.kernel.org/show_bug.cgi?id=11103](http://bugzilla.kernel.org/show_bug.cgi?id=11103)
Building kernel with patches: 
[How To Compile A Kernel - The Ubuntu Way | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/kernel_compilation_ubuntu")

---

