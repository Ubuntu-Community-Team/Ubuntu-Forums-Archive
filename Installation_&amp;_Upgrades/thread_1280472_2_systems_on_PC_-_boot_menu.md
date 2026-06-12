---
title: "2 systems on PC - boot menu"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by lordmonkeyu on 2009-10-02
Hi everyone,
I am new to ubuntu and to this forum so please don't treat me so much strictly. :)
I have a problem because I installed ubuntu 9.04 on my laptop after having there already win7 beta. And now I have this boot menu (I think coming from ubuntu) on which menu ubuntu is the first so if I don't push any button ubuntu boots. 
How can I change that for win7 otherwise than unninstalling linux ?

---

### Post by scragar on 2009-10-02
Edit ```
gksu gedit /boot/grub/menu.lst
```
And increase the default to one less than your windows option, so if windows is item 4 set the default to 3.

---

### Post by lordmonkeyu on 2009-10-02
Thank you very much :) that helped ;)

BTW can I 'remove' one of the systems of this list? because I made some updates to the ubuntu and now I have more of less sth like that:
-Ubuntu 9.04, kernel 2.6.28-15-generic
-Ubuntu 9.04, kernel 2.6.28-11-generic

What can I do about that?

---

### Post by oldfred on 2009-10-02
IF you manually remove an entry it will change the count. Also whenever a new kernel is downloaded it will change the count.

You can change the number of kernel versions to show with this line in menu.lst Change the howmany to 2 like mine.

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

You want to have 2 just incase the new one does not work, so you have a fallback.

You can move your windows to be first. Move you windows stanza here:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]put here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

Everything in the automagic area gets rewritten on every update to grub including download of new kernels.

---

