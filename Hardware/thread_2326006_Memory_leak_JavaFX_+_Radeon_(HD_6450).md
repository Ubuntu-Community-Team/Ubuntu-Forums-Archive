---
title: "Memory leak JavaFX + Radeon (HD 6450)"
date: 2016-05-27
forum: Hardware
---

### Post by ignatiamus on 2016-05-27
Good day,

I run Xubuntu 16.04 in 64 bit, with the automatically used free Radeon graphics driver (for my AMD Radeon HD 6450 graphics card).

When I run JavaFX applications in Oracle's JDK version 1.8.0_92, like the included Ensemble demo or my own programs, there's a memory leak when JavaFX shows some "action" like animated or otherwise active JavaFX components. Firstly, JavaFX's animation loop doesn't run with the standard 60 but 120 fps, and secondly the needed memory for the Java task grows until my physical RAM size is reached, then the system starts to swap memory until it stalls.

The memory leak only appears when the JavaFX application does do something, e.g. when there's a JavaFX animation loop or when I click a JavaFX  button. When I just start the Ensemble demo and don't press any key or mouse button, the memory is OK.

Also Swing and other Java programs work fine on the same system. 

The problematic JavaFX applications work fine on other Ubuntu 16.04 PCs with other graphics cards (like Radeon HD 7XXX).

When I manually invoke Java API's System.gc() at the end of my JavaFX's animation loop, the memory leak grows much slower but is still there. Also the downside is that the JavaFX program then runs very slow because of the manual gc() at each frame.

I also tried to use different garbage collection parameters with "java -X...", but it didn't help.

Since the memory leak only appears on my HD 6450 Ubuntu PC, it looks to be related to some OpenGL-ES (wich is used by JavaFX) problem on the HD 6450 Radeon driver.
How can I encircle the problem, please? Thanks in advance.

Regards,
Hermann

---

