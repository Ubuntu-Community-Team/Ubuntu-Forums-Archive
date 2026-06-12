---
title: "Help please........."
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by wicky439 on 2009-03-18
Hi I am new one in this community and saw the review of ubuntu at youtube.com. Since i am interested in this and want to install this operating software. I search in many search engines for help but cannot achieve my goal. Then i visit this forum and Register here to ask some thing about this.

As i don't know any thing about ubuntu so i want to install a fresh copy of this operating software by erasing the WINDOWS in my PC.
Any body can guide me in right way by posting tutorial of installation with pictures.

Thanks in advance

---

### Post by taurus on 2009-03-18
[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by wicky439 on 2009-03-18
> **taurus said:**
> [https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

I want to install a fresh copy not dualboot. Also i want to ask that i have 4 partitions in WINDOWS i.e C, D, E, F. When i will install ubuntu how i will delete all partition and create new partitions?

---

### Post by taurus on 2009-03-18
Dualboot, not dualboot, the process is the same.  Just tell the installer to use the whole harddrive when you get to the partition screen, Step 4 of 7.

You said you wanted some pictures, so I gave you a link with pictures!

---

### Post by Kevbert on 2009-03-18
You can tell Ubuntu to use the whole disk when you get to the partition stage or install manually. If you select manual install you can delete all the existing partitions and set up new partitions. The manual partitions to be set up are 
1) Swap (for suspend and hibernate, and if you have low memory resources use the hard disk as virtual memory), twice your ram memory size.
2) System (all program and data files store here), use rest of hard disk, formatted ext3 (the default linux system) and mounted /
The reason why dual boot with Windows is a good idea is that some programs such as games may not work with Linux (including Ubuntu). Some will work with Wine (a linux application), but not all.
If you want to burn your own Ubuntu CD please take a look at [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto").

---

### Post by wicky439 on 2009-03-19
> **Kevbert said:**
> You can tell Ubuntu to use the whole disk when you get to the partition stage or install manually. If you select manual install you can delete all the existing partitions and set up new partitions. The manual partitions to be set up are 
1) Swap (for suspend and hibernate, and if you have low memory resources use the hard disk as virtual memory), twice your ram memory size.
2) System (all program and data files store here), use rest of hard disk, formatted ext3 (the default linux system) and mounted /
The reason why dual boot with Windows is a good idea is that some programs such as games may not work with Linux (including Ubuntu). Some will work with Wine (a linux application), but not all.
If you want to burn your own Ubuntu CD please take a look at [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto").

\
Thanks for such a nice help
Another Question, if i want to come back at WINDOWS from ubuntu then what i have to do?

---

### Post by pbpersson on 2009-03-19
> **wicky439 said:**
> \
Thanks for such a nice help
Another Question, if i want to come back at WINDOWS from ubuntu then what i have to do?

Then you would have to re-install Windows, tell it to use the entire hard drive, therefore completely deleting Ubuntu.

If you think you might ever want to go back to Windows, you should do a dualboot system.

---

### Post by Kevbert on 2009-03-19
Dual boot is the best option. I'm running multiboot on all three of my PCs.
If you decide to come back to Windows (XP) on your PC you will need to reformat the hard disk either FAT32 or NTFS prior to installing Windows as the OS will probably not recognise the ext3 format used by Ubuntu. You can do this via the Live (Ubuntu installation) CD.

---

