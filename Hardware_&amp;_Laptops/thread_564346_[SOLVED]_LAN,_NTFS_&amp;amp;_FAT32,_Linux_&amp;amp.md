---
title: "[SOLVED] LAN, NTFS &amp;amp; FAT32, Linux &amp;amp; Windows"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by mandrill on 2007-10-01
OK, I have a 3 pc LAN, one is wired - xp home, (I know, I know),  other 2 are as follows: 1) xp pro with a 250gb slave currently formatted as ntsf, and 2) ubuntu with 300gb fat32 slave.

Is it wise/prudent/necessary to reformat xp pro slave to fat32 for read/write ability between it and the linux box? I have successfully written from the linux box to the xp pro box (fat32 to ntsf) using the xp pro machine, but have not tried writing to the xp ntsf drive using the linux box. The wired xp home machine doesn't really have the need for much file transferring, and if necessary, could go from linux>xp pro>xp home. And, will my reformatted fat32 boot properly?

Any thoughts?

---

### Post by Wicca on 2007-10-01
Hi,

Why not using networksharing?

Thinking about whether to use NTFS or fat32 is only usefull when different operation systems have access to the harddisk** directy**, such as in a dualboot configuration. This doesn't seem the case here, since you have a LAN with different machines. You can share each harddisk (or part of it) on each machine and leave the disk I/O to the local OS.

So, you can use NTFS for the Windows PC and ext3 for the linux PC (no need to use fat32 there) while both machines will be able to read/write on eachother disks.

---

### Post by mandrill on 2007-10-01
You mean I could have left my 300gb sdb1 as ext3? And when you say networksharing, I am not sure I know precisely what you mean?

---

### Post by js_fr on 2007-10-01
In a dual boot configuration Ubuntu can access FAT32 partitions out of the box, if you want to access NTFS partitions you have to install ntfs-3g - it's in the repositories, for documentation see [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) 
Concerning network sharing with Windows / Linux machines involved use Samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mandrill on 2007-10-01
> **js_fr said:**
> In a dual boot configuration Ubuntu can access FAT32 partitions out of the box, if you want to access NTFS partitions you have to install ntfs-3g - it's in the repositories, for documentation see [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) 
Concerning network sharing with Windows / Linux machines involved use Samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

We may be a little confused here. I am currently using samba, can access back and forth from all pc's. I formatted the 300gb slave on the linux box as fat32, under the impression it was necessary for read/write compatibility. I was, perhaps erroneously, under the impression that I should do the same to the slave drive on the windows box.

However, even if not necessary, I may do so  anyway, (if it will not cause windows to fail to boot it) simply to have the ability to swap drives around (as slaves) should the need arise, unless there are other factors I am probably uneducated about - and I am sure there are...

Any light shed is appreciated, thanks

---

### Post by Wicca on 2007-10-01
Hi!

What I meant with network sharing:
Sharing a directory on machine so it's available over the network for other machines. This directory can be just one folder, or it can be a complete harddisk.

If you want PC1 to have access to the harddisk of PC2 for read/write operations, sharing (parts of) the disk in PC2 is the best option. It doesn't matter what filesystem is used, as long as PC2 can read and write to it. It's no problem for a XP machine to write to a ext3 disk in an Ubuntu machine with samba installed. The fact that it is a ext3 disk is not relevant for XP, for all the disk I/O is not done by XP itself, but handled by ubuntu/samba.

However, if you take the ext3 disk out of the ubuntu and place it in the XP machine so XP has to do the disk I/O itself, it wont work 'cause XP can't  read ext3. In this situation (switching the disk manually between XP and Ubuntu), fat32 is the better option.

In your first message it was not clear to me that you wanted to swap the disk, therefor I thought this was a network situation.

Hope you are less confused now :)

---

### Post by weblordpepe on 2007-10-01
Windows can't read non-Microsoft filesystems? Gee what a surprise :) 
Personally, I find no use for FAT32. Its digusting. Thankfully ntfs-3g lets you read/write to NTFS.
The best thing about NTFS is that you can have built in compression right in the filesystem. That is GREAT because your disk is almost always the bottleneck, so you get a good speed boost half the time.

---

### Post by mandrill on 2007-10-01
Thank you for your reply. I am sure that I am the victim of my own learning curve! Perhaps I can be  more precise regarding my query, and unconfuse myself in the process.  ](*,)

I have my Ubuntu OS loaded on an 80gb hdd (sda1) designated as master,  just the normal Linux partitions.

I have a 300gb slave mounted in home folder, (sdb1) formatted as fat32, with the large partition of 276gb formatted as fat32. There are also two 2.89gb partitions created by gparted  (extended & swap). It was formatted as fat32 because I had been advised to do so for read/write compatibility.

This machine is successfully networked into a Windows workgroup, and, aside from some minorly irritating master browser issues, everything functions as it should.

The Windows machine has a 250gb slave formatted ntsf. From what I understand, you are telling me that, *over the network*, these machines can read and write to each other regardless of format?

If so, was it necessary to to format the Ubuntu slave as fat32?

Can the Ubuntu machine write to/copy from the current Windows ntsf slave?

Could the Windows machine have written to/copy from  the original ext3 partition on the Ubuntu slave? 

And, what really started all of this - Is it necessary to format the Windows slave as fat32?

