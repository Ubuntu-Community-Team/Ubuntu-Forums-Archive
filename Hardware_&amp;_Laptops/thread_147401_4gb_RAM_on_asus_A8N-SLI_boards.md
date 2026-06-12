---
title: "4gb RAM on asus A8N-SLI boards"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by perler on 2006-03-20
hello,

i'm running kubuntu 5.10 and upgraded my A8N-SLI Premium to 4gb ram. unfortunately, ubuntu just shows me 2,7 gb or 3,7 gb (in some applications) of ram installed.

in windows xp there is a /3gb switch which changes some internal memory handling to recognize all of the ram - is there something similar here in ubuntu?

PAT

---

### Post by dermotti on 2006-03-20
if you run **top** (or **free**) in console, how much ram does it say you have available?

---

### Post by perler on 2006-03-20
Mem:   2857304k total,  2779552k used,    77752k free,       28k buffers

---

### Post by ariek on 2006-03-20
When you use the AMD64 cd this shouldn't be a problem. I had this issue with my DELL 1850 server, and it turned out that I used the I386 installation instead of the AMD64.

---

### Post by perler on 2006-03-20
i explicitely use the i386 version for compatibilities sake. theoretically it should be possible to address 4gb in 32bit.  and practically?

PAT

---

### Post by filterpipe on 2006-04-11
Sorry about posting this again, after having placed it in another thrread. Bottom
line: Disable software and hardware memory remapping in the
BIOS->Advanced->CPU->DRAM section of BIOS, install the OS, then re-enable
memory remapping in BIOS. Howver, note that, in the case of our system here,
re-enabling memory remapping didn't work. More digging will be required.

[http://www.linuxcompatible.org/4GB_with_Asus_A8N-SLI_and_A8N-SLI_SE_t33994.html]("http://www.linuxcompatible.org/4GB_with_Asus_A8N-SLI_and_A8N-SLI_SE_t33994.html")

---

### Post by perler on 2006-04-11
ok, thank you for ssaring with us your experiences - but this is no Windows which you must trick into things ;) - there must be a reason why ubuntu behaves different when installing and when running..

PAT

---

### Post by WildTangent on 2006-04-18
[QUOTE=perler]ok, thank you for ssaring with us your experiences - but this is no Windows which you must trick into things ;) - there must be a reason why ubuntu behaves different when installing and when running..

PAT[/QUOTE]
The 386 kernel doesn't recognise that much memory, install the K7 kernel if you want 32 bit.

-Wild

---

### Post by perler on 2006-04-19
this didn't help either. i hadn't the time to play with the diferent bios settings under this kernel (no physical access to the machine right now), but with whatever is set up in the bios right now i'm still stuck with 2,7 gb available memory..

PAT

---

