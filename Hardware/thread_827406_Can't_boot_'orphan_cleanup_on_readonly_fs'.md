---
title: "Can't boot: 'orphan cleanup on readonly fs'"
date: 2008-06-12
forum: Hardware
---

### Post by tmcw on 2008-06-12
This is bad. I can't boot normally - the system ends up with a blinking cursor after going through grub and the first Ubuntu screen. Booting with recovery mode gives the more specific hang message:

Ext3-fs sda2 ophan cleanup on readonly fs

And the Ubuntu Live CD doesn't boot

Also, Puppy Linux will not boot: a unionfs problem, it says.

memtest says everything's fine.

Booting SLAX, it hangs on "Mounting non-root local filesystems"

I can access the ext3 partition from Windows and have copied over my home directory.

I have no idea what to do at this point, I'm never going back to Windows, but Ubuntu seems more toasted than I could ever imagine.

---

### Post by ARSCHKOCH on 2008-06-18
same problem here since i upgraded from ubuntu 7.10 to 8.04 a few days ago. I tried to reinstall with a 8.04 CD today but can't even boot the live cd.

anybody has a hint or a solution? Of course i will answer any further questions but at this point i don't know where to start...

thank you in advance!
...

---

### Post by emresunecli on 2008-08-08
same problem here to i didn't make any difference but it happened?

---

### Post by Pipey on 2008-09-25
I am having this issue too.  As far as I can remember, the computer went into hibernate.  After that, i think the battery died.  Since then, Ive not been able to boot from hdd, cd, or usb.  

recovery mode stalls on [   10.192913] EXT3-fs: sda5: orphan cleanup on readonly fs


sad day.

is there any way to boot into a recovery mode...perhaps with an f6 option?

i have a Dell Inspiron 9300

---

### Post by justsomedude on 2008-09-25
Maybe this helps:

[http://www.gossamer-threads.com/lists/linux/kernel/973369](http://www.gossamer-threads.com/lists/linux/kernel/973369)

---

### Post by Pipey on 2008-09-25
> **justsomedude said:**
> Maybe this helps:

[http://www.gossamer-threads.com/lists/linux/kernel/973369](http://www.gossamer-threads.com/lists/linux/kernel/973369)


this is definitely a move in the right direction.  thanks!

here's the original post from the forum:

[http://ubuntuforums.org/showthread.php?t=920192](http://ubuntuforums.org/showthread.php?t=920192)

---

### Post by Pipey on 2008-09-25
ok, i seem to have figured it out and posted in the other thread 

justsomedude:  find yourself in Chicago, and the beer's on me :guitar:

---

