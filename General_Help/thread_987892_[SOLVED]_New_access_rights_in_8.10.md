---
title: "[SOLVED] New access rights in 8.10?"
date: 2008-11-20
forum: General Help
---

### Post by Niniel on 2008-11-20
Hello,

I just noticed that I can't access my NTSF partitions anymore from Ubuntu... for the Windoze system partition, I get an error message that essentially suggests Windows wasn't shut down properly (error messages 2 and 3), but for my other partition I am told that I am not allowed to mount it (error message [1]). That didn't use to be a problem - did they change something in 8.10 vs. 8.04 that would account for this?
Also, it seems that the system doesn't see my external USB DVD burner anymore. Again, it used to work.
Anything I can do to regain access to these resources?

Thank you.

---

### Post by taurus on 2008-11-20
Did you shut down your windows cleanly (no hibernation or sleep) the last time you used it?  You probably need to boot into windows and defrag and scandisk your ntfs partition.  Then, shut it down and reboot into Ubuntu.  You shouldn't have any problem mounting that ntfs partition now.

---

### Post by Niniel on 2008-11-20
I thought I hadn't had a Windows crash in a while, but it turns out that there were indeed disk problems, and it's kind of bad... can't log into the admin account anymore. 
But after a scandisk I can at least browse the partitions from within Linux again.
Although that's kind of funny, too, because Nautilus thinks that my hd is a picture disc. :lolflag:
The system still doesn't like my DVD-RWs, but that's a different problem.

Thank you.

---

