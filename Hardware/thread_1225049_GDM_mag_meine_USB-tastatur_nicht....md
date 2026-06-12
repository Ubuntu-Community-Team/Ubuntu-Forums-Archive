---
title: "GDM mag meine USB-tastatur nicht..."
date: 2009-07-28
forum: Hardware
---

### Post by gu4rdi4n on 2009-07-28
hi,
i have bought me a new keyboard, the roccat valo.
Now i have the Problem that gdm dont like the keyboard.
That means:

Wenn i turn the PC on, the Keyboard is full functionally, i can get into BIOS.
But after the boot of linux (with extlinux) my keyboard turns off. (display and lights off -> power off)
But _after_ logging in into gdm the keyboard will turn on and works correctly.
I cant login, because the keyboard is turned off while gdm waits for login.

The intern USB-Hub stay active while the entire boot-process,
my mice, that i have connected with it, works properly.
The Hub runs with a secons USB-Connection.

I have temporarly solved this problem by turning auto-login on,
but this cant be an solve.

Does anybody know how to make gdm and the keyboard be friends?

---

### Post by Garyu on 2009-10-14
My girlfriend has the Roccat Valo keyboard and the Roccat Kone mouse. She's not running linux though. We have had problems with these products not responding during boot etc. Unable to press delete to enter BIOS setup because the keyboard is not active at that time. Then when booting Windows (both XP, Vista and 7 tried and failed) either the mouse or the keyboard will stop working. 

Roccat support says they are working on a solution. According to them, unplugging both the Kone mouse and the Valo keyboard, then plugging both of them back in within 5 seconds of eachother should solve the issues. 

Our solution was to disable quick boot in the BIOS. Then using a different keyboard/mouse to install the drivers in Windows, and we have functionality most of the time.

---

