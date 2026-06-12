---
title: "Problem with nautilus and F-Spot"
date: 2008-10-31
forum: General Help
---

### Post by t4ggs on 2008-10-31
I'm having a problem when opening an ntfs partition, it shows me this annoying bar saying that this files are on a Picture CD and if I want to open it with F-Spot Photo Manager.. This is not a Picture CD its an Hard Drive, and I have other ntfs drives mounted and the don't show that bar..

What should I do to get rid of it??

---

### Post by t4ggs on 2008-10-31
btw i'm using intrepid

---

### Post by danduq on 2008-11-04
I'm having similar issues with Intrepid. If I click "Places - Home Folder" F-Spot launches. If I click "Places - Bookmarks - Any old bookmark" F-Spot launches.

Actually, just thinking about it, half of my bookmarks are NTFS mounts. I can't remember if any of the other Bookmarks had the same problem. Maybe it's an NTFS mounting thing?

Solution so far was to uninstall F-Spot.

---

### Post by danduq on 2008-11-04
OK, forget the NTFS thing, I just reinstalled F-Spot and it happens with local ext3, ntfs and remote smbfs mounts. F-Spot just seems to want to launch whenever I try to launch a directory from the panel.

Launching from the "Run Application" box works fine (launching either "/home" or "nautilus").

---

### Post by t4ggs on 2008-11-04
well i checked fstab and not seems to be any problem there... so definitely its f-spot... but why only in intrepid??

---

### Post by plucky on 2008-11-04
> **t4ggs said:**
> well i checked fstab and not seems to be any problem there... so definitely its f-spot... but why only in intrepid??

check out this [bug report](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

To fix from a terminal open Nautilus. Right click on a folder and select "Open with other Application" and select File Browser.

The problem is because it is trying to use F-spot to open a folder instead of a File Browser.Mine tried to use Rhythmbox.

Good Luck

---

### Post by danduq on 2008-11-04
> **plucky said:**
> 
To fix from a terminal open Nautilus. Right click on a folder and select "Open with other Application" and select File Browser.


Great, thanks for this. Your solution didn't quite work, I had to;
1. Right-click on a folder and select Properties
2. Navigate to "Open With" tab
3. Select "File Browser"

All back to normal again now! Thanks again!  :)

---

### Post by t4ggs on 2008-11-04
> **danduq said:**
> Great, thanks for this. Your solution didn't quite work, I had to;
1. Right-click on a folder and select Properties
2. Navigate to "Open With" tab
3. Select "File Browser"

All back to normal again now! Thanks again!  :)

Did that but still shows the bar at the top///:confused:

---

### Post by t4ggs on 2008-11-05
I uninstall f-spot and now it opens it with brasero#&%!&#

---

### Post by t4ggs on 2008-11-19
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936)

---

