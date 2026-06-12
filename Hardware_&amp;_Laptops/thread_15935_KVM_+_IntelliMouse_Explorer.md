---
title: "KVM + IntelliMouse Explorer"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by frontline3k on 2005-02-18
Hi.
I'm using a 4 port KVM switch with a Microsoft Keyboard and Microsoft IntelliMouse Explorer 3.0A, both on PS2 port (don't ask why M$, seems they are preety good in hardware business  :grin: ). The switch simulate the presence of keyb / video / mouse all the time.
Anyway, with ANY distro with Kernel 2.6 (including Warty), I can't use the mouse, neither in console or in X. I do have the mouse cursor on screen, but it's movement it's pretty amazing, I can't tell where it will go next and what mouse button will simulate.
So, hearded from a friend that he had about the same problem with an IBM laptop with a red stick in the middle of the keyboard. He said that the problem was kernel 2.6, he never had that problem with kernel 2.4.
I tried that with some 2.4 based distros: Knoppix 3.7, Mandrake 9.2, yesterday I tried with Archlinux with a 2.4 kernel, and surprise: the mouse is working.
Also tried with Hoary Live CD from Array 4 and had the same problem.

I searched the net and I tried a lot of combination so far, and no luck: 
- psmouse proto=imps in /etc/modules
- changind protocol in xconfig Option "Protocol": ExplorerPS?/2 / Microsoft and so on

One more thing: if I plug the mouse directly in the computer, it's working, no matter what kernel I use.  ](*,) 

All that didn't help.
Anyone can help ?

Regards,
frontline3k

---

