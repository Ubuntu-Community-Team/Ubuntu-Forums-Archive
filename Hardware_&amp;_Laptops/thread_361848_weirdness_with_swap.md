---
title: "weirdness with swap"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by clifton on 2007-02-14
I can't get my laptop to use swap.  If I run "top" after logging on, I get 0K swap, 0K used.  

If I type "swapon -s" I get nothing.

Here's my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=e765bb7f-e897-447a-8626-e9512fca59c7 / ext3 defaults,errors=remount-ro 0 
1
# /dev/hda7 -- converted during upgrade to edgy
UUID=d94c2368-a2f9-11d8-8f66-e75dbf4ceaf0 /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=B2242F1D242EE457 /media/hda1 ntfs nls=utf8,umask=0222 0    0
# /dev/hda6 -- converted during upgrade to edgy
UUID=995dd941-80a5-4029-ab57-9038121f8eac none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


OK, this is where it gets strange.  If I type "swapon -a" I get:
swapon: cannot stat /dev/disk/by-uuid/995dd941-80a5-4029-ab57-9038121f8eac: No such file or directory

So now I type "ls -l /dev/disk/by-uuid/" and I get:
total 0
lrwxrwxrwx 1 root root 10 2007-02-14 12:56 0a30054a-3b4a-4f6f-89e3-f61d3f77144c -> ../../hda6
lrwxrwxrwx 1 root root 10 2007-02-14 12:56 B2242F1D242EE457 -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-02-14 12:56 d94c2368-a2f9-11d8-8f66-e75dbf4ceaf0 -> ../../hda7
lrwxrwxrwx 1 root root 10 2007-02-14 12:56 e765bb7f-e897-447a-8626-e9512fca59c7 -> ../../hda5

Note that /etc/fstab has a different UUID for hda6.

Now I type swapon -U 0a30054a-3b4a-4f6f-89e3-f61d3f77144c and it seems to work.

I type "swapon -s" and now I get:
Filename                                Type            Size    Used    Priority
/dev/hda6                               partition       506004  0       -1


So I begin to congratulate myself, but then I type "top" and get:
Tasks: 144 total,   1 running, 142 sleeping,   0 stopped,   1 zombie
Cpu(s): 16.2%us,  0.3%sy,  0.0%ni, 83.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035652k total,   603188k used,   432464k free,    20468k buffers
Swap:   506004k total,        0k used,   506004k free,   288532k cached


No swap is used.  No matter how many programs I start, it makes no difference.

That's when I realize I'm noob out of his depth.

Help, please!

Clifton

---

### Post by Stephen Howard on 2007-02-15
UUID
UUID is terrible isn't it?  Horrible to read and it isn't integrated into the OS sufficiently that fstab will update the UUID number if the swap partition changes size.  I (and many others) delete the UUID stuff and just use the old format because UUID only becomes useful if you have a lot of plug-in USB HDs etc.

That said, you can edit your fstab so that hda6 has the proper UUID number.  There's also a command [FONT="Fixedsys"]uuidgen[/FONT] that will generate a new number when you change the partition size etc.

SWAP
Just because a system has access to a swap partition doesn't mean that the OS needs to use it.  Keep in mind that hard disk access is much slower than ram access, so the OS will do its best to use up available ram before it accesses swap.  Modern linux systems are a lot smarter with their memory management, so that they can avoid using swap space.  

The best way to see if swap is being seen by the system is to: [FONT="Fixedsys"]cat /proc/swaps[/FONT]   which shows where the operating system thinks swap is installed.

Another useful command for monitoring swap is:  [FONT="Fixedsys"]free -s 5[/FONT]   That command will show 5-second updates of the swap being used (type [FONT="Fixedsys"]man free[/FONT] for an explanation of the meaning/interpretation of the output.).

A way to test swap usage is to open and use as many memory-heavy apps as you can while watching the 'free' command - sooner or later you'll see the system start to use swap.

---

### Post by clifton on 2007-02-15
Thanks.  

I should have thought of editing /etc/fstab myself.

Now when I use "swapon -a", and then "cat /proc/swaps", I get:
[INDENT]Filename                                Type            Size    Used    Priority
/dev/hda6                               partition       506004  0       -1
[/INDENT]
But there are still two problems:  No matter how many programs I start, "free-s 5" shows that no swap is used.  And apparently hda6 (my swap partitition) has a different UUID each time I boot up, so I would have to edit /etc/fstab each time.

Any more ideas?

Clifton

---

### Post by Patrick K on 2007-02-15
You can fine the UUID number in device manager <advanced tab>.

---

### Post by Stephen Howard on 2007-02-15
I suspect that you're running into the bug reported and discussed [here]("https://launchpad.net/ubuntu/+source/util-linux/+bug/66637").

You can follow the fixes suggested in it, or take the shortcut and do the following:  delete the UUID field from the fstab swap entry.  Make it read as follows:

[INDENT][FONT="Fixedsys"]/dev/hda6 none swap sw 0 0[/FONT][/INDENT]

Also, if you use hibernation, then you'll need to add RESUME=/dev/hda6 to your grub boot command (see the above link for details).

As for whether swap is actually working, I think you can assume it is if the kernel lists it as being used (ie /proc/swaps etc).  A more formal test would involve writing a little script that loops indefinately while allocating a bit more memory.  Ultimately you'd see the swap partition being used.

---

