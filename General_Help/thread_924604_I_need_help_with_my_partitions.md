---
title: "I need help with my partitions"
date: 2008-09-19
forum: General Help
---

### Post by melancholy00 on 2008-09-19
**Hi**


My Ubuntu is running out of space!
I have a dual-boot system (Windows Vista and Ubuntu Hardy). I really have a partitioning mess, because Im new on this Linux world. The only thing I want to do is take those Unallocated partitions to get fusioned with my Ubuntu partition (which has only 10 GB!), that is, expand the linux SO memory. 

Windows: sda2
Ubuntu: sda3
Swap(Ubuntu) sda4
[IMG]http://i207.photobucket.com/albums/bb179/Lyrero/mypartitions.png[/IMG]

The thing I want is expand the sda3 memory,if possible, take those Unallocated space, thats the way these gray spaces would stop to be a waste of memory. 
Check the png file, it is a snapshot of my partitions...Thanks

---

### Post by stickmangumby on 2008-09-19
I haven't used GParted for a while, but you should be able to simply move your swap partition (/dev/sda4) to the end of the drive, and then expand your Ubuntu partition (/dev/sda3).

Alternatively, you could delete your swap partition, expand your Ubuntu partition to almost the end of the drive, and then create a new swap partition in the remaining space.

As an aside, are you storing files on your Ubuntu partition? Or are you keeping all your files in your Windows partition? If you're not storing files in your Ubuntu partition, ~10GB is probably enough space. Programs don't take up very much space in the Linux world ;).

---

### Post by mb_webguy on 2008-09-19
My suggestion, assuming you have installation discs or installers for Windows and your Windows software, would be to back up your files, repartition your drive, and reinstall everything.  Your partitioning scheme is... less than idea.

For a dual boot, it's generally a good idea to put each OS on a partition just large enough for the OS and installed software, and then have a shared partition for your files.  Ubuntu can be installed comfortably to an 8GB partiion, Windows XP to a 15GB partition, and Vista to a 25GB partiion.  (This is assuming a fairly average amount of installed software.  If you use Windows for gaming and tend to install games to the hard drive rather than using the game disc, then you might want to increase those figures by 5GB or so.  I have Vista with Office 2007, Visual Studio, and a few other large apps installed, and I'm currently using 18GB of the 25GB partition.  As for Ubuntu, I have quite a bit of software installed, and I'm using about 4GB of an 8GB partition

My suggested partitioning scheme for you would be something like this:[LIST]
[*]A 25-30GB NTFS partition for Vista (depending on whether or not you're a gamer)
[*]An 8GB partition for Ubuntu root ("/")
[*]A small (1GB or smaller) ext3 partition for Ubuntu home ("/home")
[*]An NTFS partition using the rest of the drive space (mounted in Ubuntu as something like "/media/Data")
[*]A swap partition equal to 1.25x your system memory
[/LIST]

I would only create the Windows partition during the Windows installation, and create the others during the Ubuntu installation.  That way Windows doesn't try to automatically mount your Ubuntu root, home, and swap partitions.

You want a separate home partition so that if you want to do a clean installation of Ubuntu, you don't lose your settings.  You don't want to mount the NTFS partition as home because NTFS doesn't use Linux-style file permissions, which are necessary for certain configuration files to work properly.

Once you've installed everything, you can boot into Vista, mount the NTFS partition, and move your user folders to the NTFS partition (by right-clicking on each of the folders, selecting Properties, and changing the location).

Then boot into Ubuntu and delete the user folders (e.g. Music, Pictures, Documents, etc.) and replace them with symbolic links to the folders on the NTFS drive.

This way, you don't waste drive space by having the same files stored separately for each operating system, and you can access all of your files no matter which OS you're using.

You'll also want to make sure your Ubuntu root and home partitions aren't mounted under Windows, and that your Windows partition isn't mounted under Ubuntu.  This will prevent you from accidentally damaging one operating system while using the other.

---

### Post by Sef on 2008-09-19
> My suggested partitioning scheme for you would be something like this:
[LIST]
[*]A 25-30GB NTFS partition for Vista (depending on whether or not you're a gamer)
[*]An 8GB partition for Ubuntu root ("/")
[*]A small (1GB or smaller) ext3 partition for Ubuntu home ("/home")
[*]An NTFS partition using the rest of the drive space (mounted in Ubuntu as something like "/media/Data")
[*]A swap partition equal to 1.25x your system memory
[/LIST]
Overall that is good, but I would make a few changes.

1) Root should be 8 - 10 GB.

2) Why have a small home partition if one uses an NTFS partition as home?

