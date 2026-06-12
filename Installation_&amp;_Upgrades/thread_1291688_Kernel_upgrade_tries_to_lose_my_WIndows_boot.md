---
title: "Kernel upgrade tries to lose my WIndows boot"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2009-10-15
_Ubuntu 9.04, with Windows-XP dual boot arrangement_

Greetings.

After my recent success installing Ubuntu 9.04 on my Windows box, the boot menu came up looking like this:
> 
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
Other operating systems:
Microsoft Windows XP Professional

Thus, if I don't watch the boot, Ubuntu will boot within 10 seconds of presenting this menu. Since this is not to my liking (I still want XP as my default boot), I edited /boot/grub/menu.lst so that the menu looks like this:
> 
Microsoft Windows XP Professional
Other operating systems - Do not select this line:
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+

(I also gave it a 30-second timeout.)

Then the automatic update kicked in, including a kernel upgrade. When it was done, it asked me what to do with the boot menu. I told it to go ahead and impose the new menu, after saving my current menu.lst. Now the menu.list would present the following choices:
> Ubuntu 9.04, kernel 2.6.28-15-generic
Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
That is, two modes of the new release 2.6.28.15 kernel, plus two modes of the release 2.6.28-11 kernel.

*It omitted the Windows boot section; ***I had to add that back manually by copying the code from the original installed version of menu.lst. :mad:**

Am I condemned to have to remember to do this every time there is a kernel upgrade?  I can't fault Ubuntu for *some* self-promotion but this is ridiculous!

Anyone out there got a solution *besides* this manual edit?

Thanks much.

[SIZE="1"]More bones to pick in another thread...[/SIZE]

---

### Post by louieb on 2009-10-15
You put your XP entry in the **automagic **section of /boot/grub/menu.lst. Thats why it got erased. 

To put it on top and keep it from being erassed put the XP entry betweeen the these lines. 

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by rpaskudniak on 2009-10-16
louieb,

Thanks for the advice.  I have moved the those first two menu items above the BEGIN AUTOMAGIC section.  Of course, I won't know for certain if I have screwed up until my next reboot.  And I won't have confirmation that this has solved my dilemma until the next kernel upgrade.

Sighh....

However, I will still mark this thread as solved.

Again, thanks much! :popcorn:

---

