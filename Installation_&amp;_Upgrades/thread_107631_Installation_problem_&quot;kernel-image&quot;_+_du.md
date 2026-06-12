---
title: "Installation problem &quot;kernel-image&quot; + dual booting"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by myafro on 2005-12-23
Heres the problem: I have 2 HDDS, a 120gb one which has WinXP on it, and all of my documents. I also have a 6GB HDD which I hope to install Ubuntu on. I sent off for some CDs and they arrived fine. The Live CD works but whenever I try to install the whole thing I keep getting the same error:

[I]"Can`t find installable kernel in defined APT sources
Default kernel package is "kernel-image"
You can try to continue but this error is probably fatal..."[/I]

Now I have done some searching on the forum, trying as many of the ideas that I understood. I tried making the CD drive master and the HDD slave, moved all the drives round and stuff but I still cant get it to install. 

I really need some help on this problem, but I warn you I am fairly knew to linux and BIOS stuff so if you can help please be patient. 

Up to the point where I get this error everything else runs fine. Is there a way to bipass this section and install it later, or can you offer any other advice?

My second problem is that I want to be able to access the same files with both Ubuntu and WinXP. XP is set on the NTFS system, and linux on ext3 or whatever the default is. Does this mean that with my current setup of hdd1:winxp/files/ntfs and hdd2:linux/ext3 I will have problems reading the files with both O/Ss? If I partition the WinXP drive in order to free up the documents from the OS, will it allow me to see them from ubuntu,  or more importantly will it wipe over the hard drive itself? 

If there is no way to run both with this setup, would buying another drive help - would I be able to store files on it that could be read from both linux and windows? What file system would I need that drive set to etc.

If you need any more information, just ask.

If you can answer both these questions. it will be AWESOME. Thanks in advance :)

---

### Post by Ocxic on 2005-12-23
ubuntu will be able to read NTFS drive only, and there is a prog you can download to acces you ext2/3 ubuntu partions for winXP just google it

---

### Post by myafro on 2006-01-04
Ok so I finally managed to install it. Now before I can really start seeing what it can do, I have two final problems.
1) the GRUB loader - instead of it automatically running linux I want it to automatically run Windows - at least till I get used to linux. I have no idea how to do this.
2) Ubuntu is not recognising my other hard drive, and therefore not recognising my files. Is there a problem with the hard drive not being mounted? How would I go about making linux notice this hard drive. Thanks.

---

### Post by jdjuice on 2006-01-08
[QUOTE=myafro]Ok so I finally managed to install it. Now before I can really start seeing what it can do, I have two final problems.
1) the GRUB loader - instead of it automatically running linux I want it to automatically run Windows - at least till I get used to linux. I have no idea how to do this.
2) Ubuntu is not recognising my other hard drive, and therefore not recognising my files. Is there a problem with the hard drive not being mounted? How would I go about making linux notice this hard drive. Thanks.[/QUOTE]


I'm having a similar problem with the 'kernel-image' and I can't get it to work.  What fixed it?  For your first question, I think there's a settings panel somewhere in gnome that lets you customize grub a bit.  That's the way it is in Suse and I'd imagine it's similar in Ubuntu, if only I could get it to work.  As for the hard drive, I don't know.

---

### Post by myafro on 2006-01-10
1) To fix the kernel image problem, I burned the disc at like 2x. To be honest I didnt think it would work. I had presumed the ones sent to me would work fine, but I gave burning it ago on my computer, but the slowest it would burn was 8x. Which actually got me to around 80% of the installation. So I burnt the CD on an older pc at 2x and it installed fine.
2) I found out how to fix the GRUB problem. Opened menu.lst, cut the windows entry to the top of the OS list, and commented out all the other linux bits I dont need (kept in normal mode, recovery mode and memtest).
3) The hard drive problem. I solved this by following a tutorial I found somewhere. The next problem I encountered was not being able to play music from the windows HDD. But I found out that was a common issue too, found another tutorial and It was fixed.

So to sum up, burn it as slow speed as you can.

---

