---
title: "Howto write filenames with non-english characters in NTFS USB drives"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by glantucan on 2008-04-21
[INDENT]:-\"[/INDENT]
**The problem:**
Perhaps it's not so important for you, but I get a lot of files with filenames in spanish, which involves some characters like ñ, or á, é, ... ü, etc, on them.

Since I use ubuntu (either feisty, gutsy or hardy beta) with KDE this means a problem when I want to back them up in my external hard drive. 
When I try to copy or create files with filenames like "InformaciónPersonal.txt" (Note the accented ó) KDE says  I don't have write permissions on this drive.

[INDENT] ](*,)[/INDENT]
 But I can write other files without these characters with no problem.

 
 [-X
What's the problem man?

[INDENT]:shock: [/INDENT]
 **The solution:** 
Create this script on /sbin (I named it ntfs-3g-es because it's for spanish filenames):

```

sudo pico ntfs-3g-es

```
```
#!/bin/bash
/bin/ntfs-3g -o locale=es_ES.UTF-8 $1 $2
# Change es_ES.UTF-8 by the locale you want to use
```
Make it executable
```
sudo chmod +x /sbin/ntfs-3g-es
```
Remember to change the script name on this code if you used another one. 
Then redirect the proper symlinks to it.
```

sudo ln -s -i /sbin/ntfs-3g-es /sbin/mount.ntfs-3g
sudo ln -s -i /sbin/ntfs-3g-es /sbin/mount.ntfs
 
```

See wether the symlinks are correct or not, you should get something like this:
```
ls -l /sbin/mount.ntfs*
lrwxrwxrwx 1 root root 19 2008-04-21 18:01 /sbin/mount.ntfs -> /sbin/ntfs-3g-es
lrwxrwxrwx 1 root root 16 2008-04-21 18:05 /sbin/mount.ntfs-3g -> /sbin/ntfs-3g-es

```
\\:D/
If for some reason you want to go back to the default configuration you just have to type:
```
sudo ln -s -i /usr/bin/ntfs-3g /sbin/mount.ntfs-3g
sudo ln -s -i  /usr/bin/ntfs-3g /sbin/mount.ntfs
```

Now, everything should work, and any worries about loosing your work be vanished

[INDENT] :-\"[/INDENT]
By the way I tested this with no issues on Feisty, Gutsy and Hardy.

That's all folks. 

Any suggestions/improvements will be appreciated

=;
**Some explanations **(read them if you are really bored):-#:
I did search the ubuntu forums hardly without result. Perhaps it's a question of finding the right words for the search, cause I found a lot of info on other different problems with NTFS hard drives. 
In fact, I had a hard time finding the words for the title of this thread. If the information I provide is duplicated somewhere else I sincerely apologize.
I don't exactly understand the origin of the problem neither why it is a KDE problem, but this explanation found in [archlinux WIKI]("http://wiki.archlinux.org/index.php/HAL") should help curious and educated people:
> [...] If you use KDE, you may have problem with filenames containing non-latin characters. This happens because kde's mounthelper is not parsing correctly the policies and locale option [...]
So they said there is a workaround that makes it work (follow the link above). My proposal is a slightly modified version of their solution which preserves the default symlinks (though pointing to the script) instead of overwriting them with it. I do it so because I need to remember they where symlinks and not scripts.

---

