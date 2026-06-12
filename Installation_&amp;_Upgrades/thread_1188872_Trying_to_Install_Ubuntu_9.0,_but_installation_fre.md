---
title: "Trying to Install Ubuntu 9.0, but installation freezes"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Insidious311 on 2009-06-16
I'm fairly new to the Ubuntu OS and Linux in general. I had Ubuntu 7.10 installed and had to reinstall it. I had problems with it not recognizing the partitions on one of my drives correctly, so I decided to look for a new version.
 
Now I downloaded the CD Iso for Ubuntu 9.0 64-bit, but the installation keeps freezing after I select my keyboard layout (ie after the Partition Manager 'finishes' scanning my drives).
 
No error message is given, just the cursor animation freezes as well as the entire system. I've tried booting into the OS first, then clicking on the install icon on the desktop, and I have also tried installing directly from the choices at the beginning.
 
I have a Intel 945G Motherboard with 4 GB Ram. I am quintiple (sp?) booting, here is what my drives look like:
 
[Drive 1-IDE] 300GB
Partition 1: 50GB NTFS(where I want to instal ubuntu)
Partition 2: 50GB NTFSwhere I want to instal CentOS, another linux distro)
Partition 3: 100GB MacOS X
Partition 4: 100GB NTFS (extra storage with file I do not want destroyed)
 
[Drive 2-SATA] 250GB
Partition 1: 200GB Vista Ultimate 64-bit
Partition 2: 50GB Windows XP SP3 
 
The first 2 Partitions on the IDE drive are formatted NTFS because I couldn't get the Ubuntu 7.10 to recognize it with all 4 Partitions, it would just count it as one drive, while the SATA drive had the correct Partitions displayed. But now I can't even get Ubuntu 9.0 to do anything.
 
Any help or ideas would be greatly appreciated. Thanks in advance.
 
(PS- Quick question, what is the dofference between Ubuntu,Kubuntu, Xbuntu ... etc?)

---

### Post by masux594 on 2009-06-16
Well, i start use ubuntu from 2-3 months .. but even if I'm a "beginner", i have only one question to ask you .. Installing ubuntu on **NTFS**?

I think u must read some guide on [Install Ubuntu]("http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-desktop-installation-guide.html"), or try googling!

A

---

### Post by Togezo on 2009-06-16
Maybe a problem with the download? Did you go through the whole process of doing an md5 checksum etc.? A problem with the .iso file seems most likely.

---

### Post by masux594 on 2009-06-16
In your case [this guide]("http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition/") sounds like better! Partitioning HDD manually for install ubuntu 9.04..

A

---

### Post by Insidious311 on 2009-06-16
I REALISE that NTFS is not what is needed for a Linux installation. I'm sorry, I should have been clear on this point: The reason I formatted as such is because Ubuntu 7.10 installation was not seeing any partitions on my IDE drive so I was trying different file systems to see if any would be picked up by the installation. It just so happened that NTFS was the last file system I tried before giving up and trying the Ubuntu 9.0 upgrade.
 
But like I said the Partition Manager crashes and freezes the whole system, I don't even get to see any of my drives.
 
Sorry I also fogot to mention I also checked the disc with the verify option at the beginning; it turned out to be intacted.
 
I will try the guides you guys have suggested.
 
Thank you for the replies.

---

### Post by Insidious311 on 2009-06-16
Ok guys, I have looked at the guides you've suggested. The problem is the installation freezes at Step 3 (the screen that asks for your keyboard).
 
While on that screen, I click Forward. A dialog  with a progress bar appears (I guess from Partition Manager)  and completes. Before transitioning to the next step, the computer freezes (stays on the Step 3 page). 
 
This happens whether I start the installation from the desktop or the boot screen.
 
I already have the drive partitioned how I want, I used Acronis Disk Director while booted into Vista, I just need to be able to continue the installation and for Partition Manager to see my partitions.
 
Thanks again.

---

### Post by Insidious311 on 2009-06-17
Alright I fiddled around with it some more today, I was able to get to the Partition Manager screen by disconnecting my SATA drive and pressing F4 and selecting boot with 'Safe Graphics' or something like that.
 
Unfortunately, Partition Manager doesn't read any of the partitions on my IDE drive. 
 
Any ideas?
 
Thanks again.

---

### Post by lisati on 2009-06-17
BTW: it's **9.04**, *not* _9.0_

---

### Post by masux594 on 2009-06-17
Hmm.. In my case i have either vista and jaunty that can read/write datas from a shared partition.. In your case, i don't understand why this problem happen.. Maybe your Hdd partition table has been corrupted from the partiton manager u use before.. Maybe an error in some hdd sector [for older Hdds] that doesen't allow ubuntu partition manager to recognize the hdd's existing partitions.. i suggest u to format all the Hdd with a **single **partition [or ][it doesen't matter the kind, NTFS].. Obvious that if u have some data u want to keep, do a copy in anther hdd o something else.. and after formatting, re-try to install ubuntu, then unallocate the partition u have created before and follow the guide.. If u have some OS already installed on this Hdd, it doesen't matter, when i say "format all the hdd", i mean "all the space that u don't use, or all the space u need to run others OS that u sey before"

A

---

### Post by Insidious311 on 2009-06-17
> **lisati said:**
> BTW: it's **9.04**, *not* _9.0_
 
 
WOW thanks... I hope I didn't confuse anybody here..
 
I really HOPE you and I weren't the only ones who knew what OS I was talking about when I said ubuntu 9.0 and not ubuntu 9.04...
 
Wait I'm sorry, not ubuntu 9.04 , what I meant to say was Ubuntu 9.04...
 
**** are they the same thing? 'cause in some places the 'u' is uppercase and in others it's not...so...?....
 
 
Anyways, I think my only choice is to do what masux594 suggested, there is another user here with a similar problem and no one seems to have found a solution.
 
 
Thanks anyways for those of you who *tried* to help, your advice was much appreciated. :popcorn:
Have a good one!

---

### Post by masux594 on 2009-06-17
With u i mean "you" .. =)

A

P.s. Oki, i know.. it was a joke, now i understand ..

---

