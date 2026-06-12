---
title: "[SOLVED] Main Menu won't let me tick Synaptic PM"
date: 2008-11-25
forum: General Help
---

### Post by Bucky Ball on 2008-11-25
Hi all.

I am resurrecting my desktop box which has 8.04 and a fresh download of the latest updates (hasn't been done since I originally installed in May!). Couple of things but will post them in separate threads.

I go to System->Preferences->Main Menu and I can't tick Synaptics Package Manager. Rather, when I do, it stays ticked for about 2 seconds then un-ticks itself and goes to small italics again. This is also happening with a few other items like Software Sources, Hardware Drivers. As you can imagine, makes it kinda hard to make any sweeping changes to the system!

Any clues greatly appreciated. Wondering if I am missing permissions to make these changes.

BTW, this machine is running Ubuntu Studio and I have added Ubuntu Desktop also, but it was doing this before I made that change, I installed UDesktop through terminal.

---

### Post by geirha on 2008-11-25
Permission problems would be my first guess too. Try running the menu editor from a terminal by typing ```
alacarte
``` try doing those changes again, and see if it outputs any error messages in the terminal.

Also, check that you have write permissions to at least .local in your homedir. This find should find all files and directories that are either not owned by your user, or not writeable to the owner.
```
find ~/.local -not -user $USER -o -not -perm +0200 -ls
```

---

### Post by Bucky Ball on 2008-11-25
Thanks for that. When I open alacarte from the terminal, everything is ticked. When I close that and open it from the menu, unticked.

The second command outputs no files, back to command prompt. I tackled this problem briefly on my last holidays and never got to the bottom of it ...

---

### Post by geirha on 2008-11-25
Hm. Open a terminal and run ```
tail -f ~/.xsession-errors
``` Then open alacarte from the menu and do those changes that fail. Does .xsession-errors show any error messages when it fails?

---

### Post by Bucky Ball on 2008-11-25
> **geirha said:**
> Does .xsession-errors show any error messages when it fails?
```

$ tail -f ~/.xsession-errors
![1227601111,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601111,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601111,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601111,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601116,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601116,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601132,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227601132,000,xklavier_evt_xkb.c:xkl_xkb_process_x_event/]     ATTENTION! Currently cached group 1 is not equal to the current group from the event: 0
![1227
...Too much output, ignoring rest...
```I went no further ...

This is interesting from 'top':

```
Tasks: 165 total,   1 running, 163 sleeping,   0 stopped,  ** 1 zombie**
```

---

### Post by geirha on 2008-11-25
Not sure what to make of the .xsession-errors messages, but it seems to be something with keyboard, and not related to alacarte. 

As for the zombie process, run
```
ps -efH | less
```
and look for a process marked with defunct.

EDIT: Oops, how did that grep get in there. Fixed.

---

### Post by Bucky Ball on 2008-11-25
Didn't find anything with 'defunct'.

* Update:

Okay, when I right click 'Synaptics' in the main menu and go to properties, it tells me this is the command:

gksu /usr/sbin/synaptic

Run that in a terminal and package manager appears no problem. Try to tick it in main menu and problem. Have no idea about this one meself ... :(

---

### Post by geirha on 2008-11-26
Try resetting the menus to default by removing all user configuration of the menus. 

```

mkdir ~/backup
mv ~/.config/menus ~/.local/share/applications ~/backup/

```

---

### Post by Bucky Ball on 2008-11-26
Hey, geirha, thanks for your help. But this is what I did (and was gonna use this box for experimentation anyhow). I killed the ubuntustudio install and installed ubuntu straight. Then I just added all apps for ubuntustudio and working a treat (after a bit of  screwing around with the grub menu, naturally). Again, cheers, and all worked out in the end. Was gonna mark this as solved earlier but actually went out tonight, a rarity!

All the best ... :)

ps: there were so many issues, once I fixed one there was another one right behind that so just went the easy option and now much better setup, yea? Cheers

---

