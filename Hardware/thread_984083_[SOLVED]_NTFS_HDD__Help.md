---
title: "[SOLVED] NTFS HDD  Help?"
date: 2008-11-16
forum: Hardware
---

### Post by BastardNamban on 2008-11-16
Forgive me for not lurking enough!:(

I finally converted, all out, to 8.0.4 today, after a life of XP. I've wanted to do this for years, having lived with 2 comp sci majors, I caught the open source bug early. I was going to go dual boot, with XP, but I decided to go full on crack, and did HH only, after wiping my HDD for 3 days with DBAN. I still have my XP disk, but I just escaped that pimp- I don't want to go back!

Finally basking in the joy of open source! (already figured out most of basic operation, settings, hotkeys, and liking the high-graphics effects with the windows)

Maybe it wasn't a great idea- see, I'm not a comp sci. guy, I'm a linguist. I live in Japan now, and I know of no one here that even knows of linux, let alone how to help me when I get stuck. I could do nearly anything in XP, now I'm going mad just trying to get basics! Basically, I either get it, or I'm f*cked. So I need everyone's help right now, bad.

I posted my audio problem in the multimedia forum. This is a HDD problem!

I know WHAT the problem is. How to fix it is confusing me, being that I just started linux TODAY.

The problem is, before converting to pure linux, I hadn't known about the filesystem differences. I was wondering how Ubuntu would detect my 2 removable HDDs in Venus external enclosures, but I figured it would be ok, seemingly believing blindly that linux can read anything. I had this vision of linux being almighty, like that dude Jesus is with those Catholic people I hear so much about. Big mistake.

I moved everything over to my 180 GB WD IDE, pictures, docs, mp3s, everything. Even exported firefox bookmark file. The other drive is a WD SATA 500 GB.

I knew about filesystems, but it was one of those things that just nebulously floats around in your head. I didn't know that both drives were encoded with NTFS, due to using them with XP, and that Ubuntu doesn't natively recognize them, and that I'd somehow have to change this before I converted. Now, I'm stuck with a fully wiped laptop, with BOTH external HDDs encoded in NTFS, and NO IDEA how to change them to FAT for linux!

I obviously want to use the drives with windows, occasionally, when I bring them over to my friend's place (a Japanese guy who, until yesterday, didn't even know hotkeys or Firefox existed, and uses XP), so even if I found a solution, I'm afraid they won't work on XP.

How do I get these working? I have no other drives to move the data to, as the FORCE READ method suggested in the post before this and elsewhere, and I have a LOT of stuff on those 2 drives. I am jobless right now, so I can't afford to go buy another HDD to copy to!

What can I do? All my photos, my music, my life is on those disks. Can I somehow convert them to another format without losing any data? Or will I somehow have to intall XP again, on one or both of the disks, and somehow then change them?

Please help.

---

### Post by Skripka on 2008-11-16
There is no need for language--So what happens when you plug those drives in?  Ntfs partitions should be able to be read and mount automagically.

---

### Post by BastardNamban on 2008-11-16
When I connect the drive, I get an error message, saying I cannot mount the drive "Destruction". It gives me two options- 1. if I have windows (I don't have it installed, but I have an XP install disk. I want to
keep XP off this computer if possible. I may have to install it anyway later on for my parametric CAD programs)
2. If you don't have windows, *the force option explained*

I know the force option may work, but it will be read only, and with the name "force", doesn't sound like a good idea if I can help it. I won't even chance ruining my data for a peak in linux of what I already know to be there, corruption free. I need to be able to use it normally. I realize that both Linux & XP can use FAT now, but it looks like FAT has some serious limitations. What can I do, in any case, to convert these to the latest version of FAT?

---

### Post by Skripka on 2008-11-16
There has to be more going on here.

Since you say that you went to the trouble of completely nuking your onboard HDD with DBAN--you didn't do any kind of extra security or such on these drives did you (password/encryption/etc)?  Will these drives read/write on any machine?  If I had to guess without knowing more, another theory is data corruption.


