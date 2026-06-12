---
title: "Reformatted home directory"
date: 2008-08-25
forum: General Help
---

### Post by keaton on 2008-08-25
Hello! I have a bit of a problem. I'm running into a wall searching Google as well. I decided that it was time to go back to a dual-boot environment after two years of exclusive Kubuntu use. I installed Windows on my second hard drive- the one I thought was empty. I then remembered my *home* directory was on that one. Oops. Is there any way to get **any** of my data back? The filesystem is ext3, and I used the quick NTFS format. Maybe just format again as ext3? Thanks in advance!

---

### Post by Ocxic on 2008-08-25
nope sorry, your data is gone. must be more careful next time.

---

### Post by ByteJuggler on 2008-08-25
You can try a file carver tool like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" or "[foremost]("http://foremost.sourceforge.net/")" from a rescue liveCD (like [TRK]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") or [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/")), which recovers files based on internal structure, not relying on filesystem.  You may also try a more conventional unformat/recovery tool.  But, the first thing to do, is to stop doing anything that writes to your disk.  Ideally you'll make a clone image/copy of the disk and then try to recovery your files from that...

---

### Post by keaton on 2008-08-25
Hey, thanks! I really should have backed up my data, but I was sure I had my home folder partitioned elsewhere. I used an unattended install, so Windows is now on there, but I'm going from a live CD. (enet wasn't detected in Windows? *Unbelievable!*)

---

### Post by ByteJuggler on 2008-08-26
> **keaton said:**
> Hey, thanks! I really should have backed up my data, but I was sure I had my home folder partitioned elsewhere. I used an unattended install, so Windows is now on there, but I'm going from a live CD. (enet wasn't detected in Windows? *Unbelievable!*)

Unfortunately, if you've actually installed Windows then the chances of recovery obviously is reduced, since chances are that a large part of your files would've been overwritten by Windows' files.

---

