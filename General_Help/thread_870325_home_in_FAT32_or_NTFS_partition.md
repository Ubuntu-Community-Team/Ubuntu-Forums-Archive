---
title: "/home in FAT32 or NTFS partition"
date: 2008-07-25
forum: General Help
---

### Post by LIGC on 2008-07-25
Hi everyone, I'm planning on dual booting vista and hardy, and instead of having a user folder for each operating system, I was thinking of moving the vista user folder onto a different partition, either FAT32 or NTFS depending on what would work, and set that partition also as my ubuntu home directory.  I found how to move the directory in vista, but before I do the dual boot, does anyone know of any complications I could see?  Any comments would be appreciated.

---

### Post by ajgreeny on 2008-07-25
Bad move, I think.  It may work in theory, but I believe you will find that there is no-one who would recommend this file system for your /home partition.  I suspect others with more know-how will tell you why, but, I'm afraid I don't know enough.

---

### Post by coffeecat on 2008-07-25
It's not a good idea to have the whole of /home in a fat32 or NTFS partition because those two Windows filesystems don't support Linux permissions. Also, the /home folder has many hidden files and folders (these have a leading '.') for configuration and I don't know what effect this would have in Vista, or whether Visat would interfere with these..

But what I do is to have a separate NTFS partition for data and set up symlinks from my /home in Linux and whatever the equivalent is in Windows (links? shortcuts? :? ). So - say I have a 'Music' folder in my NTFS data partition, then I create a symlink called 'Music' in my Linux home and a link called - yes, you've guessed it - 'Music' in Windows My Documents. (I'm using XP.) In fact I also multiboot several Linux distros, so I do the same in each. Whichever distro/OS I'm in I can access the same files from my home folder by double-clicking on the symlinks (which look like folders with bendy arrows in Linux).

Easy peasy. :wink:

---

### Post by Vivaldi Gloria on 2008-07-25
Windows has no problems with ext2/3 partitions after you install this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by damis648 on 2008-07-25
> **Vivaldi Gloria said:**
> Windows has no problems with ext2/3 partitions after you install this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I would **strongly** recommend against this. This driver is still in beta and has corrupted my Ext3 filesystem twice.

---

### Post by coffeecat on 2008-07-25
> **Vivaldi Gloria said:**
> Windows has no problems with ext2/3 partitions after you install this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Windows may have no problems, but I'm afraid ext3 partitions can after Windows has been rampaging around inside them. I have to agree with the previous poster.

---

### Post by Vivaldi Gloria on 2008-07-25
> **damis648 said:**
> I would **strongly** recommend against this. This driver is still in beta and has corrupted my Ext3 filesystem twice.

If you guys have negative experiences with it then of course I don't recommend it anymore. 

But it is not beta anymore. I am curious if you used it lately?

---

### Post by Oldsoldier2003 on 2008-07-25
> **ajgreeny said:**
> Bad move, I think.  It may work in theory, but I believe you will find that there is no-one who would recommend this file system for your /home partition.  I suspect others with more know-how will tell you why, but, I'm afraid I don't know enough.

Extremely bad move. It does NOT work. If you move /home to a NTFS partition you will not be able to log in.

@coffecat a NTFS partition for media and files you want to share between windows and Linux is a good idea. It works real well. Until I went completely windows free I used one with no issues.

---

### Post by LIGC on 2008-07-25
thanks for the responses everyone, I'll do the symlink approach for my data.  i had a notion permissions might be a problem, but didn't know how severe :)

---

### Post by victorhugo289 on 2011-03-19
I know this thread is quite old but as I was reading I was thinking "What did I do?!", because I have a FAT 32 partition that I use as "Home", (but wait!, it's not home!), I had just put the My Documents folder and linked the specified folders Music/Documents/Videos in Ubuntu, so I just discovered that /Home is actually on the root partition.... whew!

For a moment there I thought having "My Documents" accessible from Ubuntu meant having your /Home folder in there as well, not so, thanks a lot. I made not bad move then.
It's good to know, now, although I was indeed going to do a very bad move and I never cared to read this information first!

---

