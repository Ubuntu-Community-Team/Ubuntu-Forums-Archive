---
title: "Problem with Ubuntu and Windows XP. My Windows XP drive won't load anymore!"
date: 2008-10-11
forum: General Help
---

### Post by R0x0rb0x0r on 2008-10-11
I just installed Ubuntu 8.04 on my old 27 gig IDE drive, so I could leave my 250 Gig SATA Windows XP Drive intact.

The Ubuntu 8.04 Drive is IDE Slave, my LG DVD Writer is the IDE Master.

Whenever I boot up my Ubuntu Disk Drive, it boots up fine. In grub, it gives me the 3 options (Ubuntu, MemTest, and forgot the 3rd one), but when I attempt to load my Windows, I get:

"ERROR LOADING DISK. PRESS ENTER TO CONTINUE" or something.

When I press enter, it gives me the same error again. I can't view the Windows drive from my Ubuntu IDE Drive, it says "unable to mount location". So, I can't salvage my files from Windows.

I am not the greatest with computers, and I really have no idea what I did, but it's really annoying, and I think I'm in for a re-format tonight (losing my Games, Movies, TV Shows, Pictures, Documents, etc).

Does anyone here know how I can fix this problem? What I can do to make my Windows XP SATA Drive work, along with Ubuntu, or at least how to uninstall Ubuntu. I have tried 3 different forums for help, and was referred to here. I really don't want to format... HELP!

---

### Post by cariboo on 2008-10-11
Could you post the output of:

```
sudo fdisk -l
```

You will have to do this is a Applications-->Accessories--Terminal. We need to see this to see what your disk order is, so that we can help you boot back into windows again

Jim

---

