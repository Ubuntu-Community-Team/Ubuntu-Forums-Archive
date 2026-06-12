---
title: "[SOLVED] Using 'cat' and 'split'"
date: 2008-07-28
forum: General Help
---

### Post by voteforpedro36 on 2008-07-28
I have just a small question: I'm making a backup of a folder while I reinstall something (Ubuntu as it looks right now), the rest of the files I want are small enough I just move them to Shared Documents on the Windows computer with ease. So I make an archive (.tar) of this folder, and use the command 'split' to split it into 6 different 500MB files. Now, as I understand it, if my folder was my music folder (it was), and the .tar was named music.tar, and my files are music_aa and so on, running 'cat music_a* > music.tar' should put it back into the tar file so I can unpack it and everything should be fine. Will this be the case if I move all these files to another computer while I install and back, seperating these files as I go? By that I mean I will move some of these to the shared folder of Windows, some by USB to a different computer, etc. But as long as I end up with all 6 files in the same folder on the new install, 'cat' will work, right? Sorry for the long post, but I want to be sure that it will.

PS: If you have a better backup idea (without buying an external harddrive), do say something.

---

### Post by dark_phantom on 2008-07-28
You can get an 8 gig flash drive cheap, but I think it will work by what you've describe.  Is this on the same pc or separate pcs?

---

### Post by RealPSL on 2008-07-28
I do not think split was meant for binary files. You are better of zipping your directories and using zipsplit to break it up. What ever you decide to do please make sure you test the recombination process on the target side before destroying the source data.

---

### Post by ghostdog74 on 2008-07-28
you don't cat a file into an existing tar. You update it using tar with the "u" option. Also split can split a binary file.

---

### Post by voteforpedro36 on 2008-07-29
> **dark_phantom said:**
> You can get an 8 gig flash drive cheap, but I think it will work by what you've describe.  Is this on the same pc or separate pcs?

I'll be moving the pieces to a different PC, but back to the same one after the reformat.

> **RealPSL said:**
> I do not think split was meant for binary files. You are better of zipping your directories and using zipsplit to break it up. What ever you decide to do please make sure you test the recombination process on the target side before destroying the source data.

I've tested it a couple times now, it seems to work. I'll use zipsplit too though, can't hurt to take a little more time then have 2 backups, right?
EDIT: So if I'm right, my command to zip it all up would be *zip -r backup.zip ~/Music*? 


> **ghostdog74 said:**
> you don't cat a file into an existing tar. You update it using tar with the "u" option. Also split can split a binary file.

Well, the tar won't be there when I want to cat the files. Or maybe I misunderstand you.

---

### Post by jtniehof on 2008-07-29
You could use a [multi-volume TAR](http://www.gnu.org/software/tar/manual/tar.html#SEC155). Note that the manual is pretty tape-specific...to make files of a specific size, use the -L option. Then there's a lot of detail on that page on how to specify the filename of the next file in the set.

Your split/cat procedure should work fine, though. I'd use cfv or a similar utility to verify that nothing went wrong in the transfer.

---

### Post by voteforpedro36 on 2008-07-29
> **jtniehof said:**
> You could use a [multi-volume TAR](http://www.gnu.org/software/tar/manual/tar.html#SEC155). Note that the manual is pretty tape-specific...to make files of a specific size, use the -L option. Then there's a lot of detail on that page on how to specify the filename of the next file in the set.

Your split/cat procedure should work fine, though. I'd use cfv or a similar utility to verify that nothing went wrong in the transfer.

Thanks, I'm installing cfv right now, I'll read the man page, test the tar one more time, then get on with it.

EDIT: Or maybe somebody could help with the usage of cfv? Turns out it's a bit confusing.

---

### Post by jtniehof on 2008-07-29
> **voteforpedro36 said:**
> EDIT: Or maybe somebody could help with the usage of cfv? Turns out it's a bit confusing.
man cfv

Seriously, to make the checksum file:
cd /the/directory/I/want/to/back/up/
cfv -rr -t md5 -f ~/checksum.md5

Then move checksum.md5 over to the other machine (scp, flash drive, whatever) and drop is in your home directory
cd /the/directory/I/put/it/all/in/
cfv -f ~/checksum.md5

---

### Post by voteforpedro36 on 2008-07-30
Finished now. It worked. I'll mark the thread solved just so anyone that might search for it will know it worked just fine.

---