3) Swap should not exceed 1 GB.  If you have 2 GB or more, then swap is not really needed unless you do gaming or movie editing or other cpu 
instensive applications.

4) You can have only 4 primary partitions.  If you want more then you need to create an extended partition instead of a primary partition.   The extended partition can be either made after the first primary partition where Vista needs to reside or after the third primary partition.  You can make as many extended partitions as you want.

---

### Post by mb_webguy on 2008-09-20
> **Sef said:**
> 1) Root should be 8 - 10 GB.
As I said in my previous post, I have an 8GB root partition, a fair amount of programs installed (including Office 2003 under Wine), and I'm only using 4GB.  If you want to increase that to 10GB,  more power to you, but in my experience 8GB is sufficient.
> **Sef said:**
> 2) Why have a small home partition if one uses an NTFS partition as home?
Apparently you missed the part of my previous post where I said "You don't want to mount the NTFS partition as home because NTFS doesn't use Linux-style file permissions, which are necessary for certain configuration files to work properly."  Also, if you expose your home directory to Windows, you're putting yourself at risk of accidentally screwing up your settings while in Windows.  As a rule, you should expose one OS to the other as little as possible.
> **Sef said:**
> 3) Swap should not exceed 1 GB.  If you have 2 GB or more, then swap is not really needed unless you do gaming or movie editing or other cpu instensive applications.
Swap should be at least equal to your memory if you want to use hibernation, since the contents of your memory are written to swap when your computer goes into hibernation.  Since that process itself requires some memory, you want swap to be slightly larger than your system's memory.
> **Sef said:**
> 4) You can have only 4 primary partitions.  If you want more then you need to create an extended partition instead of a primary partition.   The extended partition can be either made after the first primary partition where Vista needs to reside or after the third primary partition.  You can make as many extended partitions as you want.
Only Windows requires being installed on a primary partition.  Linux doesn't care.   I would set the shared NTFS partition as primary, just to make sure Windows doesn't have a problem with it.  I don't think Windows should care, as long as the OS itself is on a primary partition, but there's no reason to take chances.

---

### Post by godd4242 on 2008-09-26
I'm having a relatively similar problem. I need to add about a gig off of my linux partition into my windows. I only have 32mb of free space there, at the moment. Obviously unsuitable. 

Note, the warning sign says: Unable to read contents of this filesystem! Also, it's unmounted. Not sure why it says "boot" since I have GRUB setup to give me a choice everytime.

Thanks in advance if anyone has any ideas.

---

### Post by ^^rac on 2008-09-26
Hey! How did you get the black start bars etc?

---

### Post by godd4242 on 2008-09-27
> **^^rac said:**
> Hey! How did you get the black start bars etc?

Don't quite understand what you mean.

---

### Post by ^^rac on 2008-09-27
> **godd4242 said:**
> Don't quite understand what you mean.

I mean, he has like a black theme for Ubuntu (In his screenshot)

Heheeh, its completeley off the subject tho!

Where can one get it?

---

### Post by melancholy00 on 2008-09-27
If you want to check the memory distribution on your NTFS partition, you have to mount it first. I dont know how to do it with the console, but it is only a right click matter.

---

### Post by godd4242 on 2008-09-28
> **^^rac said:**
> I mean, he has like a black theme for Ubuntu (In his screenshot)

Heheeh, its completeley off the subject tho!

Where can one get it?

All it is is a dark picture for my background and then transparent menus. You can do it with right click or gnomeconfig

---

### Post by godd4242 on 2008-09-28
> **melancholy00 said:**
> If you want to check the memory distribution on your NTFS partition, you have to mount it first. I dont know how to do it with the console, but it is only a right click matter.

I don't *think* that's what I want to do. I'm pretty sure I just want to take gigs off my ubuntu and throw them at my Windows.

---

