---
title: "gfxboot theme"
date: 2008-09-28
forum: General Help
---

### Post by zzzzz1 on 2008-09-28
Id like to install this gfxboot theme 
[http://www.gnome-look.org/content/show.php/Linux+Hack+-+gfxboot+theme?content=51031](http://www.gnome-look.org/content/show.php/Linux+Hack+-+gfxboot+theme?content=51031)
 (or any other nice one if someone has a suggestion)
I tried yesterday following this thread 
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)
and screwed up badly as can be seen in my thread 
[http://ubuntuforums.org/showthread.php?t=931861](http://ubuntuforums.org/showthread.php?t=931861)

thanks to the awesome help and patience from caljohnsmith my Problem is now fortunately solved (he advised me against trying again btw.)

My question is: Is anybody here able and willing to guide me through this if i post my fdisk -l output and whatever else is required, cause I really don't want to screw this up again?

---

### Post by zzzzz1 on 2008-09-29
I followed this easy guide and it worked

[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/](http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/)

the only issue I had was :

```
sudo grub-install /dev/sdbx
```

would give me this error:

/dev/sdbx does not have any corresponding BIOS drive

however,
```

sudo grub-install --recheck /dev/sdbx
```

did the trick for me

---

