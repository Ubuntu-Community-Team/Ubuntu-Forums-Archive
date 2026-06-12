---
title: "can't get access to a secondary hdd after installing ubuntu"
date: 2014-07-12
forum: Hardware
---

### Post by ran2 on 2014-07-12
hey everyone, i am a new user in ubuntu.

i have two hard drives in my computer. the primary is an ssd that the ubuntu operation system is running on it. it was my primary that windows was running on it as well.
my secondary is an hdd that i have on it all my movies, docs, pictures and more.
Since i installed the ubuntu i can't get an access to it and i am  getting an error. "Error mounting /dev/sdb2 at /media..."
after reading alot on the error and on ubuntu i understand that the problem is something about the shutdown in windows.
the problem is that i don't have windows on my computer any more so i can't go in to windows and do a proper shutdown.

i hope the you can help me, tnx!

i have added a picture of the error/

---

### Post by yancek on 2014-07-12
You haven't indicated which windows you are running so this is just guessing.  Guessing that you have windows8 or 8.1.  If that is the case, you need to go into the BIOS immediately on booting and try to disable Fastboot.  It may not be 'Fastboot', something similar.  I don't know if that will work but it is easy enough to try and no harm done if it doesn't work.

---

### Post by ran2 on 2014-07-12
> **yancek said:**
> You haven't indicated which windows you are running so this is just guessing.  Guessing that you have windows8 or 8.1.  If that is the case, you need to go into the BIOS immediately on booting and try to disable Fastboot.  It may not be 'Fastboot', something similar.  I don't know if that will work but it is easy enough to try and no harm done if it doesn't work.

hey, thank you for responding.

i tried that right now and still the same problem. any other ideas?

---

### Post by yancek on 2014-07-12
> i tried that right now and still the same problem. any other ideas? 		

Not really.  If you have a windows installation DVD, you might be able to run a filesystem check from it if it has a Repair option.  I don't really expect that to work and don't even know if that option is available.

---

### Post by ran2 on 2014-07-12
so there is no way??? 

:(

---

### Post by yancek on 2014-07-12
> so there is no way??? 

I didn't say that!  I've only used windows 8 in a virtual environment when it was in its testing stage and that was enough for me.  I read a post recently indicating that running chkdsk might be possible from either the windows installation DVD (if you have it?) or a recovery disk, I believe selecting the Repair option.  If you don't have either disk, you might ask a friend who has one to borrow it and that might work. I have no other suggestions as my use of w8 was very limited but, someone else here certainly has more knowledge about your problem.  You might also try going to a windows forum.

Out of curiosity, have you tried manually mounting sdb2 at a different mount point?  And what is on sdb1?

---

