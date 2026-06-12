---
title: "Can get into Live CD, but can't get into actual install"
date: 2008-07-17
forum: Hardware
---

### Post by Solidcell on 2008-07-17
So I think my problems are memory related.  I acquired an HP XW8000 which had CentOS.  As I recall it could boot to the login screen.  So that was enough convincing for me that the hardware works.  So I popped in the latest Hardy Heron CD and did a memory test.  Towards the end there were plenty of errors.  It has 6 DIMM slots and I have 6 sticks (4 512MB, and 2 2GB).  I made sure they were installed in the correct order (according to the manual), and also tried all 3 pairs to see if any could pass 100%, none did.  But I went ahead and tried out the Live CD anyways.  That works.  So I went ahead and went through the full installation.  Every time I try to boot however, I either get past the BIOS to a black screen with a white blinking cursor, or I get past the Ubuntu startup sound and I get the background with the crane (but no windows or anything, except for one time when I got a GNOME error).

I have to imagine it's the memory, but I don't see how the Live CD would work then, since both ways of running Ubuntu require RAM.  If it were a problem with the HDD, I could see how the Live CD would work and the OS on the HDD wouldn't, but I don't see how the Live CD is even working if it's a problem with the RAM.

I'm stumped.  Any ideas?

---

### Post by zot171 on 2008-07-19
Alright, first off, I have a computer built from parts scrounged from friends and older computers: it never passes memory tests, and is always closer to the exact opposite. I can still boot Ubuntu from the Live CD, it just takes a long time (I left the computer when the white flashing underscore came up, took a shower, and came back to watch it finish) and occasionally it will not display a graphical login screen. When this occurs, I switch to tty2 (ctrl+alt+F2) and login, then use
```
sudo killall5
startx
```
to clear and then restart the graphical interface. If 'sudo killall5' takes a long time to execute, you can kill it with ctrl+c after it stops displaying new lines of text. Once in, if you have trouble using 'Install' via the icon, you can right-click on the icon and select 'Properties' from the menu. From there, you can discover the path and filename of the installer program and you can enter it into the Terminal to install Ubuntu.

I've done it, and I figure you probably can too.

---

### Post by Solidcell on 2008-07-19
Thanks so much for the reply, I appreciate it.  I've been able to install Ubuntu through the LiveCD before, but when I try to boot into it when it's done, I only get so far as to hear the start sound and get the fancy crane background.  I guess I can just use a tty and never use X, but I'd like to if I want to on a whim (and it makes me wonder what else is screwed up).  What do you think is the problem?

---

