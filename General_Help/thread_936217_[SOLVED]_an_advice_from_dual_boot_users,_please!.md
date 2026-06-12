---
title: "[SOLVED] an advice from dual boot users, please!"
date: 2008-10-02
forum: General Help
---

### Post by ieBrazil on 2008-10-02
You see, I backed up my files, after installed XP Professional and then Ubuntu, after that, I upgraded it to 8.04.

My case is: do you advice me to put my files back on my laptop on the XP-OS or on the Linux-OS?

What are the pros and against, it this is the correct expression?

Thank you in advance.





ieBrazil, new fan of Ubuntu.

---

### Post by LowSky on 2008-10-02
what kind of files? Documents and music and media? Why not create a entirely seperate partition that both OSes can use. that way both OSes will have access.

---

### Post by Nabanna on 2008-10-02
> **ieBrazil said:**
> You see, I backed up my files, after installed XP Professional and then Ubuntu, after that, I upgraded it to 8.04.

My case is: do you advice me to put my files back on my laptop on the XP-OS or on the Linux-OS?

What are the pros and against, it this is the correct expression?

Thank you in advance.





ieBrazil, new fan of Ubuntu.

IMHO if you intend to use these files on both the systems i.e. XP and Ubuntu, you must keep them in XP partitions, as XP does not recognize ext3(or Linux) file format..

---

### Post by ieBrazil on 2008-10-02
> **LowSky said:**
> what kind of files? Documents and music and media? Why not create a entirely seperate partition that both OSes can use. that way both OSes will have access.

Is that really possible? Never thought about that, man.

My my HD of 80... already has two partitions. You re telling me to create a third one? I dont think so...

Yes, office files, music and vids... that's all. Ah, pictures too...

---

### Post by SuperSonic4 on 2008-10-02
What's wrong with making a third partition? I've had 6 partitions on a drive sometimes :bleh: (2 were extended) 

And yeah it's possible.

---

### Post by kokkus on 2008-10-02
I think winxp will have problems to recognize other partitions. I world create 2 partitions (windows and linux), put your private data on your winxp partition and read that partition from ubuntu.
You can let windows read linux partitions too but that's a big security risk to take. I wouldn't do it.
But linux can recognize all your data, partitions and disks so that's my advice. Good luck:)

---

### Post by Herman on 2008-10-02
It's a good idea to use a third partition for keeping files for both operating systems because Ubuntu is not affected by viruses. 
A virus could be accidentally downloaded in Ubuntu but since it can't hurt Ubuntu, you might not know there is a virus hiding in a file. Then if you put it right into Windows, the virus could destroy Windows if you run it.
Therefore it is a good idea for Windows users to keep their files on a separate partition where they can scan them for viruses without needing to put  those files inside Windows first.
Just because the virus scanner fails to detect a virus doesn't not mean your Windows operating system is 'safe' though.
The only way to be safe is to stop using Windows if you can, or use it less, and use Ubuntu instead.

---

### Post by ieBrazil on 2008-10-03
> **Herman said:**
> It's a good idea to use a third partition for keeping files for both operating systems because Ubuntu is not affected by viruses. 
A virus could be accidentally downloaded in Ubuntu but since it can't hurt Ubuntu, you might not know there is a virus hiding in a file. Then if you put it right into Windows, the virus could destroy Windows if you run it.
Therefore it is a good idea for Windows users to keep their files on a separate partition where they can scan them for viruses without needing to put  those files inside Windows first.
Just because the virus scanner fails to detect a virus doesn't not mean your Windows operating system is 'safe' though.
The only way to be safe is to stop using Windows if you can, or use it less, and use Ubuntu instead.

oh sure, I am thinking seriously about not using XP anymore and yes witching completely into Ubuntu... but I am bit afraid yet. You know, that feeling we have when we are before something new, unknown.

anywya, thank you.

---

### Post by Herman on 2008-10-03
:D Okay. It is better to change slowly than to force yourself.

I'll tell you how I was converted, I already had Ubuntu, but I still used Windowx XP a lot. 
Then one day I tried an experiment.

I booted into Windows and ran my anti virus program, and then as many of my adware, spyware and malware removing tools as I had, two or three times each until my system was really cleaned out.
Those programs found a lot of bad things to remove in my Windows XP. It was a lot of work. 
I already knew that every time I used Windows XP to go browsing the internet it would pick up another load of bad stuff and would have to to run all those programs all over again.

I decided not to use Windows XP on the internet any more at all, except for 'trusted' sites like Windows Update and other update sites for all the extra protection and cleaning softwares Windows needs. 
When I wanted to go look for something on the internet, I booted into Ubuntu for that.

What I found out was that Windows XP didn't get any more viruses, adware, spyware and malware at all. All my scans in Windows kept coming up clean.

Then one day I went to boot into Windows XP and I could not remember my password.
What happened was, since I mainly use my computer for internet browsing, I had decided to boot Ubuntu more and more often. As I learned how to do everything in Ubuntu and found that it was better, I had less need to reboot to do anything in the other system. Being too lazy, to reboot all the time, I had converted myself to Ubuntu without even realizing it myself. I didn't even realize it had happened until the day I realized I counldn't even remember the password.

I still have a few computers with Windows XP in them, but the only time I ever boot them is when someone asks me a question about dual booting and I need to check up on something or do an experiment to make sure I'm giving someone the right advice.

My newest computer is one I assembled myself, it's twice as powerful and it cost me less than half price because I don't need to buy the operating system or any other software anymore, I only use Linux. :D

So if sometimes you try to do something in Linux and you have trouble, keep on trying, don't give up. It's worth it later on.

Regards, Herman :D

---

### Post by jvin248 on 2008-10-05
If you're not technically minded or short on time... I'd suggest getting an external USB Hard Disk Drive and using that under both Windows and Linux for your common files, transferring your existing files to those.

If you're interested in digging in then create another partition that is "fat32" (or maybe "fat16/12" or what option there might be for an older "non-ntfs" Windows format) - ntfs can be risky under Linux (read/write is implemented in many versions of Linux but it's another layer of risk and complexity).

My current setup is a dual boot, with a separate "/home" partition for Xubuntu.  I only use the Windows partition to watch a couple of network shows that I do not have Linux workarounds for yet. The separate /home partition cannot be read by Windows but I don't do anything important in Windows anymore.  The separate /home partition allows me to easily upgrade the Linux OS side too (5.10, 6.10, 7.10, 8.04, and two different computer hardware boxes along the way).

Another layer of adventure instead of the USB HDD, is look at FreeNAS.org, and repurpose an old computer box (like old 1998 Pentium 2 or newer) with a couple of hard drives and use that as a network storage system for all your files that can be accessed from both Windows and Linux.

Good luck!

---

