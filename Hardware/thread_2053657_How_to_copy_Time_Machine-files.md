---
title: "How to copy Time Machine-files"
date: 2012-09-05
forum: Hardware
---

### Post by esbenovich on 2012-09-05
I am in quite the pain here i hope you guys are the right to ask!

My external hard drive (WD Mybook 1TB) which i use for backups via Time Machine on my mac has gone partly out of function.

If i hook it up to a mac it will say: "The disk you inserted was not readable by this computer".
OS X Disk Utility cannot repair the drive nor do anything with it in fact (part from formatting).
I believe this problem began with a power outage - until then everything was working perfectly fine.

Now heres why i'm writing you guys:
If i hook the drive up to a computer running ubuntu (i've used 8.10 because i had a live-cd lying around) 
the system recognises it just fine and all my files seem to be intact.
Therefore i wanted to copy the files from the drive onto another so that i could format my backup-drive (hopefully getting it to work again!).

But I do not have permission to copy/move the backup files created by Time Machine from within Ubuntu.
I've tried the best i could to use the terminal with commands like chown, mv and cp (all with sudo as well) but with no luck.

Do you have any advice on how so save my files from the drive?

Also, GParted says that the 'DiskLabelType' is 'unrecognised' and the filesystem is unallocated.

I look forward to hearing from you!

Regards 
Esbenovich.

---

### Post by dgharmon on 2012-09-05
> **esbenovich said:**
> If i hook the drive up to a computer running ubuntu .. the system recognises it just fine and all my files seem to be intact.

You could try using the [DD]("http://www.thegeekstuff.com/2010/10/dd-command-examples/") utility ...

---

### Post by esbenovich on 2012-09-06
I currently don't have a second external hard drive with enough space to copy the 1TB-drive.
So is there some way of making the DD-command for a folder instead of an entire disk?

Also, the Time Machine files are owned by '501' and 'root'
Will the DD-command allow me to copy these files?

---

### Post by dgharmon on 2012-09-06
> **esbenovich said:**
> is there some way of making the DD-command for a folder instead of an entire disk?

"[dd a directory]("http://ubuntuforums.org/showthread.php?t=1245582")"

---

### Post by esbenovich on 2012-09-06
Thank you for the advice, but unfortunately the whole Time Machine-drive is read-only - so I cannot put the script on it..

Is there anything else i can do?

---

