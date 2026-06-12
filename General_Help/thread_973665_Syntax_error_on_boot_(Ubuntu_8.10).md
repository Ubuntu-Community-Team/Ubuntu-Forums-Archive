---
title: "Syntax error on boot (Ubuntu 8.10)"
date: 2008-11-06
forum: General Help
---

### Post by Monobi on 2008-11-06
I upgraded to Ubuntu 8.10 from 8.04 about a week ago. Just recently I tried to login to my Ubuntu partition when I got the following error:

```

/etc/default/rcS: 1: Syntax error: ")" unexpected
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rcS main process (2167) terminated with status 2
/etc/default/rcS: 1: Syntax error: ")" unexpected
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rc2 main process (2176) terminated with status 2

```

I figured it must be a problem with some file, although I'm not entirely sure what or how to proceed. I should note that my CDROM does not work so I am not able to boot a live CD to fix any problems. Furthermore both (recovery mode) and the regular boot yield this result, so I can't even drop to root terminal (at least the way I usually do).

---

### Post by Monobi on 2008-11-07
Does anyone have any ideas? I've been using Windows since I've been unable to boot into Ubuntu...

---

### Post by happyhamster on 2008-11-07
- When booting in recovery mode, do you (eventually) get a menu in which you have the option to drop to a root shell?

- If so, choose that option and issue:

cat /etc/default/rcS


- In my case (Hardy Heron), the output looks like this:

```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

```


- If there's something wrong with the file(*), you can edit it using the command:

nano /etc/default/rcS

- Take your time while editing. Making a mistake could leave the system in a worse shape than before I think.
- To save; press ctrl-o, to exit press ctrl-x. Use "cat /etc/default/rcS" again to see if the file has indeed changed.
- In case you get an error about the filesystem being read-only, try:

mount -o remount,rw /

- then try to edit the file again.


Good luck, and keep us informed.



(*) if you're not sure, don't edit anything: just show the output here instead.

[edit: note that the lines starting with the # character are merely comments, they don't do anything. So, in case they're missing, you don't need to add them.]

---

### Post by Monobi on 2008-11-08
> **happyhamster said:**
> - When booting in recovery mode, do you (eventually) get a menu in which you have the option to drop to a root shell?


I never get the option. I get to the screen where I can select it, but it just goes back up to "resume" as to boot normally, at which point I get the error so I can't seem to be able to drop into root shell...

---

### Post by Monobi on 2008-11-08
I booted up a liveUSB (TinyMe) and installed ntfs-3g ...

I installed Ubuntu w/ Wubi, so it's located at C:\ubuntu\disks\root.disk

I tried to mount the file with ntfs-3g, doing:

```

root ~# mkdir /vdisk2
root ~# ntfs-3g /mnt/win_d/ubuntu/disks/root.disk /vdisk2 -o loop
Error opening '/mnt/win_d/ubuntu/disks/root.disk': Read-only file system
Failed to mount 'mnt/win_d/ubuntu/disks/root.disk': Read-only file system

```

Anything else I can do to make it readable? I just need to move my /etc/default/rcS file to rcS.old and create a new one in its place...

---

