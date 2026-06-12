---
title: "What is the best file system to share data for linux and windows?"
date: 2008-08-30
forum: General Help
---

### Post by theedudenator on 2008-08-30
I have a harddrive I use for working with files and such.
This is located on my main WinXP machine

When I had WinXp on my laptop I just shared them and had no issues.

Now that I have Ubuntu on my laptop, what is the best file system to be able to read and write from both?

---

### Post by Oldsoldier2003 on 2008-08-30
For a dual boot windows/ubuntu system, I prefer making the shared data directories NTFS. Others will say use the windows driver that allows you to read write ext2/3 filesystems, but in my experience Linux support of NTFS is better than windows support of ext2/3. My reasoning here is the overall operating system (in)stabilty of windows makes writing to your ext2/3 fs more risky than writing to NTFS from linux.

---

### Post by theedudenator on 2008-08-30
This is not a dual boot system.

This is a main PC with Windows and a laptop with linux.

I want to share harddrives on the Windows machine, what format should they be?

Will Ubuntu read/write NTFS over a network?

---

### Post by Zorael on 2008-08-30
Well, the "standard" way of sharing data over a network is to use [samba](http://en.wikipedia.org/wiki/Samba_(software)). What filesystem the partitions itself are using doesn't matter; samba translates it to its own protocol. You will run into some quirks if you share content on a filesystem which differentiate between upper- and lowercase characters and you try to open either in Windows, though.

Samba is supposedly slowish. [NFS](http://en.wikipedia.org/wiki/Network_File_System_(protocol)) is supposedly faster, though I don't have any experience settings up such shares myself. There's likely some tinkering involved to be able to browse them in Windows, but I can't imagine it being impossible.

---

### Post by mb_webguy on 2008-08-30
If you're wanting to share files from the Windows PC, just share the folders and you can connect to them over the network.  

You can do the same with folders on Linux to share them with Windows.  Just right-click a folder in Nautilus and select "Sharing Options".  In the window that pops up, check the box next to "Share This Folder" and click "Create Share".  You will probably be prompted to install some packages, which you can do automatically by clicking Ok (or Continue, or whatever the affirmative button is, I don't remember).  If you do have to install the packages, you'll need to log out (or reboot) before you can share the folder.  Do so, then repeat the process described above.  This time, the folder will be shared, and you'll be able to access the folder from Windows (though you'll have to enter your Linux login information the first time you try to connect from Windows).

---

### Post by theedudenator on 2008-08-30
I have done all of this.

But it is not showing the folders that I can share when I go to Places - Network - Windows Network.

Windows Network is blank, it is not seeing anything on my XP machine.

---

### Post by theedudenator on 2008-08-30
I also shared a directory on the Ubuntu machine, but WinXP cannot even see my laptop in the Workgroups.

BUT

 I can ping each machine and connect to each remotely.

Seems rather odd.

I have another laptop with WinXP and it works fine with my main winXP machine.

I think it is some configuration in Ubuntu or SAMBA

---

### Post by motang on 2008-08-30
[FONT="Comic Sans MS"]I would go with *[COLOR="DarkRed"]Oldsoldier2003[/COLOR]*, that is what I do at home as one of my computer is Win XP Pro and I have the drive in NTFS and I share it.  Ubuntu and Kubuntu seems to work fine and they both see the shared drive w/o any problems.[/FONT]

---

### Post by Zorael on 2008-08-30
> **theedudenator said:**
> I also shared a directory on the Ubuntu machine, but WinXP cannot even see my laptop in the Workgroups.

BUT

 I can ping each machine and connect to each remotely.

Seems rather odd.

I have another laptop with WinXP and it works fine with my main winXP machine.

I think it is some configuration in Ubuntu or SAMBA
Make sure they're both in the same workgroup, I think Windows is a bit picky regarding that.

On your Ubuntu machine, run **smbtree** in a terminal and let us know what it says. You don't need to enter any password, just enter past that one. If there are errors output, we'd need to know those.

Lastly, I believe you want to make sure you have the **smbclient** package installed.

---

### Post by mike2357 on 2008-08-30
> But it is not showing the folders that I can share when I go to Places - Network - Windows Network.

I have the same problem.  The work around was to go to Places -> Connect to Server and then select Windows Share.  I typed in the Server and Share names as set up on my Windows system, and the problem was solved.  Then, in the Nautilus window, I selected Bookmarks -> Add Bookmark so my Windows system is permanently in my Places menu.

---

