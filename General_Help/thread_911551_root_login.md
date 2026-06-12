---
title: "root login"
date: 2008-09-05
forum: General Help
---

### Post by aaronbp0 on 2008-09-05
I'm running windows vista with ubuntu on an external hard drive, and accidentally messed up vista, so I need to back up my files before I reinstall vista. When I tried to mount my C drive in ubuntu, it said I couldn't because windows didn't shut down successfully. I tried to force it in the terminal, but it said "only root can do that."
How can I log in as root, or if there's another way to mount, what is it?

---

### Post by Joeb454 on 2008-09-05
use sudo.

E.g. enter ```
sudo <your command here>
```

Naturally replace the part after sudo with whatever command you want to run

---

### Post by mb_webguy on 2008-09-05
Unlike other versions of Linux, Ubuntu doesn't allow you to login as root for security reasons.  Instead, if you need to issue a command using root privileges, precede the command with sudo (or gksu for a GUI application).  You will be prompted to enter your login password (which will no appear on the screen as you type it, so just hit enter when you're done).

---

### Post by rihannaisco on 2008-09-05
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by LateNiteTV on 2008-09-05
you can enable the root acct:
```
sudo passwd root
```

---

### Post by knutschr on 2008-09-05
You should never do this.
You can 'easaly' end up having screwed up your whole installation.
Use sudo, or gksu (for GUI's)
There is a reason for this, I hope you know :-)
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by aaronbp0 on 2008-09-05
Hmm when I tried to use "sudo mount -t ntfs-3g /dev/sda2/media/OS -o force" it just gives me the mount usage instructions. If I try to do it without sudo, though, it says "only root can do that."

---

### Post by knutschr on 2008-09-05
Have you done
```
gksu nautilus
``` ?
May be it will appear there?

---

### Post by aaronbp0 on 2008-09-05
I can see it even in the regular file browser, I just can't force it to mount in the regular browser or nautilus.

---

