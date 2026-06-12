---
title: "Boot Windows partition from external HDD (GRUB?)"
date: 2008-10-21
forum: General Help
---

### Post by Yoshis88 on 2008-10-21
**How can I boot a computer from a Windows partition located on an external hard drive?**
I am very comfortable with working in terminal and have been around Linux for a little while (specifically since Ubuntu 6.06).  I think GRUB can do the trick, but any tips would be appreciated.  And sorry for the long post.  Feel free to skip to the last paragraph.

Story time below
------ 

I have two old laptops that had/have very slow Windows.  One is a Westinghouse (NB-14w2, runs 8.04 flawlessly), the other is a Toshiba (Satellite, don't know exact model right now).  Basically, through the university, I get a free XP pro install CD, so I wanted to wipe the systems and reinstall XP/Ubuntu.  The systems just came with one partition on the hard drive, the Windows partition.

I used GParted to copy the Westinghouse partition to a sufficiently large external hard drive.  So, this external hard drive has a primary data partition for easy use, but in an external partition, there is a copy of the partition of the old Westinghouse partition.  I proceeded to wipe the system and installed my dual boot configuration with GRUB written to the MBR.

Now, I want to boot off of that old partition image.  However, I realize, I don't really know how I might do that, though GRUB seems sufficiently sophisticated.  Recently, the Toshiba was given to me so that I could do the same, wipe and reinstall for speed.  As I type this, the partition is being copied to the same external hard drive, as another logical partition in the extended partition using GParted.

-----

I don't really feel like modifying my menu.lst file, because I'm not going to be doing this often, most likely just once, that is, I'm happy just manually typing this into the grub terminal.  Ideally, I would like to install GRUB to an external flash drive, that would just bring me to a GRUB terminal for me to give it manual commands.

I'm thinking I would need to type something like this, where the first # is probably 1 (the external hard drive) and the second # is whatever partition number it is.  Does this look somewhat right?
```
> root (hd#,#)
> makeactive
> chainloader +1
```

---

### Post by louieb on 2008-10-21
May have to use the map command to make XP think it is on the 1st hard drive.  don't know if XP will work installed on an external drive but if XP was on the 2nd internal drive this is what my grub enry would look like.
```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1


```

---

