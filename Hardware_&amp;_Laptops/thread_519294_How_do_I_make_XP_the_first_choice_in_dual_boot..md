---
title: "How do I make XP the first choice in dual boot."
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by yazyazoo on 2007-08-06
I just installed Ubuntu and tried to follow  Mathew Miller's instructions.  It worked til the end and I think I did it correctly.  It seems as if I didnt need to do the last few step for setting up dual boot becuase maybe feisty fawn is more current than his instructions.  I didn't have to mess with GRUB.  I hope I installed correctly.  

My question is now when I turn on the computer the first selection to boot is Ubuntu and I want to make it XP.  How would I change it so XP  is the first choice.  Thanks for helping the noob out.

---

### Post by merlinus on 2007-08-06
Count kernel stanzas in /boot/grub/menu.lst.  Subtract one from that of windows.

Find line near the top of the file:

default 0

and change it to that number.

```

gksudo gedit /boot/grub/menu.lst

```

-merlin

---

