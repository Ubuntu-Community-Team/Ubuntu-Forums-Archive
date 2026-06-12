---
title: "Worth having separate /home partition *and* docs partition?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2009-10-31
Hello all

I've had a separate /home partition for several version of Ubuntu now.  Although it is helpful, I find that when I upgrade there are settings hanging around which sometimes cause trouble.

I'm about to upgrade my desktop to 9.10 and I'd like to sort this out before going ahead.

It occurred to me that I could have 2 separate partitions for documents/settings - one where /home lives and another where my actual documents live. This way I could scrub the /home partition when I upgrade, and have a fresh set of settings, then symlink the Documents/Movies/Downloads/Pictures/Music folders in the new /home/user folder to the appropriate folders on the documents partition. Any settings that I specifically want to save, e.g. the .fonts folder or my firefox profile, I can copy to the Docs partition before I reinstall then copy back over once the new Ubuntu is up and running.

I was thinking the /home partition in this scenario could have, say, 2GB. That should (I think) be enough for a sizeable Firefox profile and the settings for other programs.  The documents partition would therefore be pretty big (e.g. 60GB) which is plenty of space for photos and music etc. It would also mean that when I browse it from within Windows using ext2fs, I won't see all the hidden folders in /home, just the nice few folders containing all my stuff (Documents, Movies, Music, Pictures etc).

Seems like quite an elegant solution to me. What do you guys think? Have I missed anything that breaks this idea?

---

### Post by melat0nin on 2009-10-31
Anybody? The installer won't allow me to mount the existing /home partition without formatting it, which is no good because it's full of my stuff(!)

---

### Post by arpanaut on 2009-10-31
Interesting, I've been thinking along those lines for a while but too lazy/busy to impliment.  The only issue I see is that I don't think ext2fs supports ext4 filesystem yet so your data part. would need to remain ext3. (this would also avoid the potential large file writing bug with ext4)

Back-up your data part. give it a go.  This plan would work well with multi-boot systems and be ideal with data syncing on UbuntuOne.

---

### Post by darkestfright on 2009-10-31
I've had /home on a seperate ext4 partition ever since Jaunty and overall, I prefer it because I don't need to backup every single time I do a reinstall (I'm a bit of a distro jumper, but I don't like dual/triple booting).  If you don't want your settings to stick around when you reuse your /home partition, then try this:

1.  Boot into the LiveCD
2.  Mount your old /home partition, you should be able to do this by just clicking on the "Places" menu and clicking on the icon for that filesystem.
3.  Open a terminal and navigate to the /home/username directory of the partition.
4.  execute ```
sudo rm -rf .*
```  This will delete every folder in your /home/username directory that contains your application settings but leave all of your data intact as long as none of your personal files were stored in hidden directories.
5.  Run the LiveCD Installer and simply specify your old partition as your /home partition.

If you don't want to use the terminal, you can do this with Nautilus, press Alt-F2 and type:

```
gksu nautilus
```

navigate to the /home/username directory of your home partitition and press CTRL+H to show all hidden directories.  Selecting all the ones you wish to delete and just delete them.


If the installer is giving you trouble, is it because you are trying to change the file system type of your /home partition?  You'll need to format if it is ext3, for example, and you want to switch to ext4.  Back up your data, and then just format your partition.  It might be a bit inconvenient, but switching from ext3 to ext4 is worth it.

---

### Post by arpanaut on 2009-10-31
> **melat0nin said:**
> Anybody? The installer won't allow me to mount the existing /home partition without formatting it, which is no good because it's full of my stuff(!)

That does not seem right... bug with installer?
Make sure you choose the fs type in installer  that is the same as what the /home exists as and then mount

---

### Post by darkestfright on 2009-10-31
haha, I didn't read half of your post the first time...completely missed the part where you want to share files with Windows.

I think that should work, I did something similar with my girlfriends PC when I got her to try Ubuntu.  I would suggest having your main /home partition as ext4, and the seperate Documents/Music/etc...folders should be fine as ext2 if you plan on browsing them from Windows.

You've thought it out pretty much the perfect way, infact I've seen some setups go as far as having a seperate partition for each Documents/Music/etc... folder!  Depends on your needs, but whatever suits you best.

---

### Post by melat0nin on 2009-10-31
> **arpanaut said:**
> That does not seem right... bug with installer?
Make sure you choose the fs type in installer  that is the same as what the /home exists as and then mount

I think I was setting it to ext4 when the /home partition is already ext3, so it was going to reformat with the new filesystem (so it was my fault).

---

### Post by melat0nin on 2009-10-31
Sounds like a good bet. What size do you guys think the /home partition should be? i.e. what size is enough to ensure there are never any problems with settings etc getting too large? Is my estimate of 2gb reasonable?

---

### Post by arpanaut on 2009-10-31
Depends on your HD size, personally having lotsa disk space I generally go for overkill... just in case. YMMV

Since a **total** new install is 2.5-3 gigs I would think your estimate would be correct. but I don't know for sure.

---

### Post by melat0nin on 2009-10-31
> **arpanaut said:**
> Depends on your HD size, personally having lotsa disk space I generally go for overkill... just in case. YMMV

Since a total new install is 2.5-3 gigs I would think your estimate would be correct. but I don't know for sure.

I've gone for the following:

Root partition (/): 10gig
/home partition:    ~4.5gig (I resized down my root partition which was previously 15gig)
Docs partition:     ~190gig (same size as whole of previous /home partition)

Now it's installing (taking all of 5 mins!). After that's done, all I need to do is copy over any settings that I want to keep from the old installation from the Docs partition to the /home partition, then delete all the other settings on the Docs partition to leave a clean set of documents folders. Then some symlinks from the /home partition to the Docs partition (and a mount of course), and that's that!

---

### Post by audiomick on 2009-11-10
> **darkestfright said:**
>  
4.  execute ```
sudo rm -rf .*
```  This will delete every folder in your /home/username directory that contains your application settings but leave all of your data intact as long as none of your personal files were stored in hidden directories.


If you don't want to use the terminal, you can do this with Nautilus, press Alt-F2 and type:

```
gksu nautilus
```



Firstly, I am grateful for the tip. It answers a question I have been wondering about for a while now, so thanks.



Secondly, having found this post a few hours ago, I found another from a moderator just now, about malicious commands, which quotes exactly this command. Therefore, I think a warning is also appropriate.

This one
```
sudo rm -rf .*
```
makes you a super user, and removes everything that is a hidden file, ie all system files, configs and so on, in the current folder and all the folders it contains, without asking for confirmation. 

If executed in the wrong place, it will kill your computer

This one
```
gksu nautilus
```
makes you a super user and opens the file manager, which puts you in the position to delete anything anywhere on the computer. The inherent danger of this should be obvious

I hope I am not treading on anyones toes. I just think that it's a good idea to know what this sort of command does

Michael

---

### Post by Ginsu543 on 2009-11-10
FWIW, this is how I've set up my system (1 TB hdd) to accomplish something similar to what you're trying to do:

/: 1 GB
/boot: 100 MB
/usr: 12 GB
/var: 6 GB
/tmp: 100 MB
/home: 80 GB
swap: 1 GB
data (ntfs): 900 GB

My data partition is like your Docs partition and I just keep it in NTFS. Ubuntu has no problems accessing an NTFS partition and Windows treats it as native.

---

