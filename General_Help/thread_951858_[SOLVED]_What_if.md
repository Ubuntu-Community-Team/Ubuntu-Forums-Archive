---
title: "[SOLVED] What if?"
date: 2008-10-18
forum: General Help
---

### Post by tromort on 2008-10-18
What would happen if I would backup my whole system (installed on sda5) to an external drive, then format my harddisk and them put it all back?
would it still work? Or would it have a conflict with being not on sda5 anymore?

---

### Post by ugm6hr on 2008-10-18
> **tromort said:**
> What would happen if I would backup my whole system on sda5, then format my harddisk and them put it all back?
would it still work?

sda5 is not your whole system.  It is a single partition.

Formatting that partition, then copying the contents back is pointless - it will not achieve anything (i.e. you will be in the same position as now).

---

### Post by tromort on 2008-10-19
> **ugm6hr said:**
> sda5 is not your whole system.  It is a single partition.

Formatting that partition, then copying the contents back is pointless - it will not achieve anything (i.e. you will be in the same position as now).

sorry, should have explained it more clearly; I want to backup sda5 (where Ubuntu is installed) on an external drive. Then format everything. When I'd put it back it probably won't be on sda5 but on 1 or something. Would that matter?

---

### Post by scouser73 on 2008-10-19
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by ugm6hr on 2008-10-19
> **tromort said:**
> When I'd put it back it probably won't be on sda5 but on 1 or something. Would that matter?

Yes, it would matter.  GRUB will not find it - so it won't boot at all.

If this is for backup reasons - why would you reinstall in a different partition?

Perhaps if you explain exactly what you are trying to do, someone can make suggestions...

---

### Post by tromort on 2008-10-19
> **ugm6hr said:**
> Yes, it would matter.  GRUB will not find it - so it won't boot at all.

If this is for backup reasons - why would you reinstall in a different partition?

Perhaps if you explain exactly what you are trying to do, someone can make suggestions...

Grub could be updated using a live cd or super grub disk :) a/w explaination:
my harddisk looks like the following:
20gb ntfs - windows xp
20gb ntfs - Vista
25gb - extended
  15 gb - ubuntu 8.04
  10 gb - ubuntu 8.10
7 gb - free
2 gb - swap
Like you can see this might not be the smartest set up since I have 4 partitions and cant great new one/edit the extended one, So basically I want to start all over again.
Although the Gparted live cd might give a solution, but it never worked for me ;)

---

### Post by Bucky Ball on 2008-10-19
I would suggest you go the APTonCD route and backup all your packages, backup all of your personal data; files, bookmarks, address books and the like then boot from you Ubuntu install CD and start from there and re-install Ubuntu, reformatting the drive in the process (at the partitioning section of the install). There is an option there to format. You can delete all the partitions and start again.

When you're done, as suggested, load back your packages and put your personal data in the freshly made new partitions.

/
/boot
/home
/visual
/audio
/personal

... or whatever you decide to create. I like to sit down with a piece of paper and pencil and plan it before going ahead. If you keep your data on separate partitions like this, next time you can just reinstall the OS without having to pick out all your personal stuff for backup. Intrepid Ibex is due to land shortly, so might be worth a short wait if you re-install. :)

---

### Post by ugm6hr on 2008-10-19
Assuming all your hardware drivers and apps are Ubuntu standard repo (rather than self-compiled)...

My suggestion:
Backup /home
Backup /var/cache/apt/archives (except lock file)
Follow advice here to create a list of apps: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
Rearrange your extended partitions (Optional: Create a separate /home when you reinstall)
Reinstall Ubuntu from CD (fresh)
Copy back /home and /var/cache/apt/archives
Reinstall apps ([http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366))

Obviously you'll need to do this for each version of Ubuntu separately.

As for copying the entire partition and reinstating elsewhere... I'm not 100% certain if it will work.  I suspect not.  But then I've never tried.

---

### Post by tromort on 2008-10-19
Thanks all for helping me.

---

### Post by expatCM on 2008-10-19
Perhaps Remastersys could help here
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

