---
title: "Finding the other end of a PIPE"
date: 2005-11-23
forum: General Help
---

### Post by vDave on 2005-11-23
Hello!

On my Mandrake linux install, I could do a line like the following, as root:

```

ls -l /proc/1234/fd

```

and see a result like the following:

```

lr-x------  1 root root 64 2005-11-23 15:08 6 -> pipe:[14667] --> /mnt/Win2k/Jdrive/SomeFileBeingAccessed.avi

```

However, on my ubuntu install, when I try the similar command:

```

sudo ls -l /proc/1234/fd 

```

I get the following only:

```

lr-x------  1 root root 64 2005-11-23 15:08 6 -> pipe:[14667]

```

Any ideas how to see the target of the pipe or socket?
both 'man ls' and 'info sysutils ls' don't seem to specifiy.

Thanks in advance,
    -dave-

---

### Post by vDave on 2005-11-24
Well after consulting with one of my 'linux guru' buddies, he pointed me towards 'lsof', which shows all open files on the machine.

if anyone knows a "prettier" way to accomplish this, feel free to chime in.

   -dave-

---

### Post by SickTwist on 2005-11-24
I wish I had an answer for you but unfortunately I do not. However, I'm curious to know what you are trying to accomplish. Perhaps there is an alternative way to go about it.

---

### Post by jliedeka on 2005-11-25
I was wondering if that number in brackets is a PID.  I couldn't find anything similar on my system so I was unable to check.  Try "ps auxww | grep 14667" and see if that gets you anything.  I figure it's either a PID or an inode number but PID makes more sense.

---