Even if they are both formatted as fat32, would it not be impossible for them to boot in opposite machines if they were swapped, due to the file systems already on the drives?

One other thought - Thanks! to all of the caring people of the Ubuntu Forums who take their time to answer stupid questions like these. Much appreciated!

---

### Post by skyviannes on 2007-10-01
> **mandrill said:**
> OK, I have a 3 pc LAN, one is wired - xp home, (I know, I know),  other 2 are as follows: 1) xp pro with a 250gb slave currently formatted as ntsf, and 2) ubuntu with 300gb fat32 slave.

Is it wise/prudent/necessary to reformat xp pro slave to fat32 for read/write ability between it and the linux box? I have successfully written from the linux box to the xp pro box (fat32 to ntsf) using the xp pro machine, but have not tried writing to the xp ntsf drive using the linux box. The wired xp home machine doesn't really have the need for much file transferring, and if necessary, could go from linux>xp pro>xp home. And, will my reformatted fat32 boot properly?

Any thoughts?
because of the way networking computers works, it shouldnt (i emphasize shouldn't because nothing is 100% with computers) cause a problem to use any file system, ntfs, fat32, ext3, whatever you prefer, they should all play nicely together because the network cards themselves dont really care about what file system is being used

---

### Post by Wicca on 2007-10-01
> **mandrill said:**
> 
The Windows machine has a 250gb slave formatted ntsf. From what I understand, you are telling me that, *over the network*, these machines can read and write to each other regardless of format?

Yes they can, if:

1) The slave drive in your Ubuntubox is shared using Samba, and the current user on the XPbox as enough rights to access it (also set in Samba)
2) The slave drive in your XPbox is shared using Windows File Sharing and the current user on the Ubuntubox has enough rights to access it.

The accessibility of drives from different machines over a network has nothing to do with NTFS, FAT32, ext3, ReiserFS or whatever, but with RIGHTS. 
> 
If so, was it necessary to to format the Ubuntu slave as fat32?

With the assumptions above in mind, No.> 
Can the Ubuntu machine write to/copy from the current Windows ntsf slave?

See above, yes.
> 
Could the Windows machine have written to/copy from  the original ext3 partition on the Ubuntu slave? 

yes!
> 
And, what really started all of this - Is it necessary to format the Windows slave as fat32?

No. You better left it NTFS.
> 
Even if they are both formatted as fat32, would it not be impossible for them to boot in opposite machines if they were swapped, due to the file systems already on the drives?

Yes, both systems can read/write to fat32, but you can't boot from them offcourse. But as long they only contain data and stay in the 'slave' position this is possible.
> 
One other thought - Thanks! to all of the caring people of the Ubuntu Forums who take their time to answer stupid questions like these. Much appreciated!
It's not as stupid as you think ;). And by the way, you're welcome.

---

### Post by mandrill on 2007-10-01
I am now, all things being equal, enlightened.........Thank you.

Before I wear out my welcome completely:

The slaves, operating as slaves, will/can correctly boot in each others boxes, and be visible, usable? At this point, just curious....

And, in a perfectly planned, executed with foreknowledge kind of world, what would have been the best way to construct this "mutual media server" thing? I hope I have not created more work for myself.... 

I am currently just sharing individual folders (music, video, photos, etc...), is there any advantage to sharing say, the entire drive(s)? Better plan?

I promise I'll go away now.......(for awhile).    :)

---

### Post by weblordpepe on 2007-10-02
Hi. Me again.

Windows XP home is a bit of a dork when it comes to file/folder networking. In fact its a very big dork. Wears glasses and everything. But your best bet would be to use samba.
You can install samba on your Ubuntu machine as to share folders which Windows can see.
And I think by default, your Ubuntu should be able to see folders shared by Windows. 

Although I think I'm really confused about what ya mean with booting each others boxes. Sounds kinky, but I don't think you can boot into another computer's hard drive over a network (at least outside of a comp science lab).

Basically the short story is you pick folders that you want to be shared over the network. And then other computers can see that folder.

In Ubuntu, try going to **network:///** or **smb:///windowshostname** where windowshostname is the name of your Windows XP home machine. You should see a few default shares.

---

### Post by mandrill on 2007-10-02
> **weblordpepe said:**
> Hi. Me again.

Windows XP home is a bit of a dork when it comes to file/folder networking. In fact its a very big dork. Wears glasses and everything. But your best bet would be to use samba.
You can install samba on your Ubuntu machine as to share folders which Windows can see.
And I think by default, your Ubuntu should be able to see folders shared by Windows. 

Although I think I'm really confused about what ya mean with booting each others boxes. Sounds kinky, but I don't think you can boot into another computer's hard drive over a network (at least outside of a comp science lab).

Basically the short story is you pick folders that you want to be shared over the network. And then other computers can see that folder.

In Ubuntu, try going to **network:///** or **smb:///windowshostname** where windowshostname is the name of your Windows XP home machine. You should see a few default shares.

Thanks for your help - not being sarcastic - but I was not having sharing problems. My final question was whether I could take the slave from one and install/boot/read in the other, but I'm guessing probably not.

---

### Post by weblordpepe on 2007-10-03
I dont think linux minds, aye. Windows XP has a 'feature' which looks at the hardware and if there's been a big enough change, it will refuse to boot.

---

