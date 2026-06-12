---
title: "File Permissions Issue on Portable Drive"
date: 2020-05-24
forum: Hardware
---

### Post by mr-bear on 2020-05-24
Hi there,

So I am new to Ubuntu, but I have run into an issue that I have not been able to resolve.

When I try to open a PSD file from my portable usb drive in GIMP, it says I can't open that file, but if I copy the file to my HD it opens without issue.

1] I have tried changing the permissions at the Root level, still no dice.
2] I have tried reformatting the USB drive and it still happens.
3] This also happens with PDF files being opened by Okular.

Myself, and some very clever Linux users were unable to resolve the issue, so I am turning here for help with this. I really want to make the move to Ubuntu permanently, but this buggaboo is causing me to lose productivity time working. Anyone had this issue and knows a solution?

I will post anything anyone needs to try and work this out, I am at my wit's end.

:(

Thanks in advance.

---

### Post by CatKiller on 2020-05-24
Are you using snaps?

---

### Post by rbmorse on 2020-05-24
What file system is on the external?

---

### Post by kurt18947 on 2020-05-24
Probably not the best solution but I format removable media FAT32 as long as the files are not larger than 4 GB. No permissions issues, I don't know if there are any security considerations.

---

### Post by mr-bear on 2020-05-25
> **CatKiller said:**
> Are you using snaps?

Yes I am.

> **rbmorse said:**
> What file system is on the external?

We tried a bunch, including VFAT and nothing changed it, same issue provided.

> **kurt18947 said:**
> Probably not the best solution but I format removable media FAT32 as long as the files are not larger than 4 GB. No permissions issues, I don't know if there are any security considerations.

I work with large files, so unfortunately this is not an option. Also we tried FAT32 and VFAT and the problem persisted. 

All I can say for sure is that this issue is not a drive formatting one, we exhausted our research on that one. :(

I really an hopeful that a solution can be found, as I long to move away from Windows as much as possible.

Thanks again for the help thus far. :)

---

### Post by CelticWarrior on 2020-05-25
This question is quite simple if you're using snaps. For 20.04 GIMP itself is not a snap but the Diolinux patch PhotoGIMP is. This is probably what you have installed. Snaps have exactly the limitation you're reporting and it has nothing to do with file systems.

Based on this assumption open the software store, find PhotoGIMP, click Permissions and then enable "Read/Write files on removable storage devices".

Regarding file systems, if the external storage device is to be used also in Windows, use NTFS. Otherwise EXT4. That's all.

---

### Post by mr-bear on 2020-05-25
> **CelticWarrior said:**
> This question is quite simple if you're using snaps. For 20.04 GIMP itself is not a snap but the Diolinux patch PhotoGIMP is. This is probably what you have installed. Snaps have exactly the limitation you're reporting and it has nothing to do with file systems.

Based on this assumption open the software store, find PhotoGIMP, click Permissions and then enable "Read/Write files on removable storage devices".

Regarding file systems, if the external storage device is to be used also in Windows, use NTFS. Otherwise EXT4. That's all.

100%

From a Celtic-Viking to a Celtic-Warrior, you have my thanks!

Wow, so simple and yet folks had me doing deep level stuff and all it needed was a toogle.

Cheers!

---

### Post by TheFu on 2020-05-25
> **mr-bear said:**
> 100%

From a Celtic-Viking to a Celtic-Warrior, you have my thanks!

Wow, so simple and yet folks had me doing deep level stuff and all it needed was a toogle.

Cheers!

it is only simple if you have a default setup.  if the external storage was mounted elsewhere, then it would have been impossible to solve other than copying the files to your HOME.   

No editor of any sort should be a snap.
No media player, audio or video, should be a snap.
No software development tools should be snaps.

Please mark this thread as solved - use the "Thread Tools" button near the top of the page. Help the community out!

---

### Post by CatKiller on 2020-05-25
> **TheFu said:**
> No editor of any sort should be a snap.
No media player, audio or video, should be a snap.

I don't agree with these, actually. I *do* think that they should default (or make it more visible) to allowing access to *removable-media*, though. If your library of stuff isn't in /home, /media, /run/media, or /mnt then you're probably capable of making your own symlinks.

> No software development tools should be snaps.

This argument has more legs, though.

Off-topic for this thread, however.

---

