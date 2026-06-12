---
title: "Wd hd"
date: 2009-03-10
forum: Hardware
---

### Post by mysteriousdarren on 2009-03-10
I was trying to copy a movie from my computer to the hd and at 4gbs the transfer would stop and show an error that the file was too big. I was wondering if there is a way to fix this, and what I could do.

---

### Post by mysteriousdarren on 2009-03-10
I also was wondering how I could cool down my hard drive and make is last longer...any ideas?

---

### Post by mtbsoft on 2009-03-10
You're not making a lot of sense, you need to explain a little better.  Are we talking about a Western Digital external hard disk as the copy target?  How is it formatted - ext3, NTFS, FAT32, FAT16(!!)?  More details please...

Which HD are you wanting to cool down?  The one in "the computer" or the external one?  If the internal one, then you could do with providing rather a lot more information on the spec's of the computer in question; if the external one, a make and model would be a good start along with details of why you think it is too hot.

The more information you provide, the better people can help - at the moment you've only told us "my car won't go"... not the full nature of the problem.

---

### Post by mysteriousdarren on 2009-03-10
Sorry for the generalities. The hard drive is a 500gb Western Digital formatted vfat(Fat32). It is an external hard drive, basically wondering how I could cool it down. I've heard enough about horror stories about linux and hard drives. Just wondering what I could do.

---

### Post by taurus on 2009-03-10
Fat32/vfat cannot handle files larger than 4GB.  If you plan to save something to your external harddrive that is larger than 4GB, better format it to ntfs filesystem.

---

### Post by mysteriousdarren on 2009-03-10
What would be the best thing to format the hd to? What has the best transfer rate, and best stablitility?

---

### Post by taurus on 2009-03-10
If you are sharing that external drive with windows and/or mac, then it's better to format it to ntfs filesystem.  But if you're only using that drive with Ubuntu (Linux) machine, then ext3 is much better.

---

### Post by mtbsoft on 2009-03-10
> **mysteriousdarren said:**
> It is an external hard drive, basically wondering how I could cool it down. I've heard enough about horror stories about linux and hard drives. Just wondering what I could do.
Ah, the good old FUD factory is still in good health I see.  Sorry, but, unless you have heard specifics about your particular hardware, you need to take such "linux wrecks your hardware" stories with a very large bucket of salt. 

I have a 2Tb WD ext drive and have noticed no overheating issues irrespective of what O/S I'm using.  Unless you're going to work in a hot house or put the thing in a small enclosed space like a cupboard or drawer, the normal ventilation should be more than adequate.  If you're that concerned, sit a small thermometer on top of the case and monitor it - if the ambient temperature of the room is so high that it impacts the HD, simply aim a desk fan at it.

---

### Post by mysteriousdarren on 2009-03-11
Thanks for the update on the issues with overheating. 

I reformatted the hard driver to ext3 and was trying to put the files back on after the reformatting. It was giving me an error that said it would not let me put on files, and could not change the permissions because I'm not the owner. I was wonder how I could fix this. THx for the help.

---

### Post by taurus on 2009-03-11
Assuming you have mounted that external drive (ext3) to /media/share and  your login name is darren, you can change the ownership of the mount point from root to your login name with

```
sudo chown -R darren:darren /media/share
```

---

### Post by mysteriousdarren on 2009-03-12
I turned on my computer after I had reformatted the hard drive, and I won't mount. I was wondering what I could do.

---

### Post by taurus on 2009-03-12
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by mysteriousdarren on 2009-03-20
Here is what popped out. 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002e839

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
kevin@Wizard:~$

---

### Post by taurus on 2009-03-20
Now that you've formatted it to ext3, just mount it from a terminal with

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by mysteriousdarren on 2009-03-21
I put the code into the terminal then tried to copy a couple music files into the hard drive, and it said that i did not have permission to do that since I am not the owner? What can I do for that?

---

