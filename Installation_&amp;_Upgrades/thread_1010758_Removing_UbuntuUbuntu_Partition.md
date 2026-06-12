---
title: "Removing Ubuntu/Ubuntu Partition"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by olly666 on 2008-12-14
I have a second computer now that I will run solely Ubuntu on so I would like to remove it from this one and give Vista some more hard drive space.

What's the easiest way to about doing it without effecting Vista?

Thanks

(P.S. The installation can be wiped; already backed up)

---

### Post by bulldog on 2008-12-14
Well you can delete and/or format the ubuntu partitions within Vista,and add them to your Vista install.
To remove grub from the mbr,I think you'll need the Vista install cd,to recover the Vista bootloader,but I'm not familiar with Vista,so I'm not sure about the procedure.

---

### Post by caljohnsmith on 2008-12-14
If you have your Vista Install CD, to restore a Windows MBR to your HDD so you will boot straight into Windows you can do:
```
bootrec /fixmbr
```
Or if you don't have a Vista Install CD, you can instead install a Windows equivalent MBR from the Live CD by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo lilo -M  /dev/sda mbr
```
And change "sda" if your drive is different, but most likely it won't be. How about giving one of those methods a shot and let me know how it goes.

---

### Post by olly666 on 2008-12-14
> **caljohnsmith said:**
> If you have your Vista Install CD, to restore a Windows MBR to your HDD so you will boot straight into Windows you can do:
```
bootrec /fixmbr
```
Or if you don't have a Vista Install CD, you can instead install a Windows equivalent MBR from the Live CD by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo lilo -M  /dev/sda mbr
```
And change "sda" if your drive is different, but most likely it won't be. How about giving one of those methods a shot and let me know how it goes.
caljohnsmith, you da man! I jumped a little too far ahead and deleted the partition through windows. then realized the mbr was unreadable and couldn't do anything. used the ubuntu live cd and did step two and it worked like a charm. thank you!!!

---

### Post by networm1230 on 2008-12-14
I know of one thing that might work for you (Dband) Darik's Boot And Nuke with this you can wipe your had drive or had drives you even erase a portion that you do not what on you pc or start a new portion the site is [http://www.dban.org](http://www.dban.org)

I this is us full to you

---

