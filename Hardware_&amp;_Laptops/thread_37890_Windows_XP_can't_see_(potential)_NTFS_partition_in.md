---
title: "Windows XP can't see (potential) NTFS partition in my Ubuntu rive"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by quasar on 2005-05-29
Hi everybody,

   brand new to the forum. Thanks everyone in advance for your help, Thanks to the developers and the community for Ubuntu, an excellent product which I'm very happy with.

   **My problem:**  WinXP (which I'm tied to for income-related reasons) can't see my other hard drive. I would like to have an NTFS partition on one drive, with XP on the other drive. XP can't see the other drive at all, so I can't seem to even format a partition on my other drive from XP.

   **My setup:** I have an 80 GB hard drive containing two Linux paritions and a Linux swap partition. This is my primary master (henceforth the big drive) . I have a 40GB drive containing my XP partition and the 8MB partition that XP makes due to the lameness of its bootloader. This is my primary slave (henceforth the small drive).

   Let me make it clear that I have NO PROBLEM BOOTING EITHER PARTITION, **This is not a bootup problem**. This is a hard drive access problem. I just want to move some of the data in my XP (small) drive to my other drive so I can justify my purchase. I would also like to access the data in my big drive from my small drive, so I can copy data back and forth across drives while running Windows.

   In my big drive, I need to keep only one of the Linux partitions. I wanted to cream the other one and turn it into a Win partition, but I can't because Win can't even see it.

   **What is my question:** how do I get WinXP to see my other drive with its partitions, so I can format over the one I don't need and turn it into a D: drive that I can write back and forth while running Windows. Any solution that involves re-installing WinXP is unfortunately not acceptable because the data on my WinXP partition pays the rent.

   If this is an question whose answer has been posted in FAQs or other forums, please don't get angry enough to not provide any answer at all if you know it. I'm *really* new and even an anchor with no other words wll be huge help.

   Thanks to all in advance once more for your help. Best,

       QUASAR

---

### Post by andlinux21 on 2005-05-29
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Sounds like you may need a partition tool like Partition Magic.  That will take care of removing the other version of linux you dont want. As far as you accessing the XP data i am not sure how you could do that... :-# [/COLOR][/SIZE][/FONT]

---

### Post by clb137 on 2005-05-29
[QUOTE=quasar]Hi everybody,

  B]What is my question:[/B] how do I get WinXP to see my other drive with its partitions, so I can format over the one I don't need and turn it into a D: drive that I can write back and forth while running Windows. Any solution that involves re-installing WinXP is unfortunately not acceptable because the data on my WinXP partition pays the rent.

   
       QUASAR[/QUOTE]

Hi Quasar,


can you please give me a complete simply break down of you drive setup

IE C 40g ntfs,  d 20g fat

then i may be able to understand your problema little better

thanks

clinton

---

### Post by quasar on 2005-05-29
[QUOTE=clb137]Hi Quasar,


can you please give me a complete simply break down of you drive setup

IE C 40g ntfs,  d 20g fat

then i may be able to understand your problema little better

thanks

clinton[/QUOTE]

Hi Clinton,

   thanks for your interest.

   Primary Master: 80GB. Partitions: 30GB Ubuntu + 48GB Ubuntu + 2GB Linux Swap.

   Primary slave: 40GB NTFS + 8MB Win boot partition.

   My runnning Ububtu system is in the 30GB partition. I want to turn the 48GB one into an NTFS part. that I can use to share data between Win and Linux.

   Andylinux's proposed solution above does not seem viable because Windows cannot see at all my primary master drive, let alone creating new partitions in it. 

   Is there a way to create an NTFS fs under linux? I tried mkfs.ntfs and that doesn't seem to exist. Besides I'm very doubtful that that alone is going to render the partition visible. I think I should somehow "tell" windows to look in the other drive... maybe not. I don't know. Ideas?

   Thanks both of you gents fos your replies. Best,

     QUASAR

---

### Post by grim42 on 2005-05-29
What do you mean by Windows cannot see the drive?

Have you tried the Computer Management console in XP?

Go to "Control Panel" then "Administrative Tools" then "Computer Management".

In the window that opens, select "Disk Management". This should show all hard drives and their partitions.

Windows Explorer will only show Windows partitions, so you'll need to select the 48GB partition and reformat it as NTFS. (Make sure everything important on there is copied somewhere else first.) Only then will the drive show up in Explorer as D: or whatever.

Sorrry if you have tried this and I didn't understand.

(BTW: I'm pretty sure you CANNOT create an NTFS filesystem with Linux)

---

### Post by khola on 2005-05-30
NTFS is a MS proprietary file system. Writing to ntfs partition from a linux is experimental at best. If you really need a partition (to save data) that can be accessed easily, ie read/write,  by both Windows and Linux,  I would suggest you use FAT instead of ntfs. 
You will probably have to change your /etc/fstab for the FAT partition so that your normal user can write to it. For example:
 /dev/hda2    /mnt/d      vfat        defaults,umask=0000             0 0

---

### Post by clb137 on 2005-05-30
hi Quasar

1.  You will be able to see your linux partitions on ur winbox, however you will have to install and configure 'samba' This will be read only though

2. Writing to NTFS form Linux is not good (It is possible though not recommeded) You will stand a very high chance of corrupting ur NTFS partition.

If you reall need to write files back on forth between Linux/Win  I sggest setting up FAT partions on both boxes, that way ALL OS can read and write with no problems.


hope this makes it a little clearer


clinton

---

### Post by quasar on 2005-06-04
Hi Everybody,

   thanks a lot for your help and interest. Sorry I've been away from the formus for so long, leaving the thread astray. Busy...

   I've fixed the problem. I had no idea of the existence of the Windows Compuater MAnagement Console, that eventually fixed the problem. Deleted partition, re-created it as Fat32, formatted, asssigned letter drive, and voila!

   Thanks a lot once more... problem solved, thread closed.

    QUASAR

---

