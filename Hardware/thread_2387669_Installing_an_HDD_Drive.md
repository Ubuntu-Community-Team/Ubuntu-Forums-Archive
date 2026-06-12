---
title: "Installing an HDD Drive"
date: 2018-03-22
forum: Hardware
---

### Post by dannyk2 on 2018-03-22
At present i am running Ubuntu (GNOME) 17.10 installed as my default operating system on a 500GB SSD Drive.
But now i want to install another 1TB HDD Drive. Is there someone who could tell me how i might accomplish this please.
I have to admit that i am a beginner so any tutorials would have to be really easy to follow.
Thanks.

---

### Post by slickymaster on 2018-03-22
*Thread moved to **Hardware**.*

---

### Post by dannyk2 on 2018-03-22
Cheers slickymaster

---

### Post by Autodave on 2018-03-22
Are you asking how to physically install it in your machine? YOUTUBE is full of videos explaining that.

---

### Post by TheFu on 2018-03-22
* Physically connect the disk to power and a sata cable inside.
* Use **gparted** to format the disk to "ext4" - do not leave it as NTFS. There are complexities with NTFS that are best avoided unless you have a very good reason.  Gparted can completely destroy every file on every disk of your system, so be 100% certain you are working on the disk you intend to be working on.  100% data loss is possible of you use the wrong disk.  _You've been warned. _
* Modify the /etc/fstab file (it is text) to mount it - google "ubuntu fstab" for a guide on help.ubuntu.com or wiki.ubuntu.com - the key is to create an empty directory to be used as the "mount point". The guides will explain better. It doesn't need to be at the top and I would suggest that for a permanent mount that it should not be in /mnt/ or /media/ - ok?

**Pro-tip:**
Whenever editing system text files, use **sudoedit**.  Ignore when people say to use anything else to edit files.  sudoedit is always safe, regardless of the editor you choose to use.   Any editor can be used ... nano, vim, gedit, leafpad,  .... whatever you like. The manpage has more details for how to change the default editor for your account.

Don't expect to use a GUI for the fstab edits.  Best to start sudoedit from a terminal.

There are hundreds of things that I've assumed.  There are hundreds of options that I haven't mentioned, which might change your choices. For a beginner, easy is more

---

