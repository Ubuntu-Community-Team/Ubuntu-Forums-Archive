---
title: "Boot order"
date: 2008-08-02
forum: General Help
---

### Post by lift_test on 2008-08-02
In Feisty I was able to edit the menu.lst file so that XP was first default OS.  The Hardy file seems to be in a different format and I'm reluctant to mess with it without definite information.  Does anybody know the correct incantation?

---

### Post by sstvinc2 on 2008-08-02
Just back up your menu.lst file first; you can always use the live CD to restore it if something goes wrong.  But to change the boot order, I'm pretty sure you just re-order the entries in menu.lst by copying and pasting them into the order you want them to be in.

---

### Post by coffeecat on 2008-08-02
> **lift_test said:**
> The Hardy file seems to be in a different format

Is it? Can't say I've noticed but it's been a long time since Feisty. :sigh: :wink:

As an alternative to what the previous poster suggested. From my Hardy menu.lst:

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0Just change the integer in the default line.

---

### Post by sstvinc2 on 2008-08-02
Good point coffeecat.  I'd just skimmed right past that line while looking at my menu.lst since it's burried among so many commented-out lines.

---

### Post by coffeecat on 2008-08-02
> **sstvinc2 said:**
> I'd just skimmed right past that line while looking at my menu.lst since it's burried among so many commented-out lines.

It is rather, isn't it? If I ever need to edit an Ubuntu menu.lst, I usually delete out all those gospel according to St Shuttleworth lines. It saves a good few gigabytes on my hard drive. :wink:

---

### Post by lift_test on 2008-08-02
Thanks Coffecat, worked fine but one snag, when you count the entries to the one you want, include any dividers.  "Other operating systems" came up as highlighted on first attempt.  Once again thanks.

---

### Post by drs305 on 2008-08-02
I recommend using StartUp-Manager if you aren't familiar with all the intracacies of the boot menu. It's a gui-based app that will allow you to tweak almost all the grub settings: number of kernels to display, **default OS to boot**, menu timeout, colors, etc.

Read the tutorial at the link in my signature.

---

