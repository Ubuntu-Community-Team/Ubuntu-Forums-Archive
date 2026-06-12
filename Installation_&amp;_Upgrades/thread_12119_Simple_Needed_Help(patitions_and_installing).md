---
title: "Simple Needed Help(patitions and installing)"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by Leer on 2005-01-22
Im a semi-n00b when it comes to linux

the only thing i dont know how to do is a make a patition.
when i first tried i could not access Windows XP (i want to have a dual boot) whatsoever. its wasnt even in the GRUB menu

I think i made the patition wrong

i just wanna give 25.5 GB to Ubuntu then have the rest for XP

can someone please explain how to do this?

---

### Post by eNiNjA on 2005-01-22
Easy Way:
    
    Install XPee first.
    
    Obtain Partition Magic.
    
    Use Partiton Magic, to shrink your NTFS(i assume) file system, so you have 25 gigs of empty space.
    
    Start your ubuntu install.
    
    Manually create the partitions to install Ubuntu (read: don't select use entire disk), with the free space, like so:
    
    / = 4 to 5 gigs (or whatever)
 swap = gawd there is sooo many arguments about this. I have spaced off a value, that doubles the amount of ram I have, ever since i was a boy =P
    /home = the rest of the space left
 
 Ensure that the XPee partiton is bootable. Should have an arrow thingy looking thing, that is pointing down. (i may have distro install mix syndrome on this one)
 
 The rest of the partitions, should have smiley-dudes beside them.
    
    Procede with install.
    
 When it is at the point of installing the bootloader, it should say whether it sees XPee or not. If it does, procede, your done.
  
  Cool way:
  
  Heck wiff XPee, use the entire disk =)

---

### Post by Leer on 2005-01-22
I got the first part but how do I create the actuall pation in the ubuntu install?

---

