---
title: "Question on mounting..."
date: 2008-10-11
forum: General Help
---

### Post by XtremeGamer99 on 2008-10-11
I run a small file server in my home that hosts all my music and some video and photo collections. Currently, these things mount automatically via an fstab entry using sshfh. Any Windows computers on the network get the same thing through Samba.

I'm having a problem, though. Every time I copy new music to the server it keeps the permissions, which isn't working so well because when I browse the share on my laptop I'm not able to read the new files considering that I'm not the user who put it there (my desktop user). This isn't a problem with files added from Windows via Samba because I have it configured to set file permissions to 0777 when a new file is added. I would like to know how to do this with an fstab entry (mount it, and any files written to it, as 0777).

It's an ext3 mount, BTW. =)

Thanks!

---

### Post by spiderbatdad on 2008-10-11
check out [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
and ```
man mount
```paying attention to uid, gid, fmask, dmask and umask.

---

### Post by XtremeGamer99 on 2008-10-11
The link you gave is very cluttered, and I can't seem to find my way through it. And I've checked the man pages, but I can't seem to find anything. I did think of umask, but the description of man pages can be so cryptic. I'm still looking for an answer...

---

### Post by Julius1988 on 2008-10-12
try
```

chmod -R 755 <name of shared folder>

```

---

### Post by XtremeGamer99 on 2008-10-12
I already do that, that's the problem. I need a way for the files to automatically be assigned those permissions upon copying to the mount.

---

### Post by earthpigg on 2008-10-12
> **XtremeGamer99 said:**
> I already do that, that's the problem. I need a way for the files to automatically be assigned those permissions upon copying to the mount.


hmmm... what about an scheduled script on the file server that runs once an hour and, using chmod, sets the permissions?

---

### Post by vanadium on 2008-10-12
You cannot determine default permissions at mounting time for ext3 volumes. You can for systems that do not support permissions.

The default permissions are determined by the current umask. Rather than changing permissions after the copying, you can change default permissions before copying using the umask command.

It is a bit a security issue: linux forces you to think if you want to open all permissions. You need to tell explicitly that the next files you are going to create should have all permissions open. You still can include the umask command in .bashrc, so that the default permissions of 777 are automatically in effect. This is a security hazard because you might not really want all your files to be created with all permissions open by default.

---

### Post by paris_alex on 2008-10-13
there's not enough information to diagnose your problem. So, this is a long shot, but try including the uid= and gid= in your fstab file with your username. Good luck!

---

### Post by XtremeGamer99 on 2008-10-14
> **earthpigg said:**
> hmmm... what about an scheduled script on the file server that runs once an hour and, using chmod, sets the permissions?

That's a clever way, but I immediately see a problem with it. The main reason why I am doing this is because of my music collection. Lets say I rip a CD from my laptop (running Ubuntu) to the public share. 10 minutes later I need to leave the house, so I hop onto my desktop (Debian) real quick and copy those files to my music player. The files are shown to exist, but since my desktop computer is not the owner of the files and can't read them then they are copied as 0KB files. Most of the time, in my rush to get out, I don't notice until I'm out the door and try to play the music in my car only to find that the music isn't playing because there's nothing to read. I could set it to run every 5 minutes or something...

> **vanadium said:**
> You cannot determine default permissions at mounting time for ext3 volumes. You can for systems that do not support permissions.

The default permissions are determined by the current umask. Rather than changing permissions after the copying, you can change default permissions before copying using the umask command.

It is a bit a security issue: linux forces you to think if you want to open all permissions. You need to tell explicitly that the next files you are going to create should have all permissions open. You still can include the umask command in .bashrc, so that the default permissions of 777 are automatically in effect. This is a security hazard because you might not really want all your files to be created with all permissions open by default.

Could you go a little more in-depth about using the umask command to change default permissions before copying? Is it something that I will have to run manually every time I add things to the mounted share or will it be automatic.

I may just reformat it into a NTFS filesystem if it's going to give me this much trouble. It's supposed to be a public share that anyone connected to out network is able to, at the very least, read, and the fact that I currently can't add files to the share without having to worry about permissions.

---

### Post by vanadium on 2008-10-14
It is not trouble. It is security and linux is designed with some security in mind. You can make the system more convenient, but less secure if you want.

One part of security is to control (i.e. *you* control) permissions. 

The correct way to handle this (i.e. no security compromise) is to change the permissions of your files as you create or copy them. You can change the permissions locally and they will be preserved during the copy on decent file systems that support linux permissions. Alternatively, you can change the permissions on the server. This is the only guarantee that only the files you want to be public are public.

To make life easier, but less secure, you can instruct Linux to grant all permissions to new files by default (*new* files, existing files keep their permissions). This can be done by setting the umask

```

umask 0000

```

will cause newly created files to have all permissions open by default.

You can execute the umask command automatically, e.g. by including the command in your .bashrc file. This, if you do not see any concern in having all permissions open by default. This is less secure.

Anyway, I am surprised that you can not even read the files. Default permissions of Ubuntu are 755, which means that you should have by default reading access for files you do not own. Again, check the umask command to see the default permissions on your system. On Ubuntu, it is 0022 by default (meaning files get permissions 755).

---

