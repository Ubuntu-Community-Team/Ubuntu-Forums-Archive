---
title: "Messed-up permissions in the $HOME directory: how to repair to default?"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Cubytus on 2009-05-23
Hi to all, 

This is a newbie-grade question, but still annoying to experience nonetheless.
I just moved to Ubuntu 9.04, but I guess this applies to any other Unices and Unix-likes.

The default install in Ubuntu is to put everything in the same partition, which is obviously undesirable when upgrade time comes. So since 7.10 that was on this computer, I set up a small partition for the OS, mounted as /, a very small partition for the swap, and a big partition for the data, mounted as /home.

With 9.04, I first set up a temporary administrator account that would be deleted later, as admin2, then I proceed to recreate the tarcum user that was there before, and logged out and back in.

I must have missed something because although I could enter the desktop, every file one it was marked as locked. Indeed, the command **ls -ahl** entered in the terminal confirmed that all these files were marked as pertaining to admin2 with permissions, I guess, 755 (readable but not editable to other people). 

I successively did **sudo chown tarcum -R ~** ; **sudo chgrp tarcum -R ~** ; **sudo chmod 644 -R ~**, then I logged out and back in.

Now, I get this error message (translated from French):
File $HOME/.dmrc has been ignored. This doesn't allow you to save session and default language. File should be owned by user and have 644 permissions. User directory must be owned by the user and must not be accessible in writing to other users.

I then went to the /home directory in the Terminal, and did (no -R here!) **sudo chmod 755 tarcum**.

The session does start and appears to run correctly, but I know that security issues are around the corner.

I admit, this is probably the worst method available to solve the problem since absolutely no distinction is made between ubuntu-read hidden files (."something"), but contrary to Mac OS X, I don't know of any utility that can repair permissions in one click in Ubuntu. Does such an utility exist? Or better yet, an assistant that would ask plain questions about wether I want to allow people and groups X to access folder Z?

Thanks for yur patience :)

---

### Post by albinootje on 2009-05-23
> **Cubytus said:**
> 
I successively did **sudo chown tarcum -R ~** ; **sudo chgrp tarcum -R ~** ; 

Good. 
For the record, you could have done this instead, saves you writing down, for next time :
```

sudo chown -R tarcum:tarcum /home/tarcum

```
> 
**sudo chmod 644 -R ~**, then I logged out and back in.

Unfortunately the "chmod 644 -R ~" is a huge mistake.

In Linux (and other Unix-alikes etc.) there's a big difference in the permissions of files and directories.

Changing permissions on a directory to 644 will lead to problems.

For a file 644 is good, because it means that the owner can read/write, the group can read, and the rest can read.
For a directory, having 644, it means that noone can "cd" (navigate) into it.

You need to solve this with the "find" and "chmod" commands combined.
```

cd /home/tarcum
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;

```
> 
Now, I get this error message (translated from French):
File $HOME/.dmrc has been ignored. 
This a FAQ (I don't remember the solution by heart), there are several threads about this :
[http://www.google.com/search?ie=UTF8&q=site%3Aubuntuforums.org+dmrc+ignored](http://www.google.com/search?ie=UTF8&q=site%3Aubuntuforums.org+dmrc+ignored)

---

### Post by Cubytus on 2009-05-23
> **albinootje said:**
> Good. 
For the record, you could have done this instead, saves you writing down, for next time :
```

sudo chown -R tarcum:tarcum /home/tarcum

```
Will try to remember that. However, as a Mac-user most often, I don't have to deal with the Terminal; there's also an GUI advanced option to set up the /Users folder on another drive if desired in OS X.

> For a file 644 is good, because it means that the owner can read/write, the group can read, and the rest can read.
For a directory, having 644, it means that noone can "cd" (navigate) into it.Up to now, I wanted that tarcum could obviously do anything he wants with his files, but to deny any other access to other users; no reading, either, because there can be private documents in the **~** folder.

Is there a way to default file permissions to 600 when they are created so no one excepot the creator can read or write them?

The "Public" folder is intended to be shared across the LAN with both read and write access, and the "Video" folder shared read-only; are these permissions set up in the OS or in Netatalk/Samba? 

If the **~** folder is inaccessible in read operations to other users, will they be able to still open the Public and Videos folders from the lan or by *cd*-ing directly to them?

> You need to solve this with the "find" and "chmod" commands combined.
```

cd /home/tarcum
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;

```Do this set the permissions/groups/owners correctly for every single file and folder, including system-created ones?

I applied these operations, and it kept on telling that access to .gvfs is denied.

I have a hard time conceiving that every file and folder in the ~ directory get the same permissions. Maybe it's subjective.

> This a FAQ (I don't remember the solution by heart), there are several threads about this :
[http://www.google.com/search?ie=UTF8&q=site%3Aubuntuforums.org+dmrc+ignored](http://www.google.com/search?ie=UTF8&q=site%3Aubuntuforums.org+dmrc+ignored)I'll check that..

---

### Post by ph1 on 2009-06-05
albinootje,

You, sir, have just saved my day.

I salute you.  Thanks very much for the solution--I did not know that directories and files needed different permissions.

Or that cp now has a permission-preserving option.  Will remember that in the future for this sort of thing.

---

### Post by albinootje on 2009-06-05
> **Cubytus said:**
> 
I applied these operations, and it kept on telling that access to .gvfs is denied.


That's normal, you can ignore it.

---

### Post by albinootje on 2009-06-05
> **ph1 said:**
> albinootje,

You, sir, have just saved my day.

I salute you.  Thanks very much for the solution--I did not know that directories and files needed different permissions.

Or that cp now has a permission-preserving option.  Will remember that in the future for this sort of thing.

Glad to hear you could use this information. :)

In my opinion the logic of chmod in Linux is a bit weird at first sight (e.g. that chmod 644 on directories will give serious problems, while chmod 644 on files is pretty normal), but we'll have to get used to it.

---

