---
title: "Cannot access external hard drive after connecting to Ubuntu."
date: 2013-07-16
forum: Hardware
---

### Post by Rishabh99 on 2013-07-16
Hello everyone,
I have a 1TB seagate hard drive formatted in NTFS format, which was working fine until I connected it in Ubuntu 12.04. Now when I try to use it again in windows 7 it displays the drive letter perfectly and even shows that 500MB of it is also used but when I open it in windows explorer it shows empty. Earlier it was showing just a shortcut which was not opening but after I performed "chkdsk" on the disk that link also disappeared. Now its just showing empty after opening but it still shows approx 500MB occupied when I check it in My Computer. In Ubuntu 12.04 the disk is mounting automatically and it shows some files and folders along with a folder with no name, all my previous files are in that folder.
I want to access my files in windows now so please help me as I can't find any solution on google. Having a lot of hopes from you guys.
Please help.:(

---

### Post by sudodus on 2013-07-16
Welcome to the Ubuntu Forums :-)

Please run a few commands in a terminal window, and post the output from them in a reply. Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this

```
output
```

It will make it easier to help you. Here are the commands:

```
sudo fdisk -lu
```
```
sudo parted -l
```
```
sudo blkid
```
```
df
```

---

### Post by dannyboy79 on 2013-07-16
the info sudodos asked for will be helpful in people helping you.

NOTE: i have been seeing more and more people complain about losing files lately when it comes to NTFS and linux. I just don't trust writing to a filesystem that isn't native to linux. I write my files to a FAT32 partition that I need to access in windows or use SAMBA to share files between linux and windows and I never have an issue

---

### Post by varunendra on 2013-07-17
Welcome to the forums Rishabh !

> **Rishabh99 said:**
> Earlier it was showing just **[COLOR="#FF0000"]a shortcut[/COLOR]** which was not opening but after I performed "chkdsk" on the disk that link also disappeared. Now its just showing empty after opening but it still shows approx 500MB occupied when I check it in My Computer.
One possibility is that windows detected the partition table as corrupt (probably because you disconnected it without unmounting/safely-removing in Ubuntu) and 'repaired' it its own (stupid) way. The folder with "no name" should, in this case, be a hidden system folder which *should* appear with name "found<some number>" in windows if you enable "Show hidden files" and disable "Hide system files" in "Folder options" in windows.

Either that, or your windows may be affected by some virus that usually hides the data and does not let you unhide it while it is active.

That being said, if your data on that drive is important to you, I'd suggest to back it up on Ubuntu while you can access it from there. You never know what windows 'automatic' repair can do to your files.

I'm more suspicious about it being a virus since you say there are "some files and folders" other than the one in which you can still find your data, and that one has "no name" (chkdisk would never do that). Besides, the chkdisk utility usually renames the recovered files so you can not identify them just by looking at them. If you can not 'unhide' the files from within "Folder Options" in windows, you are certainly affected by a virus.

Just copy the important files to another drive or within Ubuntu, then try formatting the drive (in ubuntu or windows) and copying the files back.

---

### Post by Rishabh99 on 2013-07-18
> **varunendra said:**
> Welcome to the forums Rishabh !


One possibility is that windows detected the partition table as corrupt (probably because you disconnected it without unmounting/safely-removing in Ubuntu) and 'repaired' it its own (stupid) way. The folder with "no name" should, in this case, be a hidden system folder which *should* appear with name "found<some number>" in windows if you enable "Show hidden files" and disable "Hide system files" in "Folder options" in windows.

Either that, or your windows may be affected by some virus that usually hides the data and does not let you unhide it while it is active.

That being said, if your data on that drive is important to you, I'd suggest to back it up on Ubuntu while you can access it from there. You never know what windows 'automatic' repair can do to your files.

I'm more suspicious about it being a virus since you say there are "some files and folders" other than the one in which you can still find your data, and that one has "no name" (chkdisk would never do that). Besides, the chkdisk utility usually renames the recovered files so you can not identify them just by looking at them. If you can not 'unhide' the files from within "Folder Options" in windows, you are certainly affected by a virus.

Just copy the important files to another drive or within Ubuntu, then try formatting the drive (in ubuntu or windows) and copying the files back.

Thanx everyone for your quick solutions and sorry for not reverting back sooner. I had to go out of station so did not had access to internet.

A really big thanx to Varunendra. You were right. Stupid windows was hidding my files and I was able to access them once they were unhidden.
Thanx alot, you saved my life...:P

---

### Post by varunendra on 2013-07-18
Pleasure is mine buddy! :)

Congratulations for the recovery of data without too much hassle. But always remember - a data without backups is the data that is not important to you. Losing it is just a matter of time. ;)

---

