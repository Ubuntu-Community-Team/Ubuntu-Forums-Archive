---
title: "Ubuntu is making me feel retarded..."
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by apocalypse2012 on 2007-10-27
I know... Maybe its me... I am new to Ubuntu and Linux. And I am trying real hard.

I remember with the installer asked me to setup my user account name and password, but I do not remember anything about the root password. How do I identify my root password.

Why do I need it? I'm glad you asked.

My Nvidia Settings are not staying between sessions. I set up the Nvidia drivers with Envy. I try to save the configuration to the Xorg.conf file, but it spits out an error that says it can't save a backup of the file. I am assuming that means it failed the save entirely. 

So I am using Nautilus to browse to my X11 directory, and lo, there is an army of xorg.conf backup files. I assume that I want to delete them. No can do. I must be root.

Now I know that I could just open a terminal window type in 'sudo "whateverdeleteiscalledinlinux" ', but that's just so... DOS. So, do I need to log into Ununtu as the root user? or is there some special Desktop equivalent of Sudo?

---

### Post by taurus on 2007-10-27
You can only create and delete files in your own $HOME directory.  Anywhere else, you need to be root so you must use sudo.

Press <Alt>F2 and type 

```
gksudo nautilus
```
Now, you can delete whatever you want so be real careful with that.  Deleting wrong files could crash your machine.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by glosman15 on 2007-10-27
sudo rm "path to file you want to remove"

---

### Post by apocalypse2012 on 2007-10-27
Excellent. Thanks!

---

