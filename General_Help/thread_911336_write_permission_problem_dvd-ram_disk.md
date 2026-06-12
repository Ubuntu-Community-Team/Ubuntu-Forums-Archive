---
title: "write permission problem dvd-ram disk"
date: 2008-09-05
forum: General Help
---

### Post by sdowney717 on 2008-09-05
ok, I have a dvd-ram disk and I formatted the disk using 
(make sure disc is unmounted or it wont really format, you get no warning)

scott@scott-desktop:~$ mkudffs /dev/scd1
start=0, blocks=16, type=RESERVED 
start=16, blocks=3, type=VRS 
start=19, blocks=237, type=USPACE 
start=256, blocks=1, type=ANCHOR 
start=257, blocks=16, type=PVDS 
start=273, blocks=1, type=LVID 
start=274, blocks=2236173, type=PSPACE 
start=2236447, blocks=1, type=ANCHOR 
start=2236448, blocks=239, type=USPACE 
start=2236687, blocks=16, type=RVDS 
start=2236703, blocks=1, type=ANCHOR 
scott@scott-desktop:~$ 

problem is I can only write to the disk if I am root,(sudo nautilus to test), so I right click and go into permissions and tell it for others to be able to read and write files. Now it can write to the dvd-ram.
does this have to be done for every disk that gets formatted?

---