If you don't have it already, I'd suggest you open up Synaptic Package Manager, search for and install ntfsprogs.

---

### Post by twisted_steel on 2008-11-16
It is most likely giving you the error message in the first place because you did not safely remove the external drive when you were in Windows.  Do you have access to a friend's computer over there with Windows?  You should just be able to plug it in, let the computer detect the drive, and then click the safely remove hardware button in the system tray to remove the drive.  I haven't come across any way to fix it within Ubuntu.

---

### Post by BastardNamban on 2008-11-16
Skripka, I never passworded/encrypted the drive. I wiped it totally with a 3 pass DoD short wipe.

Twisted Steel, I think you may be right- I always just switched off the Venus enclosures, not bothering to dismount them. I never ran into problems, but I guess that was bad of me.

To both of you, and anyone else- I do have a friend with WinXP, since it is 2 AM here my time, I'm going to bed. I will plug BOTH drives into his computer tommorrow, and make sure they work. There shouldn't be any data corruption, I just never dismount my drives. I guess that was stupidity.

Just in case, if he has enough space, I will copy my files to his computer, and subsequently convert both HDDs to FAT32 filesystem, and then copy my stuff back, and kill the problem flat. I will also grab, if he has them (since his is a Japanese OS) the MS truetype fonts I didn't know I'd need.

Hopefully this should fix my problems. Is FAT32 that much more unstable than NTFS? I'd like something to work with both XP and Ubuntu, and as far as I can see, FAT32 is all there is. Is there anything better?

Thanks.

---

### Post by Skripka on 2008-11-16
> **BastardNamban said:**
> 

Hopefully this should fix my problems. Is FAT32 that much more unstable than NTFS? I'd like something to work with both XP and Ubuntu, and as far as I can see, FAT32 is all there is. Is there anything better?

Thanks.

FAT32 should never have been a standard file partition setup.  Microsoft should have stopped using it before Windows 3.1 even came out.  There were much better partition schemes in the day-and it was a dumb idea IMHO.

It has numerous problems, and ntfs--if it works as it should is the wat to go.  FAT12/16/32 is the reason why "defragmenting" became the system maintenance necessity on Windows machines of yore (and many folks still do it)--as with FAT, over time data on the drive gets fragmented and severly effects performance.  If you don't do much deleting/shuffling files around-it can be a nice universal access for a drive--but if you do any kind of large scale deleting or moving, drive performance will suffer quickly and severely.

---

### Post by twisted_steel on 2008-11-16
I agree with Skripka - NTFS would be better in your situation than FAT32.  If it were 3-4 years ago, I would have pushed FAT32, but NTFS read/write support is fine these days.  The only problem I have run into when sharing files between Linux and Windows is related to filenames.  NTFS can support additional characters, such as question marks, but Windows does not like them.  I had a file that I created in Linux with a question mark that could not be deleted from Windows.  Other than that, it's been fine.  Note that my NTFS shared disk is installed in my desktop, so I haven't personally dealt with safely removing it.

Ext3 *can* be used in Windows with additional tools, but while they work, they do not support all of the features of the filesystem.  I've only used them to quickly copy a file off of an ext3 partition, but not for writing.

As far as Microsoft's TrueType fonts, you can install most (if not all) of them through Ubuntu without copying them from a Windows install.  See this page for some steps: [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by BastardNamban on 2008-11-19
Ok, to get back, problem fixed. I plugged the drives into a windows box, and dismounted them properly. Now they work in Ubuntu no prob, even when I just shut down the drive! (I don't know how to dismount them in linux yet)

Thanks.

---

### Post by twisted_steel on 2008-11-19
> **BastardNamban said:**
> Now they work in Ubuntu no prob, even when I just shut down the drive! (I don't know how to dismount them in linux yet)

Great to hear that you got it working!  To dismount drives, I usually either right-click on the drive on the desktop if it shows up there and select Unmount Volume (something like that).  The other place to look for the drive is in Computer, which is under the Places menu on the main Gnome menu bar.

---

