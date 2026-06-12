---
title: "Can I still access my /home if I do this?"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by jimric on 2009-04-05
I have Ubuntu  8.10 installed on a Dell GX 270.

I have the OS installed on 1 hard drive and my /home is on another hard drive.
I was thinking about reinstalling ubuntu again and I am going to leave my /home drive intact.
After installing ubuntu can I still have access to my /home drive ?
Thx Jim

---

### Post by jordilin on 2009-04-05
Yes, when installing Ubuntu again mount your /home from that drive.

---

### Post by jimric on 2009-04-05
> **jordilin said:**
> Yes, when installing Ubuntu again mount your /home from that drive.
 This may sound dumb, how do you go about doing that?
I just don'nt want to lose all my data.

---

### Post by CyberMando on 2009-04-05
In the new install while partitioning disks it may be possible to tell the loader to use that partition as /home and not to reformat it. I have never done that and would be leary of it unles I tried it ona system I did not care about.

If you just partition and do not mount a partition at /home in the new install, once youboot into the new install youcan add a line to /etc/fstab that will mount your old partition at /home. If youdo not know the fstab syntax it would be best to copy the line out of your current /etc/fstab that mounts /home so you can use it in your new install.

---

### Post by jimric on 2009-04-05
> **CyberMando said:**
> In the new install while partitioning disks it may be possible to tell the loader to use that partition as /home and not to reformat it. I have never done that and would be leary of it unles I tried it ona system I did not care about.

If you just partition and do not mount a partition at /home in the new install, once youboot into the new install youcan add a line to /etc/fstab that will mount your old partition at /home. If youdo not know the fstab syntax it would be best to copy the line out of your current /etc/fstab that mounts /home so you can use it in your new install.

Thank you Cybermando I did what you said about copying my line in etc and it worked!!!!! you are awesome!!!
Lets see the Winblows people do that with their OS.
Jim

---

