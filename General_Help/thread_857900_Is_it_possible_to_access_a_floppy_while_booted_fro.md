---
title: "Is it possible to access a floppy while booted from a LiveCD?"
date: 2008-07-13
forum: General Help
---

### Post by Armor on 2008-07-13
That's the question. I have scoured the universe for answers, and have come up with non. I NEED to be able to do this - any ideas?

---

### Post by dcstar on 2008-07-13
> **Armor said:**
> That's the question. I have scoured the universe for answers, and have come up with non. I NEED to be able to do this - any ideas?

If the hardware (floppy) is functional, then it will be detected and available - probably as /dev/fd0.

---

### Post by Armor on 2008-07-13
Except it's not working. The floppy drive works fine, there's nothing wrong with it. And this is Ubuntu, not kubuntu - sorry. Anyway, I put a floppy in there, and a box pops up saying "Opening floppy drive. Cancel to quit" and it just hangs there and hangs there and hangs there, and eventually it says that it's unable to mount. I tried manually mounting via right click, Mount Drive, also in the terminal with some mount commands. It will not work.

---

### Post by ghost_ryder35 on 2008-07-13
can u post the errors from the terminal.   

to find out where the drive is being loaded check
```

dmesg | grep floppy

```
then try remounting it in the terminal
```

sudo mount /dev/floppy /mnt/MYFLOPPY

```
when (if) it fails post the output to the forum and we can better help you out

---

### Post by Sef on 2008-07-13
I would download [Knoppix]("http://knoppix.com") and see if it is recognized.

---

