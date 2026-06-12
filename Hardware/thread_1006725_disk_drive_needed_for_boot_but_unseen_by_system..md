---
title: "disk drive needed for boot but unseen by system."
date: 2008-12-09
forum: Hardware
---

### Post by berkbw on 2008-12-09
I'm beginning to think that my computer is out to get me before I get it.  And I think it knows that 8.10 is evil and twisted in my computer and doesn't want me to return to 8.04, which worked perfectly .

I have an intel d865 w/ 2-120 gb. ata drives, and even tho told to install on one drive, it used both.  Now - I can't examine/modify the second drive to free it up - the system doesn't see it.  If I pull the power plug on it and  try to boot, I get grub error 21.

Help would be appreciated.

berk

---

### Post by berkbw on 2008-12-09
Well, I had mis identified which drive was which, BUT - gediting /boot/grub/menu.lst and replacing all instances of "hd1,0" with "hd0.0" did the trick.

I can even boot 2.6.27 instead of having to boot 2.6.34.

b-

---

