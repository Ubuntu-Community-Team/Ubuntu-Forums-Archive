---
title: "[SOLVED] (how to?) symbolic link to /home/user"
date: 2008-07-29
forum: General Help
---

### Post by rated727 on 2008-07-29
I have installed three Linux distros on the first hard drive of a computer for side-by-side comparison.
[FONT="Courier New"][SIZE="3"](hda1)[/SIZE][/FONT] -- a Red Hat based distro (Berry)
[FONT="Courier New"][SIZE="3"](hda2)[/SIZE][/FONT] -- a Debian based distro (Mint)
[FONT="Courier New"][SIZE="3"](hda3)[/SIZE][/FONT] -- Gentoo

The three access a Linux swap partition on the second hard drive -- [FONT="Courier New"][SIZE="3"](hdb3)[/SIZE][/FONT]

I want to use the second partition of the second drive [FONT="Courier New"][SIZE="3"](hdb2)[/SIZE][/FONT] as a common [FONT="Courier New"][SIZE="3"]/home/*username*[/SIZE] [/FONT]directory.  The purpose here is to have a single directory for data that I create/save that is independant and seperate from the Linux distros that may (and probably will) come and go according to my mood.  

I want to avoid the bother of keeping multiple [FONT="Courier New"][SIZE="3"]/home/*username*[/SIZE][/FONT] directories synchronized across multiple partitions.  How does one direct a given Linux installation to treat [SIZE="3"][FONT="Courier New"](hdb2)/home/*username*[/FONT][/SIZE] as if it were its own?

---

### Post by knightcoder on 2008-07-29
To create symbolic link

ln -s <target path> <link name>

---

### Post by dexter.deepak on 2008-07-29
you can still seperate your /home on a seperate partition...see this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

its for ubuntu, but should work for you.

---

### Post by Potatoj316 on 2008-07-29
cant you tell each distro to just set whatever partition to be its home directory?  wouldnt editing the fstab acomplish that.

---

