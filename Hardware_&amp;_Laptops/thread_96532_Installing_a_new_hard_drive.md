---
title: "Installing a new hard drive"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by erjohan on 2005-11-29
Hey all,

I just bought a new harddrive and popped it into my machine, and well it's not showing up anywhere. Do you guys know of any graphical tool that can help me install a new hard drive? 

I really want a graphical way of doing this. I have been using linux since 1994 so I know how to do it from the command line:
[http://aplawrence.com/Linux/adddrive.html](http://aplawrence.com/Linux/adddrive.html)
[http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)
[http://linux.ncl.ac.uk/format/](http://linux.ncl.ac.uk/format/)

---

### Post by Lambert on 2005-11-29
I've heard there are graphical ways of adding a drive. I believe kde has one. But my knowledge is limited. you can google fstab graphical and see what comes up. Maybe search synaptic using the term fstab to see what apps associate with that keyword.

With out a graphical interface it's actually very easy to add the drive into the file tree. Just add a line to your /etc/fstab file.

Here is a link that explains in detail about that file.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by erjohan on 2005-12-04
[QUOTE=Lambert]
With out a graphical interface it's actually very easy to add the drive into the file tree. Just add a line to your /etc/fstab file.
[/QUOTE]

I would like everything to be graphical.. ;-) Recently a friend of mine an old school game programmer, asked me how he should add his new harddrives to the system. He succeded in formatting them and all that, but he didn't realize that there was a fstab.

I don't think the installation of Ubuntu, should be the only thing that's easy to setup.. Am I th only one who thinks this?

You were right:
[Diskdrake](http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake)  abit userfriendly..
[Kouvert ](http://www.kde-apps.org/content/show.php?content=15185) expert stuff

They don't give me the features I want:
1. recognition of a new harddrive,
2. automatic configuration of a new harddrive (partition/filesystem creation/mount point)
3. accessability to the user
4. handling of a strange FS (NTFS/HFS+/VFAT)

First point, if I pop a new harddrive in the computer I should be intructed how to let the computer do automatic configuration for me.

Second point, the dialog "Do you want to format this new harddrive YES/NO" is all that is needed. Of course there should be an advanced dialog, which would probablybe something like Diskdrake.

Third point, if the user inserts a NTFS harddrive it must be configured so that he can read the dataas a user. You should no thave to be root to access them, do you know how many people have problems with this? 

Fourth, that was point three. ;-)

Nice to get this off my chest.

---

