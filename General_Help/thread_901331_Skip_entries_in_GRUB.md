---
title: "Skip entries in GRUB?"
date: 2008-08-26
forum: General Help
---

### Post by Burillo on 2008-08-26
I'm not sure where to put it so please move if necessary.

I have 4 operating systems installed (2 WinXP, 2 Ubuntu). I'd like to have separate sections for OS types - like 2 Ubuntu's, then 2 WinXP's. my boot menu looks similar to this:

Linux:
Ubuntu 1
Ubuntu 2

Windows:
WinXP 1
WinXP 2

what i am asking is - is there a way to actually SKIP entries that don't contain any OS choice? Like i press DOWN only once and go from Ubuntu 2 to WinXP 1, and not three times. Is this possible?

---

### Post by drs305 on 2008-08-26
Yes. You can manually edit /boot/grub/menu.lst and remove the non-OS descriptions in /boot/grub/menu.lst.

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst

```

I am not on a dual boot machine at the moment, but you would delete the *section* that had the "Windows:" line in it. 
Added: this is the section I would remove on my machine (note you are removing one of the 'titles':
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root

```

One note: the menu list choses the option to run by counting the number of "titles". Even though you are not removing a valid choice, you are removing a "title". If your default OS is one below the one you are removing, you would need to change the line "default=X" to "default=X-1", with X being a number (in your case probably 1 through 6  before deleting).

---

### Post by Burillo on 2008-08-26
you misunderstood me a bit. I didn't say i wanted to delete them. I want GRUB to SKIP them when selecting OS - just like the "greyed-out" menu entries in GTK! i mean they are shown but they can't be selected!

---

### Post by caljohnsmith on 2008-08-26
I've also wished Grub had that feature of skipping the dividers in the menu, Burillo; but because those "dividers" are essentially just bogus entries for another OS (entries that don't point to any OS), then as far as I know you can't get Grub to skip over them.

---

