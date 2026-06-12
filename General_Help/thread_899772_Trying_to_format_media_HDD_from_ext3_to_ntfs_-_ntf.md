---
title: "Trying to format media HDD from ext3 to ntfs - ntfs is not active??"
date: 2008-08-24
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-24
Alright, I am using a dual boot system.

So the media I have on hdd #2 needs to be read by Ubuntu (which is already is/was) and also on windows.

I formated the HDD in ext3 and everyone told me that it will be much easier for windows to recongnize ntfs.

So i removed all media, I was ready to format to ntfs, but it is not highlighted and wont allow me to do so.

Is this because hdd #1's 1st parition is set to ntfs?

How do I force it to format in ntfs?

---

### Post by gkaragoulis on 2008-08-24
Are you trying to format this in Ubuntu or Windows?  I don't think there's a way to do it in Ubuntu, and if it's Windows I'd say try your luck at a Windows forum...

---

### Post by panayk on 2008-08-24
```
sudo apt-get install ntfsprogs
```

but I'm not sure it will work...

---

### Post by drs305 on 2008-08-24
Are you using gparted? If so, the volume must be unmounted. Additionally, the gparted version on the liveCD, gparted CD or the systemrescuecd all support formatting in NTFS - the gparted version installed within ubuntu doesn't have that feature as yet.

---

### Post by mssever on 2008-08-24
Another option: There exists a Windows driver to enable Windows to use ext3 filesystems.

---

### Post by PsychedelicWonders on 2008-08-24
No I am trying to do this in Ubuntu.

What is stopping me from being able to do so?  

Yes I was using gparted.

what about that code?  Is that my best option?

What will that open? 

Will it do the 2nd hdd as default when I use that code?

---

### Post by panayk on 2008-08-24
That's just a command to install the ntfsprogs package. Feel free to use synatpic if you prefer. If I remember correctly this will enable gparted to work with NTFS partitions just as it does in the LiveCD. The full description of this package is:
> 
Description: tools for doing neat things in NTFS partitions from Linux
 The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full support
 for the NTFS filesystem to the Linux operating system. 
 
 This is a set of tools targeted for people interested in working with the NTFS
 support in the Linux kernel and using it.  The following utilities are
 included: 
 
 ntfsfix - Fix common filesystem errors and force Windows to check NTFS. 
 
 mkntfs - Format a partition with an NTFS filesystem, optionally bootable. 
 
 ntfsinfo - Show some information about an NTFS partition or one of the files or
 directories within it. 
 
 ntfslabel - Show, or set, an NTFS partition's volume label. 
 
 ntfsresize - Resize an NTFS partition without losing data. 
 
 ntfsundelete - Recover deleted files from an NTFS partition. 
 
 ntfscluster - Locate the owner of any given sector or cluster on an NTFS
 partition. 
 
 ntfscat - Concatenate files and print them on the standard output (without
 mounting the partition). 
 
 ntfsls - List directory contents on an NTFS filesystem (without mounting). 
 
 ntfscp - Overwrite files on an NTFS partition. 
 
 ntfsclone - Efficiently clone an NTFS filesystem or a part of it. 
 
 ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE. 
 
 ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED). 
 
 ntfscmp - Compare two NTFS volumes and tell the differences.


---

### Post by PsychedelicWonders on 2008-08-25
Can i format this easier in ntfs in windows?

If i format in windows and make it an ntfs, will ubuntu regonize it?

it wont try to make hdd #2 the default hdd since hdd #1 is also ntfs will it?

---

### Post by mc4man on 2008-08-25
you can format it no problem in windows (and give it a volume name
or install this on windows and keep it ext3 (or format in ubuntu to Ext2
[http://www.fs-driver.org/](http://www.fs-driver.org/)
(accessed thru control panel

---

### Post by PsychedelicWonders on 2008-08-27
> **mssever said:**
> Another option: There exists a Windows driver to enable Windows to use ext3 filesystems.

Perhaps this is just the easiest way.  

Where do I get this driver from?

Why isnt gparted allowing me to just format it under an ntfs heading?  It seems like the easiest way.  All of my data is transferred off of hdd #2 and its ready to be switched.

Do I need to install the ntfsprogs package?

I dont want to change it to ext2 since ext3 is better/newer.

---

### Post by fooman on 2008-08-27
> **PsychedelicWonders said:**
>  

Where do I get this driver from?



from the link in the post above yours by mc4man.  read the instructions on the page (works on both ext2 and ext3).  its pretty easy to install and configure.

---

### Post by bigbrovar on 2008-08-27
gparted can format your drive to an ntfs .. but you would need to install a tool called ntfsprogs which can be installed from synaptic .. once this tool is installed gpated would be able to format the drive to ntfs ..

---

### Post by PsychedelicWonders on 2008-08-27
> **bigbrovar said:**
> gparted can format your drive to an ntfs .. but you would need to install a tool called ntfsprogs which can be installed from synaptic .. once this tool is installed gpated would be able to format the drive to ntfs ..

Ahh I see now.

But I was able to make my windows partition an ntfs?

So what is stopping gparted from doing it to my 2nd hdd?

what is synaptic?

I know what gparted is, but not familar with synaptic.

Fooman: thanks, if i cant get this to work in gparted this time, I'll follow that walkthrough.

---

### Post by mssever on 2008-08-27
> **PsychedelicWonders said:**
> what is synaptic?
The GUI package manager. System > Administration > Synaptic Package Manager.

EDIT: When it comes to formatting as NTFS, I think it's best to do that from within Windows.

---

### Post by PsychedelicWonders on 2008-08-27
Why what does it make a difference one way or another?

I'm in Ubuntu right now, would prefer to just do it all here, unless there is a good reason not to?

---

### Post by mssever on 2008-08-28
> **PsychedelicWonders said:**
> Why what does it make a difference one way or another?
I don't fully trust the Linux NTFS tools. They had to be reverse-engineered, after all, and not everything works (which is why you have to mount the partition in Windows if it was unmounted uncleanly). For regular data access, there's really no choice. But for a one-off task like formatting, I'd prefer to play it safe and let the Windows tools do it.

---

### Post by tiga2001 on 2008-08-28
I was trying to format ntfs in Ubuntu, too. Because I used all primary partitions, the Windows XP installer did not want to give me more partition because I already had 3 (actually 4 but windows didn't detect linux swap). The reason I have so many partitions is because I'm triple-booting mac, windows, and linux.

Just replying to say that installing ntfsprogs works like a charm.

---

### Post by PsychedelicWonders on 2008-08-28
Al;right, so what is the easiest and quickest way to format in windows?

This hdd I am trying to format is now showing up under my computer on windows... so how do I make it find it?

---

