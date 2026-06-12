---
title: "Can't install Ubuntu on HP Pavilion g6"
date: 2011-09-24
forum: Hardware
---

### Post by saviouz on 2011-09-24
Hi there, I finally got a new laptop and thought of installing Ubuntu alongside with Windows 7, but something seems very wrong with it. Ubuntu won't load in any way. I tried to install it with wubi and by booting it but there's always a problem.

-When I install it with wubi, the installation seems to work, but when I restart the computer the "overeating shutdown" error comes up on the screen, I ignore it and try to load Ubuntu, but then it stops loading (there seems to be something wrong with the network card)

-When I try to install it by booting it, I resize the ntfs partition, but then the free space is labeled as "unusable".

What can I do? I googled the problem and I saw that many are having the same problem with this exact laptop.

Do you think that another Linux Distro would work? (I'm thinking Fedora?)

---

### Post by coffeecat on 2011-09-24
> **saviouz said:**
> Do you think that another Linux Distro would work? (I'm thinking Fedora?)

Another distro won't work any better than Ubuntu if you want to install Linux to its own partitions, because you need to delete one of the HP partitions first, There are four primary partitions, hence the "unusable" free space.

I've only just posted about the same problem in another thread here:

[http://ubuntuforums.org/showthread.php?t=1849335](http://ubuntuforums.org/showthread.php?t=1849335)

Have a look at my post #4. Then follow the link in that and the links in the link and the links in that. :wink: That should give you a good idea of what you need to do.

Sorry - I don't know what the wubi problem is and other distros (except Mint) don't do wubi.

---

### Post by saviouz on 2011-09-24
Thank you very much! =) That was tricky to figure out

---

### Post by coffeecat on 2011-09-24
It would be very unwise not to make backup DVDs. What if your hard drive failed? Relatively new ones do sometimes. If your hard drive failed then your recovery partition would go with it and there would be no way to restore Windows to a replacement hard drive. Unless you contacted HP who would, I am sure, make a significant charge for supplying replacement restore DVDs.

I'm not sure what you mean by making a partition secondary - I guess you mean logical. That wouldn't work. You would have to delete it and recreate it. And then you wouldn't be able to make logical partitions for Linux where you need them, between sda2 and sda3, because the two areas are not contiguous. I simply copied the few files that are on HP_TOOLS into a folder in the C: partition, so that I had a backup.

**EDIT**: @saviouz, you edited your last post while I was typing this one and changed it entirely. It is usually better to repost. I will leave mine as is except for this edit - you seemed reluctant to create restore DVDs.

---

### Post by saviouz on 2011-09-24
I edited simply because I realized I said something pretty dumb =P
I did made the backups and I followed what you said on the other posts, it worked as a charm. Thank you again =)

---

### Post by coffeecat on 2011-09-24
I'm glad it's worked for you. Good luck with using Ubuntu on that machine. :)

---

### Post by quarara on 2011-11-24
Hi,
I need to make a backup copy of Windows 7 on a brand new hp g6 before installing Ubuntu, but I don't know what kind of tool I should use to better perform this task.
If I understand correctly, HP pc's usually have their own backup system, but I think I'll follow coffeecat advise to erase the HP_TOOLS partition, so I think it's better to use Windows 7 tool. Is that correct?

Thank you in advance for your help.

---

### Post by coffeecat on 2011-11-24
> **quarara said:**
> Hi,
I need to make a backup copy of Windows 7 on a brand new hp g6 before installing Ubuntu, but I don't know what kind of tool I should use to better perform this task.
If I understand correctly, HP pc's usually have their own backup system, but I think I'll follow coffeecat advise to erase the HP_TOOLS partition, so I think it's better to use Windows 7 tool. Is that correct?


A few points. My understanding is that the utilities in the hp_tools partition are for creating a set of restore DVDs which duplicate the functionality of the recovery partition. This is to restore the machine to its factory condition - i.e. a working Windows 7 but without your apps, customisations and personal files. It does not backup your system.

I don't know what you mean by the Windows 7 tool, but if you mean creating a recovery CD from within Windows, this is only creates a bootable CD with a set of repair tools. You should create one, but it cannot be used to backup your system.

If you want to backup your Windows 7 system as it is now - all your apps, etc - you need to use an imaging application. A good free - but still proprietary - one is Macrium Reflect which I've used and can recommend:

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

I found the free version could do all that I need - I had no need for the extras in the paid-for versions. I believe you can also use clonezilla which is open-source but I have no experience of this.

---

### Post by quarara on 2011-11-24
First of all, thank you for your very informative reply.

I am not a Windows expert, so the confusion. At this point, I think I'll need to do a set of recovery dvd's. I erroneously the "Create a recovery disc" tool included in Windows 7 as backup.
So, do you suggest me to create those revovery discs with the W7 tool or with the tools provided by HP?

Thanks for your patience. I know it's difficult to deal with newbies, especially if they don't speak your same mothertongue! :)

---

### Post by coffeecat on 2011-11-24
Do all three. You can only create a repair/recovery CD from within Windows 7 itself. This is very limited, but something you should have. The recovery DVDs you create with the HP software is something else, and an image from imaging software such as Macrium is something else again.

---

### Post by quarara on 2011-11-26
I have done all three as you suggested me :)
But i have a proble right now. I have removed HP_TOOLS partition, but now I have the recovery partition in the middle of my hard drive.
Here's a picture of the situation I'm stuck at now.

Thanks for your help.

---

### Post by coffeecat on 2011-11-26
You have approx 4GB "lost" at the end of what looks to be 500GB drive. Forget about it. Better that than move the recovery partition and risk corrupting it. Use Gparted (don't use Windows Disk Management) to create an extended partition in the 216.97 space and then you'll be able to create the logical partitions you need for Ubuntu.

---

### Post by quarara on 2011-11-26
Um.. I think you're right.
I'm shrinking Win7 a little more and then I will be ready to install Ubuntu.

Thanks for the support!

---

### Post by quarara on 2011-11-27
The installation went just fine. Thanks for your help!

---

