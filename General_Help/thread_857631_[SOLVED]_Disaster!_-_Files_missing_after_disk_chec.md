---
title: "[SOLVED] Disaster! - Files missing after disk check"
date: 2008-07-12
forum: General Help
---

### Post by christianxxx on 2008-07-12
First time ever I'm really disapointed about Linux. Here's why:
I got a new mobile yesterday and copied all the pictures to my harddrive. This morning, my computer spontaniously rebooted and performed a disk check.
After that, all pictures from this year are missing. There's a few from last year remaining, but that's no help.
I even did a "locate *.jpg" to see if I could find them somewhere else on the disk, but no luck.
I didn't really see all of the disk check process, but I remember it deleting some inodes or something.

Am I screwed or is there anything else I could do? I would stretch really far to get those pictures back.

---

### Post by christianxxx on 2008-07-30
*bump*

---

### Post by cdtech on 2008-07-30
You said it did a reboot on it's own?

Have you checked your log files to see what happened for sure?

**P.S.**
If you bump your threads some will think they are answered.

---

### Post by unoodles on 2008-07-30
Check /lost+found. You'll need to be root.

---

### Post by christianxxx on 2008-07-30
Bumped because it was 2 weeks without replies. Maybe I'm impatient? :)
I'm clueless to which logfiles to check. Hope to get a little assistance on that. 
It spontaniously rebooted, or more like reset. 
Checked lost+found, but it was empty. Does it empty on it's own, or would they be there even after all this time? 

Still hoping for some solution...

---

### Post by cdtech on 2008-07-30
Honestly I have not heard of such a disaster. I wish I could be of more help. Be patient though maybe someone will come up with a reason for this.

---

### Post by christianxxx on 2008-08-11
This has been sort of solved. Be sheer coincidence, I discovered a package called testdisk in the repositories. This contains a utility called photorec, which could scan my disk searching for deleted files. Maybe I should have read a little more about it before I attempted a recovery, as I recovered A LOT OF FILES.
So after hours of browsing the disk and internet, I have now copied all pictured to a folder. For some very strange reason, there are no large files, which is peculiar because most of the files I lost where pictures taken at a resolution of 5 megapixels.
Anyways, this tool is probably as close as I'll ever get recovery unless I cough up some £3000++ for a professional recovery job.
There's also a tool called recoverjpeg, but it really didn't do anything for me. 

With regards to the crash itself, we have deduced that the computer must have some faulty hardware. Might be the harddisk, though SMART hasn't given any warnings.

For any other lost souls, there's a whole section on data recovery on the ubuntu documentation, [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

For me, this is case closed. Now I've got to sort out the 30000 pictures and see what can be used...

---

