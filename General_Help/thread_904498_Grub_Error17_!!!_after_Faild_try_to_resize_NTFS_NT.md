---
title: "Grub Error17 !!! after Faild try to resize NTFS NTFS Partition!"
date: 2008-08-29
forum: General Help
---

### Post by hamzamusa on 2008-08-29
as i was trying to resize my NTFS Partition ! with all the patation tools i get : gParted , Partation Magic , FDisck . with no resize or , convertion NTFS to Fat32 !!

also i tried many LiveCD with HDD Partitining  tools , as puppy linux   linux , Rescue CDs , PE:CD , and Ubuntu Live Install !



now i got Grup 17 error !!!!



as i tried this : [http://ubuntuforums.org/showpost.php?p=5664510&postcount=5](http://ubuntuforums.org/showpost.php?p=5664510&postcount=5) , when i move to :

```
setup (Hd0) 
```

i get :> Error 17: Cannot mount selected partition

with no outputs !!!


what should i do to restore the old grub setting and boot the main installed Ubuntu !

---

### Post by cdtech on 2008-08-29
> setup (Hd0)

That should be a small "h":
setup (hd0)

Have you tried, from the live cd:
grub-install /dev/sda1

---

### Post by Tux+ on 2008-08-29
Sounds like the boot sector has moved. Have you tried re-installing GRUB?

---

### Post by caljohnsmith on 2008-08-29
> **hamzamusa said:**
> 
as i tried this : [http://ubuntuforums.org/showpost.php?p=5664510&postcount=5](http://ubuntuforums.org/showpost.php?p=5664510&postcount=5)
That post you linked to above was for a specific user with a specific HDD partitioning setup, do it probably doesn't apply directly to your partitioning scheme. You need to make sure that when you reinstall grub to the master boot sector (MBR) that Grub points to the correct partition for its system files (menu.lst, stage2, etc). So, bottom line is I would first recommend doing the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

```
If that doesn't fix your Grub issue, you'll need to post the output of:
```
sudo fdisk -lu
```
And also the contents of your Grub's menu.lst. But try the above commands first, and report back the results.

---

### Post by hamzamusa on 2008-08-30
Hi , through this forum i tried to do many things as reinstalling grub , but the HDDs stuck and can't be accessed by LiveCDs .

i tried to save my data , and reformat it , but it only worked after a while of trying to fix the grub and resizing the HDD partations ...

the only livecd were cabable to see ( after many tryouts ) was puppy linux which also helped me backup my datas and reformat the HDD .

thanks alot for helping , and sorry for the late reply .

but it seems HDD problem !

---

