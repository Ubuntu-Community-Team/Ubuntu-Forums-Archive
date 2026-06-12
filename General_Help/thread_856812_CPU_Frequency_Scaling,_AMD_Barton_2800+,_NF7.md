---
title: "CPU Frequency Scaling, AMD Barton 2800+, NF7"
date: 2008-07-11
forum: General Help
---

### Post by Vasto on 2008-07-11
I just installed Ubuntu (minimal installation) on a computer. I want to enable frequency scaling because this computer will be a file/media/web server that will be up 24/7, and anything that saves power would be nice.
Ok, so anyways...
```
michael@michael-server:~/Desktop/powerd$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: AMD Athlon(tm) XP 2800+
stepping	: 0
cpu MHz		: 2079.598
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips	: 4162.52
clflush size	: 32

```
It's an AMD Athlon XP 2800+ Barton, running on an Abit NF7 rev.2 motherboard (NForce 2 chipset).

I came across this bug: [https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/223812](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/223812)
And tried to install the .deb from [https://launchpad.net/~hanno-stock/+archive](https://launchpad.net/~hanno-stock/+archive), but I get the below error.
```

michael@michael-server:~/Desktop/powerd$ sudo dpkg -p powernowd_0.97-2ubuntu5~hs2_i386.deb 
Package `powernowd_0.97-2ubuntu5~hs2_i386.deb' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
michael@michael-server:~/Desktop/powerd$ sudo dpkg -i powernowd_0.97-2ubuntu5~hs2_i386.deb 
(Reading database ... 37318 files and directories currently installed.)
Preparing to replace powernowd 0.97-2ubuntu5~hs2 (using powernowd_0.97-2ubuntu5~hs2_i386.deb) ...
 * Stopping powernowd:                                                   [ OK ] 
Unpacking replacement powernowd ...
Setting up powernowd (0.97-2ubuntu5~hs2) ...
 * Starting powernowd...                                                         * CPU frequency scaling not supported...                                [ OK ] 

```

Any help would be appreciated.

---

### Post by dcstar on 2008-07-12
> **Vasto said:**
> I just installed Ubuntu (minimal installation) on a computer. I want to enable frequency scaling because this computer will be a file/media/web server that will be up 24/7, and anything that saves power would be nice.
.......
```

 * Starting powernowd...     * CPU frequency scaling not supported...  [ OK ] 

```

Any help would be appreciated.

If the hardware (and kernel) doesn't support frequency scaling, then you can't have it.

---

### Post by mcduck on 2008-07-12
Barton, like other Athlon and Duron cores, doesn't support frequency scaling.

However there's app called "athcool" that instead of scaling the frequency tells the CPU to use powersaving mode when it's idle. It should be in repositories (at least it used to be) so you could give it a try. But be aware that in some (although rare) cases using athcool might result in more or less seriour problems (ranging from distorted sound to filesystem corruption..).

I used it without any problems on my old machine with AXP2800+ & Asus A7N8X-E motherboard (which is also NF2-based).

---

### Post by Vasto on 2008-07-12
> **mcduck said:**
> Barton, like other Athlon and Duron cores, doesn't support frequency scaling.

However there's app called "athcool" that instead of scaling the frequency tells the CPU to use powersaving mode when it's idle. It should be in repositories (at least it used to be) so you could give it a try. But be aware that in some (although rare) cases using athcool might result in more or less seriour problems (ranging from distorted sound to filesystem corruption..).

I used it without any problems on my old machine with AXP2800+ & Asus A7N8X-E motherboard (which is also NF2-based).

Ah, Thank you. I don't know why I thought Bartons had CPU frequency scaling. I'll have to try out athcool.

---

