---
title: "sharing files in dual-boot"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by mafaldaspeaks on 2009-05-10
When I had installed version 8.10, ubuntu detected that part of my drive where my files were stored. The same experience with kubuntu. I could open those files (windows documents, pictures, music, etc) from within ubuntu/kubuntu and also store new files in the same drive; when i boot into vista, i could likewise open whatever it was that i had saved when using ubuntu/kubuntu.

Now with version 9.04, the drive where I have my files are not detected so I don't see them in Places and therefore can't mount that drive. However, when i boot into vista, they're there. What step did I miss?

(dual boot: vista and ubuntu; vista and kubuntu)

---

### Post by Herman on 2009-05-10
It's possible that Ubuntu is detecting a file system problem of some kind in the partition you're looking for. Therefore Ubuntu doesn't want to offer you the file system for mounting to protect that file system from the potential of further corruption. I'm not sure, I'm only guessing.

Try running a file system check in that partition and see if that helps.
If it's an NTFS file system, the best file system check  you can give it will probably be from Windows.
If it's any other file system, you can use Gnome Partition Editor in your Ubuntu Live 'Desktop' CD. Just go 'System'-->'Administration'-->'Partition Editor', and right-click on the file system you want to have checked. Then click 'Apply', and 'Apply' again in the confirmation box. Wait and in a few minutes your file system should be repaired. (If that's the problem).

EDIT: For Kubuntu, the equivalent of Gnome Partition Editor is [QTParted]("http://qtparted.sourceforge.net/features.en.html"). I haven't tried that in the last year or two, so I'm not sure if it runs file system checks.  Try it. If not possibly you can install Gnome Partition editor or run fsck from the command line.

Regards, Herman :)

---

### Post by mafaldaspeaks on 2009-05-10
> **Herman said:**
> It's possible that Ubuntu is detecting a file system problem of some kind in the partition you're looking for. Therefore Ubuntu doesn't want to offer you the file system for mounting to protect that file system from the potential of further corruption. I'm not sure, I'm only guessing.

Try running a file system check in that partition and see if that helps.
If it's an NTFS file system, the best file system check  you can give it will probably be from Windows.
If it's any other file system, you can use Gnome Partition Editor in your Ubuntu Live 'Desktop' CD. Just go 'System'-->'Administration'-->'Partition Editor', and right-click on the file system you want to have checked. Then click 'Apply', and 'Apply' again in the confirmation box. Wait and in a few minutes your file system should be repaired. (If that's the problem).

EDIT: For Kubuntu, the equivalent of Gnome Partition Editor is [QTParted]("http://qtparted.sourceforge.net/features.en.html"). I haven't tried that in the last year or two, so I'm not sure if it runs file system checks.  Try it. If not possibly you can install Gnome Partition editor or run fsck from the command line.

Regards, Herman :)

Ok, I'll try this. Thanks!

---

