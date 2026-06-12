---
title: "Upgrade from Kubuntu 8.04 to Ubuntu 9.04"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Bluemax_36 on 2009-10-09
My wife's computer has Kubuntu 8.04 installed.  It has worked quite well for her, but lately it seems to have become unstable.  On recent updates, I've noticed an option to upgrade to Ubuntu 9.04.  I have Ubuntu 9.04 installed on my laptop, and I'm very pleased with it.  My questions are these:
1)  If I use the option on line to upgrade the existing Kubuntu OS, will it result in the installation of Ubuntu 9.04 or will it continue the KDE4 desktop.  Personally, I'd rather end up with the Gnome format.  That's what I have in my laptop, and I like it much better.
2)  My wife has Thunderbird mail.  Using the online upgrade, will I have to copy the profile and reinstall it in the new setup?  Or will the upgrade simply incorporate the existing profile?
3)  Anyone else done this, and are there any other known issues that I should be aware of?

Thanks a bunch,

Bluemax_36

---

### Post by slakkie on 2009-10-09
Upgrading directly to 9.04 is not possible AFAIK. I know they implemented an option to directly upgrade from 8.04 to 9.10. But don't know when that version of update-manager will hit hardy.
For now you need to upgrade to 8.10 and upgrade to 9.04 from there.

On my 8.04 box, I can only upgrade to 8.10...
```

sudo do-release-upgrade                     
Checking for a new ubuntu release                                                        
Done Upgrade tool signature                                                              
Done Upgrade tool                                                                        
Done downloading                                                                         
extracting 'intrepid.tar.gz'                                                             
authenticate 'intrepid.tar.gz' against 'intrepid.tar.gz.gpg'                             

```

> 
1) If I use the option on line to upgrade the existing Kubuntu OS, will it result in the installation of Ubuntu 9.04 or will it continue the KDE4 desktop. Personally, I'd rather end up with the Gnome format. That's what I have in my laptop, and I like it much better.


It will upgrade to KDE4, although the version in 8.10 is not up to par, but the 9.04 version is a better improvement.

> 
2) My wife has Thunderbird mail. Using the online upgrade, will I have to copy the profile and reinstall it in the new setup? Or will the upgrade simply incorporate the existing profile?


If you upgrade there is no need to worry about that data. Nothing in /home will be touched by the upgrade itself. Upgraded packages could off-course change bits in your homedir but that's logical. Firefox and Thunderbird however will not have any changes that affect your profiles. I use 9.10 and can boot in my 8.04 install and use Thunderbird as if nothing has changed.

> 
3) Anyone else done this, and are there any other known issues that I should be aware of?


TBH, if you can wait a month you could install (not upgrade) Ubuntu Karmic (9.10). KDE 4.3.1 is awesome. It is far better then Gnome IYAM. 

If you have a separate slice for /home then it becomes even easier. You could use clonezilla to backup your current OS, do the upgrades, if it fails you can restore the backup really easy. I can backup/restore within 15 minutes from one version to another version of Ubuntu.

---

