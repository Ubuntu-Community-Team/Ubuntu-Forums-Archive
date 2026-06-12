---
title: "USB unable to mount"
date: 2013-04-08
forum: Hardware
---

### Post by jonoinfrance on 2013-04-08
Hi,

After transferring some files to my usb key the other day, I took it out without using the "eject" function and ever since it has been doing some strange things.

It had two partitions on it, one ntfs and one fat, the fat works fine, but the ntfs partition (which is the one I was transferring files to), gives me this error whenever I plug it in or try to access it:
Unable to mount key, Error mounting /dev/sdc2 at /media/jono/key
[...]
exited with non-zero exit status 13: Can only open dev/sdc2 as read only.

There is a lot more written, I will add if necessary.
Now, I guess that I have messed up the key, but since I didn't have anything important on it, I would like to reformat the whole key (both partitions) and merge them into one big partition.
The problem I am having is that fdisk won't reformat the key since it cannot be mounted. The second problem I am having is that both partitions are seperate, one is sdc1 and the other sdc2, so how can I tell fdisk to merge them?

Thanks in advance for any help ..

---

### Post by ajgreeny on 2013-04-08
If you have a windows machine to plug it into, windows will mount it properly.  Now remove it as you should have done last time and you should then be able to mount it automatically in Ubuntu.  This happens if ntfs partitions are not removed properly and the partition is left with an "in use" flag on it.  Windows ignores this flag, linux does not.

---

### Post by jonoinfrance on 2013-04-08
Hi, thanks for the answer. I do have a windows machine, but for some reason it cannot even see the partition (actually, it has never been able to see the second partition).
It is the same machine but I have both OS on it. I always thought that the other partition was just un a format that windows couldn't detect, as I could see and use the other one on Ubuntu, but since this problem I can't use it on either OS.

I seem to be in a bit of a pickle.

Is there any other way to remove the "in use" flag another way?

---

### Post by Bashing-om on 2013-04-08
jonoinfrance; Hi !

Not sure as I have never had an "NTFS" partitioned drive. But, might be worth a shot to see what ubuntu's partition editor can do in this situation. Gparted maybe able to (un)mount the partition (click on key symbol).
GParted is available on the liveCD, or whatever other medium you used to install ubuntu.[INDENT=4]
hope this helps

[/INDENT]

---

### Post by ajgreeny on 2013-04-09
Sorry, jonoinfrance, I forgot that windows can only ever see a single partition (presumably the first) on a USB memory stick or thumb drive.  That may explain why the windows machine is not helping in your situation.

---

### Post by jonoinfrance on 2013-04-09
I will try to see what gparted does, thanks :)

---

### Post by breezypt on 2013-04-09
You can try the 'Disk Utility' app, that may help..

---

