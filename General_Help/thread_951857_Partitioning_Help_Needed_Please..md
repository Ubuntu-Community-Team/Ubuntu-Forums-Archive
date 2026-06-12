---
title: "Partitioning Help Needed Please."
date: 2008-10-18
forum: General Help
---

### Post by Mortus on 2008-10-18
Ok, so I am a fairly experienced computer kid.  I am the person people go to for computer help, but I never played around with Linux.  I would like to know if I could dual boot set up, so I can use a lot of my mozilla data, plug ins, stuff like that from windows.  Also, it would help if I could transfer 2 gig of music over without using a spare drive.  I heard you could partition it so you have shared data, and I was wondering if someone could tell me how to do that.  And is a "home" directory for ubuntu necessary ( not literally, but it is very good to have )?  Any information on this would be great.

Oh, I have an older computer, 512 RAM, Duo Core Processing ( I am upgrading ram to 1 gig soon....its all I can have... ), and an 80 GB hard drive.

The only things that arent really open source, or just don't run without Wine on linux are Warcraft 3 and Itunes.  I use Pidgin, Firefox, ObjectDock, OpenOffice, and pretty much nothing else..I can't really game on this computer so it is more of a Media/Office computer since I am a student.

Any advice would be nice.

---

### Post by bDerrly on 2008-10-18
Sharing mozilla data will be a challenge at best, if you're new to linux I don't think I would bother with something like that just yet (that and it may not even work, I've never tried).

A home directory is a necessity for users logging in. Generally it will be /home/<user> and is where all of said user's personal data is stored.

You can setup a shared partition fairly easily. I would use fat32 formatting since it has very stable support in linux. Basically when you're going through the install process, when you come to the section where you partition your drives make sure to say that you want to do it manually, make a chunk large enough for your data (2GB you said?) and format it fat32 like I mentioned before.

---

### Post by Mortus on 2008-10-18
Well, actually half my drive is full.  I was just giving an example.  I want to be able to access my "windows" data through linux, and I was wondering if they could just share it, both ways.  I just won't do much on Windows if at all.

I just want to leave my options open.

If I decide later to get rid of windows, or linux for that matter, would I be able to merge the partitions again?

Also, is Wine a viable option for Itunes and may be the occasional game?

**

Also, I realize most of the stuff I have installed that take up space, GIMP, Pidgin, Miro, Firefox, either are on Ubuntu or have an equivalent ( in the case of Miro ).

***

bump

---

### Post by pmooney78 on 2008-12-28
Mounting a Windows partition under Linux is pretty simple ... especially if it's FAT32, but NTFS isn't much harder to get working. I dual-boot Windows 2000/Xubuntu 8.04 and keep my music on an external NTFS disk so it's accessible from both OSes. Linux gives you a lot of control over how your drives are set up and where they're mounted.

This forum has a lot of good tutorials on setting up the /etc/fstab file, which is what you normally need to play with if you want control over mountpoints and options. The Ubuntu installer sets up reasonable options for you when you first install, so you may not need to play with this at all, but it's fairly easy to do if you want more control.

Short answer: shouldn't be a problem getting at information from your Windows drives.

You can resize your partitions on the fly using gparted. Install it from your favorite package manager or type "sudo apt-get install gparted" (no quotes) from a terminal. GParted is pretty good about not screwing things up, but it's always best to make a backup of your data. (I've never had any problems, but ...) Also, I've found it works much more smoothly if you defrag a badly fragmented drive before attempting to repartition (this is easier to do in Windows).

As for "merging the partitions," that may be harder. If what you really mean is that you want to resize the partition and have the information that was previously on the windows (NTFS/FAT32) parition magically appear on a Linux (JFS/ext2/ext3/etc.) partition ... probably not. You do have a couple of options, though: One the one hand, you can just keep your info on a Windows partition and access it fairly easily from Linux. On the other hand, if you decide to give up windows entirely, you could copy your files from the Windows partition onto ... well, something else (DVDs, external hard drive, etc.) ... then erase the Windows partition, grow the Linux partition to fill the gap, and then copy them back. GParted does all of the partition manipulation pretty easily. (Again, good time to make a backup... might as well use DVDs or whatever else you normally use to back your files up.)

I'm just starting to experiment with Wine myself and haven't yet managed to get iTunes running well. (Rumor has it that iTunes 7 works well if you tell Wine to report that Windows 98 is running, but I haven't yet confirmed that myself.) But there are good native Linux replacements: I use GTKpod, but other people rave about Songbird or yamiPOD, or Rhythmbox or Amarok. Quite frankly, I only use my iPod for music and audiobooks, and GTKpod handles both of those very well, and has a visual layout similar to iTunes, which makes it an acceptable drop-in replacement for me. I also keep iTunes running for the twice a month when I boot into Windows. I agree with you: I don't use Windows much, but I like having my music accessible when I do need it.

One of the things I liked about switching to Linux was playing with different alternatives to the Windows programs I've been using.

---

### Post by jacksaff on 2008-12-28
On sharing drives, ntfs works pretty well perfect on linux now. Use FAT if you want to be absolutely sure. You can also get ext2/3 support on windows which works well.
I would use a windows drive for shared data. Windows writes crappy little index files all over your linux disk which is harmless but annoying, plus windows is much less secure so better to leave your linux disks inaccessible to it. It also dooesn't understand unix permissions giving extra opportunities for mess-ups.
I wouldn't share a firefox profile, that's asking for trouble, but sharing the bookmarks file should be harmless. YOu can also share bookmarks and passwords by having them online and using an extension (foxymarks?? cna't remember)

---

