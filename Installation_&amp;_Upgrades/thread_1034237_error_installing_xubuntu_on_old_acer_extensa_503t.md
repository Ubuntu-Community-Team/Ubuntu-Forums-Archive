---
title: "error installing xubuntu on old acer extensa 503t"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by caindelta on 2009-01-08
I am trying to install Xubuntu 8.10 on an old Acer Extensa 503t laptop that has been gathering dust. It has 160mb ram and a 4GB hardrive. It is currently running Windows 98 but i wanted to try my hand at Linux. I am using the Alternate install CD and have burned the iso at 4X. 

When i try to install from the text mode interface and the graphic boot menu it says:

*Not enough memory to load specified kernel*

I have searched the forums and found a reference to a certain command:

*/install/vmlinuz mem=160m*

When i input that command at the text mode interface, it seems to load the kernel but then i get a kernel panic message:

*Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)*

Any help would be greatly appreciated.

---

### Post by Pumalite on 2009-01-08
Your memory and graphics?
You might try Puppy or DSL if memory is too little. Ot increase your memory.

---

### Post by caindelta on 2009-01-08
Memory is 160MB (2x 64MB and 1x 32M) Apparently this is the maximum amount for the Extensa 503t
 
Graphics is Neomagic MagicGraph 128ZV+. I believe it has 2 MB. 

Tried DSL 4.4.10 but when the Live CD loads then i can only see some of the screen since its a weird color, greenish on top and white/yellow in the bottom. Can see four icons but cannot read what they are and can barely read the "Getting Started with DSL" window

---

### Post by snowpine on 2009-01-08
Puppy Linux is a good choice for older computers that can't handle Xubuntu. I've found that Puppy has outstanding hardware detection, so perhaps it will be able to handle your graphics card. Good luck!

---

