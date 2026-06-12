---
title: "Disabling auto-mount of other partitions"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by manualfaderen on 2008-03-19
Hi All.

I'm new to the ubuntu universe, I used to run linux back in slackware 6/7/8-days, but seeing as that is some years ago, I've sort of lost my touch.

Anyway, I'm running a lenovo t61 with ubuntu 7.10, where almost everything works out-of-the-box - (a huge improvement over my old slackware experience) - but I have some minor problems:

1) on boot ubuntu automatically mounts the three other partitions on my hd (besides my ubuntu-one). I only want it to mount one of them - how do I *dis*able automounting? (one is ntfs the other is fat32)

2) a (probably) related note; one of the folders on the partition I do want, has a little "locker"-logo in the upper right corner of the folder-icon - what does this mean? I can write, edit and run programs from this folder as well, so I guess it's not a consequence of permissions or privileges.

3) I want to make a link on my desktop to some of the folders on my partition, when I right-click and choose "make link" on any folders on the partition I get a 'operation not permitted' dialog box - so something *could* be messed with the permissions/privileges after all!

Any suggestions/recommendations?

Thanks for an awesome community!
Morten

---

### Post by Thanoulis on 2008-03-19
Hello there and welcome back!

To disable auto-mount, edit your /etc/fstab file (you must be root). Comment out the lines with your not-wanted hard disks, and reboot. That's all!
If the folder with the "locker" icon is "lost+found" one, it's ok...i have one too :)
As for the third question, try to type ls -l in a terminal to see the actual priviledges on the folder ~/Desktop (this is where the Desktop icons are been stored).

---

### Post by manualfaderen on 2008-03-23
Thanks for the answer - sorry it took me so long to answer, I've been on holiday.

Anyway, fstab edit was no problemo - thanks!

The folder with the locker-logo is on one of the folders on my fat32-partition. I can read and write from the subfolders, although the permissions are dr-xr-x---! The subfolders are drwxrwx--- though.

Is there any nice program in ubuntu to edit these permissions, or should I just chmod? I've forgotten all but the +777 chmod command - and that may be a bit drastic, after all.

The problem with the link is no the ~/Desktop-folders fault i reckon - it's already when I right-click on a folder and choose "make a link" from the dropdown, that I get the "permission denied". Let me say again, that I can read and write to the folder... It's highly mysterious!

Kind regards,
Morten

---

