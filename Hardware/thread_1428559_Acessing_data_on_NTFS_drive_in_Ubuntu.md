---
title: "Acessing data on NTFS drive in Ubuntu"
date: 2010-03-12
forum: Hardware
---

### Post by jakster66 on 2010-03-12
Hi there,

I am trying to access data that is on a Raid 5 array in Ubuntu...  There are 4 installed disks (250gig disks) - 3 of which are setup as a Raid 5 array (the 4th is active but unused). These show up as one large drive (474gig)...   Win 2003 server is installed on the logical drive.

I have had an issue with the drive where it is no longer allowing Windows to boot (I receive a disk read error on boot) - basically I unplugged then replugged in a disk which affected the array...  I reactivated the disk and the array seems OK (is listed as "Optimal" in the Raid BIOS) however, the problem persists.

At this stage, I just want to copy the data to a single hard disk if possible and move on. I have started Ubuntu v9.10 from a CD and it shows a disk of the right size (474gig) but there are no folders or files on it....  However, if I view the disk in Gparted, it shows a disk with about 67gig of used space on a 474gig disk (this is correct.).

Can anyone please advise on what I could try at this point.  Hopefully, the data is not lost!

Thanks in advance for any help.

Cheers,
Jack.

---

### Post by 2hot6ft2 on 2010-03-12
> **jakster66 said:**
> However, if I view the disk in Gparted, it shows a disk with about 67gig of used space on a 474gig disk (this is correct.).
On a disk that was used with windows that's not unusual, between RECYCLER, Recycle Bin, and System Volume Information and I think there's a System Recovery too if I'm not mistaken. The folders are hidden.

If there are no normal folders with stuff on it then I wouldn't worry about the used space. If you're going to be using it with linux just format it, even if you want windows to use it no problem it will create new ones as soon as it mounts it.

I always hated the way windows created those things and hid them from me. As if I wouldn't go to folder options and select show hidden files and folders. Bah

In nautilus you can go to View and check Show Hidden Files.

---

### Post by jakster66 on 2010-03-13
Hi,

Thanks so much for responding..... 

I think that there may actually be data in that used space...  Regardless, I would just like to be able to copy that data to another (single) drive just in case there is something there that may be needed at a later date (I don't care about viewing or accessing the data at this stage)...

In Nautilus, the disk shows only the free space (although viewing "Information" for the disk shows 67gig used space and 399gig free space - the same numbers as is seen in Gparted). However, it still does not display the data that is shown in Gparted... This is even with hidden files and folders shown.

One more thing.... when I try the command 'sudo dmraid -tay' it says that there is no raid disk (there are in fact, no drives plugged into IDE or SATA slots - all disk are plugged into the RAID controller card).

Anyway, do you think it is possible to retrieve the data now?  Or is that data now irretrievable?

---

### Post by jakster66 on 2010-03-13
Hi there,

One more thing....  If anone has any suggestions regarding booting the PC into Win Server 2003 (as is installed on the disks in a Raid 5 array), that would also be really useful (as I could then backup the data to another drive from Windows).  I guess this would involve rebuilding the Raid array?

Anyhow, thank you in advance for any suggestions....

Cheers,
Jack.

---

