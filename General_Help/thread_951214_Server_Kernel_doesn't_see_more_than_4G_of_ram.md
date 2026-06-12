---
title: "Server Kernel doesn't see more than 4G of ram?"
date: 2008-10-17
forum: General Help
---

### Post by BrantlyMedders on 2008-10-17
Due to incredibly low prices and personal ignorance at the time, I upgraded my XPS 400 to a full 4G of ram and a 512MB video card.  Obviously my 32bit OS couldn't address all of it.  While I would like to go to a 64bit OS, I'm using a 32bit CPU (Pentium 4 HT).

So I decided to install the latest server kernel (2.6.24-21) in order to access my full 4 gigs of ram.

After the kernel installed and I booted into it, I ran free, and got this:
```

             total       used       free     shared    buffers     cached
Mem:       3114624     780312    2334312          0      21948     382200
-/+ buffers/cache:     376164    2738460
Swap:      2056312          0    2056312

```

Which is ironically the exact same output I see when I'm running the 2.6.24-21 generic kernel. (I ran uname -r two or three times just to make sure I hadn't booted the generic kernel by mistake).

Although the config files for the server kernel state that PAE and HIGHMEM_64G are enabled, something is obviously going wrong here.  I'm fairly certain my processor should support PAE.

Can someone help me determine what's going on?

---

### Post by Pelham123 on 2008-10-18
I found this information in another post:

[I]Actually the system sees(the correct term is address) a max of 4GiBs.
But you have to count all the system RAM, CPU cache, GPU RAM, disc(s) cache, etc.
So, if you have a 256 GPU plus a 16MiBs disk cache, and other low address memories, the CPU and OS can now only address about 3,5GiBs of the system RAM...
[/I]

Hope this helps

---

### Post by bodhi.zazen on 2008-10-18
> **BrantlyMedders said:**
> Due to incredibly low prices and personal ignorance at the time, I upgraded my XPS 400 to a full 4G of ram and a 512MB video card.  Obviously my 32bit OS couldn't address all of it.  While I would like to go to a 64bit OS, I'm using a 32bit CPU (Pentium 4 HT).

So I decided to install the latest server kernel (2.6.24-21) in order to access my full 4 gigs of ram.

After the kernel installed and I booted into it, I ran free, and got this:
```

             total       used       free     shared    buffers     cached
Mem:       3114624     780312    2334312          0      21948     382200
-/+ buffers/cache:     376164    2738460
Swap:      2056312          0    2056312

```Which is ironically the exact same output I see when I'm running the 2.6.24-21 generic kernel. (I ran uname -r two or three times just to make sure I hadn't booted the generic kernel by mistake).

Although the config files for the server kernel state that PAE and HIGHMEM_64G are enabled, something is obviously going wrong here.  I'm fairly certain my processor should support PAE.

Can someone help me determine what's going on?

You have to have the correct hardware as well.

What is the output of :

```
grep --color=always pae /proc/cpuinfo
```

---

### Post by BrantlyMedders on 2008-10-18
```

brantlymedders@zabulon:~$ grep --color=always pae /proc/cpuinfo
flags           : fpu vme de pse tsc msr **pae** mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr
flags           : fpu vme de pse tsc msr **pae** mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr
brantlymedders@zabulon:~$ 

```

Looks like PAE is supported to me.

---

