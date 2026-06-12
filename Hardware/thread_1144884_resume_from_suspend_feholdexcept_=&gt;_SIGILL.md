---
title: "resume from suspend: feholdexcept =&gt; SIGILL"
date: 2009-05-01
forum: Hardware
---

### Post by mindoms on 2009-05-01
Hello!

Ive configured an older laptop (acer aspire 1300, athlon mobile, jaunty) as a frontend for mythtv and everything works fine. But after suspend/resume the pc mythfrontend refuses to start and dies with: "illegal instruction"

I think mythtv is only the symptom, so i decided to post here, and not in the mythbuntu sub-forum.

mythfrontend -v all output is at:
[http://paste.ubuntuusers.de/394879/](http://paste.ubuntuusers.de/394879/)
(the last line is missing, where says \"illegal instruction\"

firefox, mplayer work fine.
i can connect to mythconverg on the backend using mysql from a terminal

output of ps -A and lsmod seems to be the same before and after suspend.

no lines add to dmesg when mythfrontend fails to start

this is the relevant gdb output. I thought, maybe the kernel doesnt reinit the floating-point-cpu part correctly. But im just guessing:

```
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/bin/mythfrontend.real 
[..]
Program received signal SIGILL, Illegal instruction.
[Switching to Thread 0xb56c6710 (LWP 3914)]
0xb5db39b9 in feholdexcept () from /lib/tls/i686/cmov/libm.so.6
(gdb) bt
#0  0xb5db39b9 in feholdexcept () from /lib/tls/i686/cmov/libm.so.6
#1  0xb664db6d in QLocalePrivate::doubleToString () from /usr/lib/libqt-mt.so.3
#2  0xb6661a98 in QString::setNum () from /usr/lib/libqt-mt.so.3
#3  0xb6661b31 in QString::number () from /usr/lib/libqt-mt.so.3
#4  0xb6ba8472 in MythContext::GetFloatSetting ()
   from /usr/lib/libmyth-0.21.so.0
#5  0xb6ba90cd in MythContext::GetResolutionSetting ()
   from /usr/lib/libmyth-0.21.so.0
#6  0xb6ba9438 in MythContext::GetResolutionSetting ()
   from /usr/lib/libmyth-0.21.so.0
#7  0xb6b65b4a in DisplayRes::Initialize () from /usr/lib/libmyth-0.21.so.0
#8  0xb6cfc9de in DisplayResX::DisplayResX () from /usr/lib/libmyth-0.21.so.0
#9  0xb6b655fe in DisplayRes::GetDisplayRes () from /usr/lib/libmyth-0.21.so.0
#10 0xb6b657c7 in GetVideoModes () from /usr/lib/libmyth-0.21.so.0
#11 0x080e7e8e in ?? ()
#12 0x0806322c in ?? ()
#13 0x0806f2be in ?? ()
#14 0xb5c51775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#15 0x08062851 in ?? ()
(gdb) x/i 0xb5db39b9
0xb5db39b9 <feholdexcept+89>:	stmxcsr -0x4(%ebp)


tv@aspire:~$ cat /proc/cpuinfo 
processor     : 0
vendor_id     : AuthenticAMD
cpu family    : 6
model         : 8
model name    : mobile AMD Athlon(tm) XP 1800+ 
stepping      : 0
cpu MHz       : 500.010
cache size    : 256 KB
fdiv_bug      : no
hlt_bug       : no
f00f_bug      : no
coma_bug      : no
fpu           : yes
fpu_exception : yes
cpuid level   : 1
wp            : yes
flags         : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
bogomips      : 1000.02
clflush size  : 32
power management: ts fid vid

tv@aspire:~$ uname -r
2.6.28-11-generic
```

Thanks in advance for any help.
stefan

---

