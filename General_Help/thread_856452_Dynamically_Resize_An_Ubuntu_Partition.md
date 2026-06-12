---
title: "Dynamically Resize An Ubuntu Partition"
date: 2008-07-11
forum: General Help
---

### Post by LBattis on 2008-07-11
I presently have two instances of Ubuntu (AMD64) loaded along with an XP installation for legacy Notes/Domino purposes.  My principle Ubuntu partition is /dev/sda4 .  When I originally installed it I goofed up and got the partition size wrong.  It's too small.  I missed a decimal place or something equally dumb.  What I would like to do now is dynamically resize /dev/sda4 , by transitioning ~80% of /dev/sda2 over to /dev/sda4 .  I have loaded QTParted, sudo'd it up in a terminal window and gone through the GUI looking for a 'Partition Magic,' function for dynamic sizing with no success.  I've read from multiple sources that what I want to do is do-able.  How do I do it? . . . :confused:


FDISK:

DEVICE BOOT START END BLOCKS ID SYSTEM

/dev/sda1 * 1 3891 31254426 7 HPFS/NTFS
/dev/sda2 3892 36187 259417620 83 Linux
/dev/sda3 38086 38913 6650910 5 Extended
/dev/sda4 36188 38085 15245685 83 Linux
/dev/sda5 38175 38913 5935986 82 Linux Swap/Solaris
/dev/sda6 38086 38174 714829+ 82 Linux Swap/Solaris

---

### Post by dracayr on 2008-07-11
you can't resize from the running system because you can only resize unmounted drives. You'll have to use a liveCD. In the case of the ubuntu liveCD: go System->Administration->Partition Editor, apply the wanted changes and click apply

dracayr

---

### Post by chris4585 on 2008-07-11
You can do that or use the gparted livecd, i find it works very well

---

### Post by LBattis on 2008-07-14
> **dracayr said:**
> you can't resize from the running system because you can only resize unmounted drives. You'll have to use a liveCD. In the case of the ubuntu liveCD: go System->Administration->Partition Editor, apply the wanted changes and click apply

dracayr

Worked beautifully, Thank-you.  
Having had the experience I can add some caveats for Windows users who are making the transition over to Ubuntu.
The GParted (partition editor) software on the Ubuntu v.8.04 LiveCD requires a bit more attention as you're configuring it for your desired operation than Partition Magics I have used.  You have to create space before you can expand another space.  In other words, you have to shrink a partition before you can expand a partition.  I also suspect that the partitions must be adjacent although I haven't tested this hypothesis as my partitions were adjacent to begin with.
With all that said, it was a reasonably rapid and very well executed process that left me with exactly the desired result.
Lovin' Ubuntu . . .

---

