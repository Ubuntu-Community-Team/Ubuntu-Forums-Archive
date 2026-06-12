---
title: "problems (probably module relatet) after updates or disk full issue."
date: 2008-09-17
forum: General Help
---

### Post by qorron on 2008-09-17
hi,

I don't know yet wat caused this problems, here are my guesses:
- yesterday I had a grep running all the night long over ~15gig of files.
due to recursive symlinks, this did never stop unitl the disk was full (I did not partition the essential areas of the os in a seperate filesystem, so the rootfs went full.)
I managed to delete this large file.
- i did some automatic security updates since the last boot (~9.9.2008)

now, there are the problems:

I did a reboot because od some weird behavior of the pdf viewer.
(I thought the full disk might have messed something up)
then the troubles begun:

kernel modules which would have been loaded at boot time did not load.
examples:
the network driver (modprobe sky2 in my case)
the audio driver (lshw says I have an ATI Azalia audio device, it also notes the word 'UNCLAIMED')
the thing (don't know if it is a module or something else) which mounts a /dev/shm

and maybe some other stuff.

some additional errors occour as well:
none of the grafic terminals are working (the standard 'Terminal', mrxvt and xterm) the 'Terminal' says: 'There was an error creating the child process for this terminal'.
mrxvt an xterm just don't do anything.
I straced gnome-terminal and found this messages:
open("/dev/ptyp0", O_RDWR)              = -1 EACCES (Permission denied)
open("/dev/ptyp1", O_RDWR)              = -1 EACCES (Permission denied)
...
open("/dev/ptyee", O_RDWR)              = -1 EACCES (Permission denied)
open("/dev/ptyef", O_RDWR)              = -1 EACCES (Permission denied)


repairs so far:
I've inserted 'sky2' into /etc/modules
so I have a network after rebooting.

is there any way to regain a working kernel/modules config?

I havn't seen such a problem before.. and I'm playing around with linux since (kernel) version 2.2 :)

kind regards and thanks for every small tip,
andreas

---

### Post by qorron on 2008-09-17
```
ls -l /dev/ptyp0
crw-rw---- 1 root root 2, 0 2008-09-17 16:06 /dev/ptyp0
```

chmod &#65279;&#65279;&#65279;&#65279;&#65279;666 /dev/ptyp0
now it worls for _one_ terminal.

but all other things are still broken.

at least I have one terminal to do something so I don't have to switch to the console every time I want to type someting.

---

