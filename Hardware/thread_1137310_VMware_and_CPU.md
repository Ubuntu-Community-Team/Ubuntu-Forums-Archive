---
title: "VMware and CPU"
date: 2009-04-25
forum: Hardware
---

### Post by tanha on 2009-04-25
Can I run VMware if my CPU Core 2 Quad Q8300 doesn't have VT (Virtualization Technology) support ([http://ark.intel.com/cpu.aspx?groupId=39107](http://ark.intel.com/cpu.aspx?groupId=39107))?

(Running 9.04 x86_64)

---

### Post by Barry Carroll on 2009-04-25
Sure, it's usually an option to use the hardware features if you have them but it's no biggie if you don't.  I use virtualbox and I haven't noticed any significant difference in running with vt on or off.

---

### Post by tanha on 2009-04-25
> **Barry Carroll said:**
> Sure, it's usually an option to use the hardware features if you have them but it's no biggie if you don't.  I use virtualbox and I haven't noticed any significant difference in running with vt on or off.

Thank you, Barry. It seems to me that it begs the question as to what the need of VT is -- why is it there if it doesn't make any noticeable difference? 

As an aside, I can't make heads or tales about what it does from [http://www.intel.com/technology/virtualization/](http://www.intel.com/technology/virtualization/) but it seemed like something I would need if I wanted to use vmware...

---

### Post by Barry Carroll on 2009-04-25
I don't really know either.  The impression that I got was that by providing some virtualisation features in hardware the coder wouldn't have to implement them in software, reimplementing the wheel.

---

### Post by tanha on 2009-04-25
OK so after a bit more research it would *seem* that the VT instructions on the intel chip are only needed for 64 bit guests, as explained below

> [http://pubs.vmware.com/ws65_ace25/ws_user/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ws_user&file=intro_sysreqs_ws.html](http://pubs.vmware.com/ws65_ace25/ws_user/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ws_user&file=intro_sysreqs_ws.html)

PC Hardware
•Standard x86-compatible or x86-64-compatible personal computer
•733MHz or faster CPU minimum
Compatible processors include the following:
•Intel — Celeron, Pentium II, Pentium III, Pentium 4, Pentium M (including computers with Centrino mobile technology), Xeon (including “Prestonia”), Core, and Core 2 processors
•AMD —Athlon, Athlon MP, Athlon XP, Athlon 64, Duron, Opteron, Turion 64, and Sempron
•Multiprocessor systems are supported.
•Support for 64-bit guest operating systems is available only on the following versions of these processors:
•Revision D or later of AMD Athlon 64, Opteron, Turion 64, and Sempron
•Intel Pentium 4, Core 2, and Xeon processors with EM64T and **Intel Virtualization Technology**

---

### Post by platinumriver on 2009-05-01
I am running VMWare 64 bit, but only with 32 bit hosts. After reading your post, now I know why it wouldn't let me install 64 bit guests. I have the same Q8300 CPU.

Does anyone know if VirtualBox has the same requirements for running 64bit guests?

---

### Post by tanha on 2009-05-01
I'd install it from the repositories and just try to run an x86_64 live cd... I'm doubtful that it'll work though...

---

### Post by platinumriver on 2009-05-01
You are correct. I installed VirtualBox from the repositories, put in an x86_64 live cd and got the same error message as I got with VMware. It looks like the **Intel Virtualization Technology** is a CPU requirement in order to run 64 bit guests.

---

