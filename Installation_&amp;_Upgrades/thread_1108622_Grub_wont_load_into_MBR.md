---
title: "Grub wont load into MBR"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by strangedays on 2009-03-27
Alright, so this is what i got.  i have 4 drives in my system. 
1 contains ubuntu and a ntfs extended partition (movies)

2 vista, xp and extended partion for yes (more movies)

3 and 4 storage.

now my issue is this.  #2 drive with vista and xp is done.  i can get it to load but shortly after it says bu bye.  i take it out and now grub wont load.  i loaded the live disk and went through the reinstall grub process


sudo grub
root (hd0.5)
setup (hd0)
quit

reboot and nothing.  as soon as i reconnect the old win drive grub loads
i've gone over and over in my head and am lost.  

any ideas.   also if you need detail tell me what ya need and i will get to ya

thank you for any help

---

### Post by daveg2 on 2009-03-27
It sounds like your windows CD was hooked up during the Ubuntu install and grub was written to the boot sector of your windows drive, thus windows will no longer load because the Windows boot loader has been replaced by grub.  I don't understand why the reinstall of grub with the windows drive out didn't take.  Might hd0 now be one of the two storage drives?  

I'd suggest noting the position of all four drives, unhook all drives and hook up the ubuntu drive in the primary position.  Then install grub on the only drive.  Ubuntu should now boot correctly.  Remove the ubuntu drive and put the windows drive back in the primary position.  Reinstall the windows boot loader with a Windows install disk.  How I don't know.  Google for it.

When Windows will boot, then put the Ubuntu drive in the primary slot, the Windows in the secondary, and do the grub magic in thread "Two Hard Drives" in this forum.

When Windows and Ubuntu will dual boot correctly, put the two storage drives back in.

Suggestions only.  YMMV.  I could be way off base.  If so, I hope someone will let us know!

---

### Post by strangedays on 2009-03-28
well i am obviously not a smart as i know im not.


it was a simple thing that i had not even thought of.


when i loaded the partition manager after removing the windows drive
i failed to flag the ubuntu drive as boot.

all the time and effort for something so simple

thank you much for replying.  

all is right with my world

---

### Post by giridharseel on 2009-03-28
Hello guys,,plz help me man!!!!!!!!!
My problem is here..
i had installed ubantu 8.x as a fresh copy in my hard disk but now i need to get back to windows so i set my bios to load from a cd drive and used the vista cd.but it never reads the cd it just goes to boot the ubantu.

so tried another method by just formatting the partition in which ubantu lies and creates another partition as a ntfs partition using ubantu live cd.

but i get the error number 17 grub error,, vista cd never boots and also xp,,, it works well in other systems..

plz guide me...............

---

### Post by tommcd on 2009-03-28
> **daveg2 said:**
> 
When Windows will boot, then put the Ubuntu drive in the primary slot, the Windows in the secondary, and do the grub magic in thread "Two Hard Drives" in this forum.


To dual boot with Ubuntu on the first hard drive and Windows on the second drive (i.e., Ubuntu is on the primary, or first boot drive) see this:
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

---

