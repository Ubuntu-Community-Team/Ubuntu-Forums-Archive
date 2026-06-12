---
title: "Changing order in Grub?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by bogiestl on 2009-04-18
I did a quick search, and probably missed it, but my girlfriend will be using the new box mostly - is there a simple way to make the XP Pro the first in line?
 
BTW, eventual plan is to switch the household to Ubuntu (seems that folks have a nasty habit of opening up "the cutest emails" and stuff - the teenager got 103 viruses on her windoze machine - "All I did was look at Myspace..." Yeah, right...), and this is the first box...

---

### Post by sonu 1807 on 2009-04-18
Tough way-: sudo gedit /boot/grub/menu.lst and then change default from 0 to 3,4 etc depending on your grub . Mine is like this
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

Easy way-:install startup-manager from synaptic and in boot options tab choose your default OS

---

### Post by BugFixBug on 2009-04-18
You can change the order of the grub list by editing the grub file:


in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

a gedit window will appear with the grub conf file. 
At the bottom of this file theres a list of operating systems. At the top of the file there is a option "default num" probarly stating 0 at the moment. You'll have to change this number to the place xp is on your list (counting from 0). save your file and try rebooting.

all should go well.

you can post the content of your grub file here if your unsure.

good luck

---

### Post by bogiestl on 2009-04-18
Thanks... Somehow, I was expecting things to be more complicated...

---

