---
title: "[SOLVED] I locked myself out"
date: 2008-09-13
forum: General Help
---

### Post by njd4k on 2008-09-13
I downloaded the Songbird player (getsongbird.com) and unpacked it, then tried to move it into my /etc/ directory with the rest of the programs. I didn't have write permission for /etc/, and for some reason I couldn't copy from the command line using sudo... so I used sudo chmod to set the permissions on etc to 0777, then tried to put it back -- without looking up the appropriate permission code. I typed sudo chmod 0000. Unfortunately, that was the wrong choice. Trying to undo the problem, or work around it, has been impossible since the root user is apparently in the /etc/ folder.

```
I have no name!@nic-laptop:/$ mkdir etc2
mkdir: cannot create directory `etc2': Permission denied
I have no name!@nic-laptop:/$ sudo mkdir etc2
sudo: can't open /etc/sudoers: Permission denied
```

So, I'm an idiot.

How can I fix this?

---

### Post by bodhi.zazen on 2008-09-13
Easiest way to fix this is to re-install.

You should not change ownership or permissions of system files like this.

use sudo or gksu (gksu nautilus).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by njd4k on 2008-09-13
Thanks for your quick replay. But may I just ask what you mean when you say

> use sudo or gksu (gksu nautilus).

I haven't been able to use sudo with the directory locked. If you mean I should used this instead of changing permissions, that was exactly what I tried to do before I changed the permissions. Or is there a third meaning?

Looks like I'll have to reinstall...



> **bodhi.zazen said:**
> Easiest way to fix this is to re-install.

You should not change ownership or permissions of system files like this.

use sudo or gksu (gksu nautilus).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2008-09-13
use sudo and / or gksu rather then changing permissions.

---

### Post by sisco311 on 2008-09-13
> **njd4k said:**
> I downloaded the Songbird player (getsongbird.com) and unpacked it, then tried to move it into my /etc/ directory with the rest of the programs. I didn't have write permission for /etc/, and for some reason I couldn't copy from the command line using sudo... so I used sudo chmod to set the permissions on etc to 0777, then tried to put it back -- without looking up the appropriate permission code. I typed sudo chmod 0000. Unfortunately, that was the wrong choice. Trying to undo the problem, or work around it, has been impossible since the root user is apparently in the /etc/ folder.

```
I have no name!@nic-laptop:/$ mkdir etc2
mkdir: cannot create directory `etc2': Permission denied
I have no name!@nic-laptop:/$ sudo mkdir etc2
sudo: can't open /etc/sudoers: Permission denied
```So, I'm an idiot.

How can I fix this?

Did you change the permissions recursively?

If not, boot in recovery mode or with the live cd and change the permissions back:
```
chmod 0755 /etc
```

---

### Post by mb_webguy on 2008-09-13
Installed programs go in /usr or /usr/local, not /etc.  Executables go in /usr/bin or /usr/local/bin, and support files go in /usr/share or /usr/local/share.

/etc is for system-wide configuration files.  You really shouldn't mess with anything in /etc unless you really know what you're doing.

[Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by njd4k on 2008-09-16
I reinstalled; I had been thinking about switching to 32-bit anyway, and this stupid error was enough to make me do it. 

Thankfully -- I post this for any other newbies reading -- I didn't have to reformat and wipe the partition. I was able instead to just install to the same boot point. My files and some of my settings were preserved.

Thanks to all who responded. I'm marking this as solved.

---

