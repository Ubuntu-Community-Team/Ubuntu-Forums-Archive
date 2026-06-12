---
title: "Is there a better way to transfer your data safely?"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by learningcurb on 2009-05-15
So I am trying to transfer my data from Windows to Ubuntu (and also from a Mac to Ubuntu)... and I read this:

"After you have made a copy of your files, it is very important to test the files to ensure that they have been copied successfully. If you have many files, at least check the most important files and randomly check other files where possible. This will help to protect you from data loss."
[https://help.ubuntu.com/9.04/switching/preparing-storage.html](https://help.ubuntu.com/9.04/switching/preparing-storage.html)

Is there a better way to do this?  While this is pretty much what I've done with my data in the past, it is pretty tedious and you can never be quite sure that you've checked thoroughly enough.  After all this is Linux so there must be a better way right? :)  I'm aware that there are tools that can checksum and run diffs between files, but I'm not sure how to use them to properly verify several hundred gigs of mixed data.

---

### Post by Anthon on 2009-05-15
if you use md5sum to generate checksums:
  cd windows_dir
  find . -type f -print0 | xargs -0 md5sum > /var/tmp/1.chk
you can then 
  cd linux_dir
  md5sum -c /var/tmp/1.chk
assuming that the files are in a similar directory hierarchy

---

### Post by learningcurb on 2009-05-15
Awesome, thanks for the tip!  This is exactly the type of script I wanted to try.  By the way how would it be done with SHA1?  Can it be done with the openssl program as well?

I also tried using [Back in Time]("http://backintime.le-web.org/") to back up my data and run a diff with rsync, which only took about 5-10 minutes.  md5sum took about an hour and a half in comparison but perhaps it is more thorough.  In any case, a second level of verification is nice to have.  It looks like the commandline that Back in Time uses is:

rsync -aEAX -i --dry-run --chmod=Fa-w,D+w --whole-file --delete --include=/media/target-drive

Any idea how this compares in effectiveness to md5sum?  I've got to wonder if it's so easy to add a md5 checksum to your backups why more backup programs or scripts don't integrate this feature in.  It does take a fair amount of time, but it does seem like a worthwhile step for verifying the integrity of your data and it's backups.

---

### Post by Anthon on 2009-05-15
Thanks for the reply, I am glad that works for you.

sha1sum has the same -c option (probably on purpose. So in these two commandlines you can just replace md5sum with sha1sum (you can try sha1sum/md5sum --help to see the options). A brief glance at the man page of openssl did reveal it is not a drop in replacement like sha1.
I don't think you need the extra bits of sha224 or higher. I know sha1 can be forged but for checking if a copy has no flipped bits sha1 is still good.

I do not know what rsync does to compare the files, but i do know it does this in parallel on the source and the destination, so that should help. It might also be more efficient in reading multiple files and/or larger files. That is a big speed difference. However if you can automate that, you probably do not care to much if you get an email in the morning telling you whether things were copied ok or not.

---

