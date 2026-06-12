---
title: "Another laptop fan running constantly"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by N6546R on 2006-06-03
Thought I'd add mine to the list of 6.06 laptops that have continuously running fans. Both the i386 and i686 kernels exhibit the same behavior. Thinkpad T42.

Perry

---

### Post by xela321 on 2006-06-03
Same here, ThinkPad T42.  Fan stays on the whole time.  Processor scaling monitor and top both indicate the fan is running at essentially no load.

---

### Post by zahidism on 2006-06-04
add delll 600m to that. (2ghz centrino M)

---

### Post by Johnsie on 2006-06-04
Add HP Pavilion ZE4404ea (1.2ghz intel celeron) to that list :-/

---

### Post by linuxworld on 2006-06-04
same here :confused:

---

### Post by FuturePast on 2006-06-04
[QUOTE=zahidism]add delll 600m to that. (2ghz centrino M)[/QUOTE]

I have a Dell Latitude D600 and had the same problem.
These laptops have an ATI Radeon graphics card - and as mentioned in another thread it's the graphics card fan that keeps running.
Installing the proprietary ATI drivers seems to resolve the problem:
[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

Now I can't resume after suspend, but at least the machine is usable again.

Cheers
FP

---

### Post by .t. on 2006-06-04
I have this problem, but can control it, as I am running a Dell, with i8kmon. Just apt-get install i8kutils to get it.

---

### Post by zahidism on 2006-06-04
[QUOTE=FuturePast]I have a Dell Latitude D600 and had the same problem.
These laptops have an ATI Radeon graphics card - and as mentioned in another thread it's the graphics card fan that keeps running.
Installing the proprietary ATI drivers seems to resolve the problem:
[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

Now I can't resume after suspend, but at least the machine is usable again.

Cheers
FP[/QUOTE]

my graphics card is a mobility radeon 9000 which i believe is an IGP and it is fanless...nevertheless it could be heating up...but that doesnt explain why it doesn't heat up in windows

---

