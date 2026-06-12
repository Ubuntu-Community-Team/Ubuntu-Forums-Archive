---
title: "How to burn a CD (and DVD) despite bug #149076"
date: 2008-08-09
forum: General Help
---

### Post by editrix on 2008-08-09
This isn't my discovery, I'm just writing it up. Many, many thanks to mc4man for all his help.

1. Download and install Wine and ImgBurn. There's a tutorial for it here:

> How to get ImgBurn working on Ubuntu 7.10
[http://forum.imgburn.com/index.php?showtopic=5317](http://forum.imgburn.com/index.php?showtopic=5317)

(Note: I just installed Wine from the repository with apt-get--I'm on Hardy)

ImgBurn is not K3B, but it will do in a pinch. 

2, Follow the ImgBurn forum's excellent tutorials. The list is here:
[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

mc4man recommends configuring Wine to emulate Windows NT. Otherwise, the default settings for ImgBurn are good for most normal uses.

[COLOR="Red"]BIG FAT CAVEAT[/COLOR] I wasn't prepared for this, so just in case you aren't: ImgBurn spits the disk out before veryfying it. Don't touch it! The tray will close up and the verifying process begin--which may take longer than the burning process did.

[COLOR="Red"]Minor caveat[/COLOR] ImgBurn doesn't have the tolerance for oddball characters in filenames that Linux does. This is also true for directories. That is, even if the filenames themselves are okay, the directory name may not be. It will warn you that the "filename" can't contain (and then give you the list of characters). But it could be the directory that's the problem. Just rename it.

I still have very little experience of ImgBurn, but here's some testimonial:

[QUOTE=mc4man]For [burning DVDs] Imgburn has no equal, it always uses the proper filesystem ext.'s, allows/prompts you to set a disk label, sets and uses a proper sized buffer, ect., ect. ... as far as data dvd's I've tested imgburn created ones on xp, vista, linux, and 2 mac Os's and all were able to access the disk.[/QUOTE]

As well, you might want to look over the "what's new" section of the main Imgburn page. The last 3 or 4 releases will give you a good idea of its capabilities.

UPDATE: I have just received information on another workaround, which involves getting rid of buggy wodim and installing and using the original cdrecord. You might want to look at that solution, too: [https://bugs.launchpad.net/bugs/149076](https://bugs.launchpad.net/bugs/149076)

UPDATE 2: Just found this thread which I haven't tried, but it's very clear instructions on how to replace wodim with cdrecord: [http://ubuntuforums.org/showthread.php?p=5721644#post5721644](http://ubuntuforums.org/showthread.php?p=5721644#post5721644)

UDPATE 3: Some interesting discussion here: [http://ubuntuforums.org/showthread.php?t=851707](http://ubuntuforums.org/showthread.php?t=851707)

---

