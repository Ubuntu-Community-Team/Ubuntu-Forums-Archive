---
title: "how to install ubuntu on a computer with no OS.."
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by dorado29 on 2009-02-14
hey guys im a newb when it comes to this but i just assembled a new desktop (ordered parts from newegg). now that its up and running i have no idea how to install any linux based OS on it (or any OS for that matter). I searched around a bit and only found instructions for installing linux on a computer that already has an OS loaded on it... i'm pretty sure that my computer doesn't fit in that category. How do i load ubuntu onto it and not have it run from the disc? also, would a flash drive work instead of a disc?

I have tried loading mandriva onto it just because i had a mandriva disc lying around but i could only get it to boot from the disc, i couldn't figure out how to load it into the computer's memory. 

one last thing: i have 4 gigs of memory. will ubuntu utilize all 4 or is it like windows XP?

---

### Post by hansdown on 2009-02-14
Hi dorado29.

You should be able to boot from the ubuntu disk, and get to a window with choices to install, etc.

Here is an install guide for ubuntu 8.04.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by ilioscio on 2009-02-14
64bit ubuntu address all 4 gigs of ram but 32 doesn't

---

### Post by MarblePanther on 2009-02-14
No operating system that is "worth its salt" (that I can think of) requires another operating system to install itself.  (except in special circumstances--like Windows 1,2,and 3 were with DOS,etc...)

Typically with any OS, you boot from some sort of media (can be floppies, CD/DVD, usb, etc...) and it gives you an installer or command line to install from the media to your hard disk (RAM is an important factor).

Ubuntu is no different.  With the livecd, you can boot straight to the installer or enter a live Ubuntu environment to play around with before you install.

---

### Post by dorado29 on 2009-02-14
okay good, i already had the 64 bit downloaded, it's the 8.10 version though. will burning that to a cd and following the same steps from the 8.4 tutorial work?

im trying to figure out how to burn and iso image. what does this line mean; "Select the Ubuntu **CD image file** you want to use, then click 'Open'."

where is the cd image file? is it the entire contents of the folder when it's unzipped?

---

### Post by MarblePanther on 2009-02-14
> **dorado29 said:**
> okay good, i already had the 64 bit downloaded, it's the 8.10 version though. will burning that to a cd and following the same steps from the 8.4 tutorial work?

im trying to figure out how to burn and iso image. what does this line mean; "Select the Ubuntu **CD image file** you want to use, then click 'Open'."

where is the cd image file? is it the entire contents of the folder when it's unzipped?

Simply select the .iso file you just downloaded and burn it.

---

### Post by m_duck on 2009-02-14
The image file it is referring to is the .iso that you downloaded. You need to burn it to CD as an image file and not just burn the file to a disk...

If your are in Windows, you can use a program like [InfraRecorder](http://infrarecorder.org/?page_id=5) to do it.

---

### Post by dorado29 on 2009-02-15
okay im trying to install ubuntu onto my computer from the disc (8.10) and im at step 4 of 7, the "preparing partitions" step. every option is grayed out and i cant click anything except quit, back and forward. when i click forward it says no root file system is defined and to correct from the partitioning menu. assuming that step 4 is the partitioning menu, how do i correct it if everything is grayed out? i thought partitioning was only necessary when you have >1 OS on a computer?

edit: after looking at this [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) and [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) i found that dynex isn't on the list. is it possible for ubuntu to recognize a dynex card?

it's this one [http://www.bestbuy.com/site/olspage.jsp?skuId=8545005&type=product&id=1188560188217](http://www.bestbuy.com/site/olspage.jsp?skuId=8545005&type=product&id=1188560188217) to be exact

---

### Post by theozzlives on 2009-02-15
You want to make a 10 or 20 GB partition (ext3) and make the mount point root (/). You want a swap partition at least 4 GB. Make a partition using the rest of the space ext3 and mount point of /home. Then click forward.

---

### Post by hansdown on 2009-02-15
Is it this screen dorado29?

---

### Post by dorado29 on 2009-02-15
no. it was a screen from the actual ubuntu installer. im guessing you can't partition from within the installer so thats probably a program accessed from the desktop right? this is my first time using ubuntu so i have no idea where to go to partition and after some brief searching all the instructions just assumed i knew how to get to "/dev/sdc - GParted" program (i think its a program)

its this screenshot here that i want to get to now [https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions)

---

### Post by hansdown on 2009-02-15
The install disk can load ubuntu without having to play with partitioning at all.

---

### Post by hansdown on 2009-02-15
This video is a complete step by step tutorial.

[http://www.youtube.com/watch?v=IlQGk0PcqbI](http://www.youtube.com/watch?v=IlQGk0PcqbI)

---

### Post by dorado29 on 2009-02-15
[IMG]http://i226.photobucket.com/albums/dd97/dorado29/IMG_0051.jpg[/IMG]

sorry for the low  quality pic but thats what step 4 looks like

perhaps my hard drive isnt being recognized by my computer or it's plugged in wrong?

---

### Post by dorado29 on 2009-02-16
anyone? when i get to step 4 it looks like my hd isnt even recognized

---

### Post by pistehead on 2009-02-23
Hi everyone i'm new here.
Trying to get into this so I can use it instead of vista.
I like what i've played with so far :-)
I'm here cos i have the same problem as the author.
On step 4 of 7 my screen looks like his picture.
I've managed to change the partition to ext3 instead of ntfs.
I know i need to mount this partition too, with /
God can i find a way to do this.
Anyone know why we are getting no partitions showing in step 4 of 7?
like the author says clicking forward just returns..
no root file system is defined please correct this from the partitioning menu.
Please help :-)
I'll of course keep searching.

---

