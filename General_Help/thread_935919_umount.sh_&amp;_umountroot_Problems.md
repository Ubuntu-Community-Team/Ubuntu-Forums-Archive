---
title: "umount.sh &amp; umountroot Problems"
date: 2008-10-02
forum: General Help
---

### Post by aladdin83 on 2008-10-02
Hello,

I recently made a mistake of deleting "umount.sh" & 'umountroot" from my 'etc/init.d' folder.  As a result I am noticing   "fsck" executed on every boot.  
When I boot the frist time fsck will scan telling me there was an unclean shutdown.  granted the scripts are missing so its doing its job right.  Moments later fsck will reboot the computer. Upon reboot I am able to access my Ubuntu and does not go into another fsck loop.  

I would like to know how I can rebuild, umount.sh and umountroot scripts. Or if there is a solution to this to download the 2 deleted files. I'm a newbie to Ubuntu and Linux in general.  

Currently Using:
Ubuntu 8.04 64 bit
File System is in Ext2 format
other drives are all NTFS format


Thank you in Advance for replies.

---

### Post by BryanFRitt on 2009-06-11
Maybe it's too late, but here you can have mine. I don't know if will still help, but here you go...
P.S. I'm using KUbuntu 8.04.2 64bit AMD (actually an Intel dual core II) on Ext 3, 
I hope it's close enough.
(I have it NTFS, Linux Swap, Ext 3, Ext 3, and a NTFS external)
> 
Or if there is a solution to this to download the 2 deleted files.

You could ask on the message boards, if anyone has a Ubuntu 8.04 64 bit will they attach their umountroot and umountfs files to a post.
(Sounds like something I just did, cause maybe I did? :D )
Note: I had to add a .sh to the end of the file names, so they would upload.

I currently dealing with these files myself, if you think you can help feel free to post (not required though):
[http://ubuntuforums.org/showthread.php?p=7437058](http://ubuntuforums.org/showthread.php?p=7437058)

---

