---
title: "[SOLVED] Permissions and ownership problems"
date: 2008-11-14
forum: General Help
---

### Post by GamesForLinux on 2008-11-14
I dualboot Ubuntu 8.04 x64 and openSuse 10.3 x32 so I'll have an operating system to run those 32-bit applications that haven't been upgraded yet, like Amazon MP3 and Java.
While using openSuse, I decided I needed to access my Ubuntu partition. In Ubuntu, I have no problem mounting and reading the other partition. Unfortunately, openSuse does have problems.
I got it to mount the partition by giving it a label and setting the mount point to /mnt/ubuntu, but it gave me a "permission denied" error, so I did
```
chmod 666
``` and ```
chown james
```
Now, openSuse showed that I owned (but I couldn't see anywhere what permissions it had) the folder, but it still wouldn't let me read from it.

At this point, I rebooted into Ubuntu, and came across 3 errors. First, when it was booting, it said something along the lines of "the ubuntu partition doesn't match backup. Check forced." and then ran the disk check.
Next, when logging in, it came up with the error "Home directory isn't owned by you. This is dangerous and should be fixed" or something. I've had this problem before and fixed it.
Last, another error came up that said "Your session lasted less than 10 seconds. Try booting into safe mode to see if you can fix the error." (booting into safe mode didn't help. I didn't try safe terminal mode) The error message also said that the reason was because it couldn't create /home/james/Desktop, home/james/Documents, /home/james/Templates, etc...

So, how do I put permissions and ownership back the way they're supposed to be?
Also, if you help me get openSuse to read from the other partition, that would be nice to.
Thanks in advance!

---

### Post by taurus on 2008-11-14
Did you add an entry in /etc/fstab to mount your Ubuntu while you are in OpenSUSE?  Changing ownership and permission of your Ubuntu's root filesystem just because you couldn't access it is the worst mistake you could make.

---

### Post by GamesForLinux on 2008-11-14
I didn't manually add anything to the /etc/fstab, but in the partition tool, I did change the mount point via "fstab option" button.
Actually, my home directory is on a different partition than my root directory. The root, where Ubuntu is installed was never mounted under openSuse. The only folder I messed with permissions with was /home/james, but I did use the --recursively argument.

Ok, I logged into Ubuntu safe-mode terminal, and could change permissions /home back to 644, but chown james /home didn't fix the problem.

---

### Post by GamesForLinux on 2008-11-15
Forget it. After messing around in the terminal, I managed to finish off the usability of the partition, and am reinstalling Ubuntu.

---

