---
title: "First-look: Newbie Questions"
date: 2008-10-18
forum: General Help
---

### Post by sirdouglas on 2008-10-18
I just finished making the switch from Windows to ubuntu (4.10 I think) with GNOME 2.18.1, and upon first look and playing with it for the past day I must say that I love it!  Naturally, as a newbie with the Linux a world a few questions have come up.  Any support would greatly be appreciated.

1)  I know that the newest version of Ubuntu is beyond 8.0 by now.  To upgrade to this do I simply click on the "upgrade" option in my desktop?  Will this erase all my data?

2)  I have found that a few necessary programs are not supported by Linux.  One of them includes mobipocket reader (converts and reads .prc ebook files).  So I'm considering reformatting once again to run a dual-boot of Windows and Ubuntu.  My question is: can I partition my hard drive to include Windows without erasing my current setup/files with Ubuntu?  I've spent the whole weekend just getting it set up and don't want to go through the whole process of installing Ubuntu again.  And my HD is just 80 GB... does anyone know if a very small version of Windows XP exists?

3)  I bought a Kingwin External Hard drive enclosure about 3 years ago, and it has always worked fine with Windows.  Ubuntu only seams to support it as read-only though.  Is there a way to get the drivers for this advice?  Maybe the newest version of Ubuntu supports and will solve my problem.

I will surely return with more questions as my journey through Ubuntu continues.  All the help from this community is much appreciated.

Doug

---

### Post by scragar on 2008-10-18
> **sirdouglas said:**
> I just finished making the switch from Windows to ubuntu (4.10 I think) with GNOME 2.18.1, and upon first look and playing with it for the past day I must say that I love it!  Naturally, as a newbie with the Linux a world a few questions have come up.  Any support would greatly be appreciated.

1)  I know that the newest version of Ubuntu is beyond 8.0 by now.  To upgrade to this do I simply click on the "upgrade" option in my desktop?  Will this erase all my data?

The is very minimal chance of any data being lost by upgrading to the latest version
> 2)  I have found that a few necessary programs are not supported by Linux.  One of them includes mobipocket reader (converts and reads .prc ebook files).  So I'm considering reformatting once again to run a dual-boot of Windows and Ubuntu.  My question is: can I partition my hard drive to include Windows without erasing my current setup/files with Ubuntu?  I've spent the whole weekend just getting it set up and don't want to go through the whole process of installing Ubuntu again.  And my HD is just 80 GB... does anyone know if a very small version of Windows XP exists?[http://www.spacejock.com/yBook_Download.html](http://www.spacejock.com/yBook_Download.html) <-- this will run under wine and allow you to access your ebooks without needing to boot into windows for the pupose, in regard to the other part of the question [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) is a nice guide that covers everything you will need to know.
> 
3)  I bought a Kingwin External Hard drive enclosure about 3 years ago, and it has always worked fine with Windows.  Ubuntu only seams to support it as read-only though.  Is there a way to get the drivers for this advice?  Maybe the newest version of Ubuntu supports and will solve my problem.

Intresting, since ubuntu can read it I can't see why ubuntu would refuse to write to it, paste the output of the```
mount
```command back here, it may just be a case of remounting the drive...
> 
I will surely return with more questions as my journey through Ubuntu continues.  All the help from this community is much appreciated.

Doug

---

### Post by sirdouglas on 2008-10-18
Wow, well thanks for the quick reply.  

As I am quite the newbie at this point, I don't really even know how to add "mount" under the code!

Thanks so far!

Doug

---

### Post by scragar on 2008-10-18
Open a terminal(Applications>Accessories>Terminal) and just type the command(or you can use the highlight-middle click shortcut to paste it out(if you don't have a middle mouse button you can press left and right click at the same time)).


PS: as a new user there are a few things you will likely want to install, the restricted extra's package contains MP3 codecs, flash and a few other things:
```
sudo apt-get install ubuntu-restricted-extras
```

---

