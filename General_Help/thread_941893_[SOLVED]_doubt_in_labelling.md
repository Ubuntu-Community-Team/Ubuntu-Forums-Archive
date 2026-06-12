---
title: "[SOLVED] doubt in labelling"
date: 2008-10-08
forum: General Help
---

### Post by suhaib1thariq on 2008-10-08
i have four drives in ntfs .... and partitioned another one drive for ubuntu...if i labelled the ntfs drive in ubuntu ...if that also changes label in windows?but my windows labelling is showing in ubuntu for one drive...(i labelled one drive in windows previously)

---

### Post by drs305 on 2008-10-08
Yes, you can label them in ubuntu and they will have the same label in windows.

Install ntfsprogs:
```
sudo apt-get install ntfsprogs
```

To label an NTFS partition:
```

ntfslabel /dev/sdXX labelname

```

Example:
ntfslabel /dev/sdb1 mymusic

Here is a link to a post that explains how to label many different formats in ubuntu. Note they are different for different formats. The labeling information is about 1/5 of the way down the post.
[Understanding Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by jerome1232 on 2008-10-08
As long as you have the appropriate utility installed (ntfsprogs for ntfs) then you can also set label's in gparted (at least on intrepid I keep forgeting I'm using the Alpha)

This guide is good for doing labels [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by suhaib1thariq on 2008-10-08
i installed gparted...i don't know where it installed ...how can i find that

---

### Post by drs305 on 2008-10-08
> **suhaib1thariq said:**
> i installed gparted...i don't know where it installed ...how can i find that

You can look in System Tools but I may have put the link there myself. If it's not in System Tools, open it with:
```
gksudo gparted
```

To find out where the command to start an app is located (if you know the actual command name), use the 'which' command:
Example:
```

which gparted

```

Returns:
```
/usr/bin/gparted
```

Since /usr/bin is included in the normal PATH, all you have to type in this case is "gparted". You use "gksudo" because you will be altering system files and administrative privileges are required.

---

### Post by scouser73 on 2008-10-08
Gparted can be found in: **System** > **Administration**

---

### Post by drs305 on 2008-10-08
> **scouser73 said:**
> Gparted can be found in: **System** > **Administration**

Yes, on mine it's listed as "Partition Editor" and not gparted... Guess that's why I made my own link.  ;-)

---

### Post by scouser73 on 2008-10-08
Sorry, it's called Partition Editor, not Gparted

---

