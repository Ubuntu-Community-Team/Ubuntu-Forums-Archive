---
title: "Ubuntu load in trouble without CD rom"
date: 2008-07-30
forum: General Help
---

### Post by tejaka on 2008-07-30
Hello

I have installed both Ubuntu and win XP on a single IDE. Win loads fine all the time but when I remove DVD rom away from the PC, Ubuntu try to load and finally ends to a command prompt screen and don't log into ubuntu screen.

any idea how to avoid this?

Thanks in advance.

---

### Post by Potatoj316 on 2008-07-30
if I understand you right than this is your problem:
you have windows and ubuntu on your computer.  they both work fine.  If you take your DVD drive out of your computer than ubuntu will no longer boot but windows will.  am I getting this right?

if so could you post the output of this command
```
cat /etc/fstab
```

---

### Post by tejaka on 2008-07-30
yes you got it right...

plz give me a min to put that in here...

---

### Post by tejaka on 2008-07-30
it goes to something called Debian built is shell...

when i put that in there, it said there is no such a location...

now i'm going to put Rom back in give u the result of Ubuntu terminal.

---

### Post by tejaka on 2008-07-30
This is it...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=e954db9a-19fa-46ed-b92b-d4a8d1e67a2d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=2b512949-264a-4d79-ac17-4c61e90a8f4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

any idea?

---

### Post by Potatoj316 on 2008-07-30
i think if you were to put a # infront of this line
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

to make it look like this
```
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

to edit run this command
```
gksudo gedit /etc/fstab
```

---

### Post by qotsa13 on 2008-07-30
hey, im having a similar problem. i bought the CD with the LINUX STARTER PACK.

sometimes when i boot up without the cd i get to the login screen however no unsername/password entry boxes appear - so the screen is just beige.

---

### Post by tejaka on 2008-07-30
> **Potatoj316 said:**
> i think if you were to put a # infront of this line
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

to make it look like this
```
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

to edit run this command
```
gksudo gedit /etc/fstab
```

is that # doing not evaluating that line, eh?...

---

### Post by tejaka on 2008-07-30
i did that, but till yet the problem is same :-?....

---

