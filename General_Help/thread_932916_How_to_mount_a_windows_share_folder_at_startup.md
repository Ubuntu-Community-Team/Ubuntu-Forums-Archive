---
title: "How to mount a windows share folder at startup?"
date: 2008-09-28
forum: General Help
---

### Post by ablmf on 2008-09-28
Hi all,

As I have to use a windows share fold frequently, I added the following command to ".profile"

```
sudo mount -t cifs  //192.168.0.31/Software software -o user=worker,pass=xxxx

```

But it seems not work.  Any suggestion?

BTW : I can't use gnome "Ctrl+L" to reach the share folder——"smb://192.168.0.31/Software".  

It just told me "mount fail".  Where can I find any log to see what the reason?   

As I can use **smbclient** and **mount ** to reach it, I don't think I misspelled the path or password.

Thanks in advance! :D

---

### Post by olejorgen on 2008-09-29
You could try adding it to /etc/fstab. I'm not sure if this will work well if you network connection drops. It might hang your startup too. At least if you're disconnected.

Anyway: something like this:
```

//192.168.0.31/Software /full/path/software cifs user=worker,pass=xxxx 0 0

```

The .profile wont work because sudo can't ask you the password

---

### Post by TeXtonyx on 2008-09-29
There is a tool for automatically adding shares to fstab.
sudo apt-get install ntfs-config
sudo ntfs-config
You will be prompted to make names for the shares.
If you use /menu choice, the shares appear on the desktop, but with /mnt, not so.

---

### Post by Mia_tech on 2008-09-29
well, I think it's always good knowing how to do things, in his case the problem was he was missing the mount point

---

### Post by Ms_Angel_D on 2008-09-29
I have written a blog post on things I do to my clean installs of Ubuntu, Part of that includes setting up my windows shares to mount automatically at boot the post is [HERE]("http://www.thedallemagnes.info/index.php?option=com_content&task=view&id=203&Itemid=1"). Take a look at steps 5 and 6.

Angel

---

### Post by ablmf on 2008-10-03
It works, thanks a lot! :o

> **MetalHellsAngel said:**
> I have written a blog post on things I do to my clean installs of Ubuntu, Part of that includes setting up my windows shares to mount automatically at boot the post is [HERE]("http://www.thedallemagnes.info/index.php?option=com_content&task=view&id=203&Itemid=1"). Take a look at steps 5 and 6.

Angel

---

