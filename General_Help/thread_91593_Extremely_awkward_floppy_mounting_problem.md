---
title: "Extremely awkward floppy mounting problem"
date: 2005-11-17
forum: General Help
---

### Post by ferentix on 2005-11-17
Now, I have seen a lot of posts on problems mounting floppies... however, this is an extremely annoying and somewhat cyclic problem... I could really do with some help.

My Ubuntu box has no internet connection whatsoever, nor can I give it one.

Whenever I try to mount the floppy drive (whether a disk is inserted or not), I get this error:

"Unable to mount the selected voume"

then under "show more details"

"mount: I could not determine the filesystem type, and none was specified"

Most of the solutions I have seen involve updating "pmount" or something. You can probably see the problem already :s...

No internet connection, so can't download directly.
Floppy would be ideal for small file... but floppy doesn't work
I only have CD-R discs- rather a waste for a small file!
No USB ports on Ubuntu box, so no USB pen! ](*,) 

Is there a workaround for my problem that can be done in a basic Ubuntu installation? Floppies are my ideal way of sharing data between my computers, and without them I am essentially high and dry...

---

### Post by suRoot on 2005-11-17
From a terminal, try

```
sudo mount -t msdos /dev/fd0 /media/floppy
```

assuming /dev/fd0 is your floppy & /media/floppy is where you want it mounted.

---

### Post by NeverDream on 2005-11-17
You have to give mount the filesystem with the -t switch. E.g., if it's a Windows-formatted floppy, do:
```
sudo mount -t vfat /dev/floppy0 /media/floppy
```

You can always do
```
man mount
```
if you get stuck.

---

### Post by ferentix on 2005-11-17
OK, thanks a lot :)

Can I specify a default filesystem to assume whenever trying to mount a floppy? Because I know already they will ALL be FAT... Just doing this every time could get annoying for sure, having to enter the root password every time just to read a floppy. And it'd be particularly annoying for any other members of my family who use it...

EDIT: I don't actually appear to have anything even remotely resembling "floppy#" in /dev :?

---

### Post by hajk on 2005-11-17
You can edit /etc/fstab and look for the line 

/dev/fd0        /media/floppy0  auto    rw,users,noauto  0       0

and change "auto" to "msdos"  -- and now you can mount your floppies
with the command "mount /media/floppy" (this is in the standard Breezy setup a symlink to /media/floppy0... might as well save yourself the trouble of typing all those extra "0"s as well...). 
(And, if you're really a minimalist typist, then substitute "vfat" for "msdos"...)

The icon on the desktop can be right-clicked and Unmount selected in the usual way to unmount the floppy.

---

### Post by ferentix on 2005-11-19
Thanks!

But still I have the problem that there isn't actually an entry in the /dev directory remotely resembling fd0! So I still get errors when trying to mount the volume :(

"Unable to mount the selected volume"

"mount: special device /dev/fd0 does not exist"

My floppy drive is in perfect working order though- if I insert a floppy at bootup it recognises it... And the floppies themselves are fine, not corrupted- I just tested them on my WinXP computer.

---

