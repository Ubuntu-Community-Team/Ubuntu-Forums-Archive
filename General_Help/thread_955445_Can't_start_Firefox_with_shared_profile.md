---
title: "Can't start Firefox with shared profile"
date: 2008-10-22
forum: General Help
---

### Post by Markstar on 2008-10-22
Hi,
I am new to Ubuntu and need to share my Firefox and Thunderbird with my Windows. The profile is on a FAT32 partition which I mounted with the following command:
```
/dev/sdb9 /mnt/MS	vfat	defaults,user,dmask=000,fmask=000 0 0
```

I also edited the profiles.ini to point to the right directory (/mnt/MS/...). However, when I start Firefox or Thunderbird, I get the error message:
> "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system." 

I used Google and found those three possibilities:
1) Firefox is still running in the background.
[INDENT]-> Not it because this also happens when I just restarted.[/INDENT]

2) The folder is still locked because the profiles folder still contains a "parent.lock" (Windows) or "lock" and ".parentlock" (Linux) file.
[INDENT]-> There are no such files in the folder (and I can see hidden files).[/INDENT]

3) I don't have the permission to write to that folder. 
[INDENT]-> Didn't I mount the partition so that I have all permissions?[/INDENT]


If I copy the folder over to the Linux partition and point profiles.ini to that folder, it does work. :confused:

Any help would be greatly appreciated!!!

---

