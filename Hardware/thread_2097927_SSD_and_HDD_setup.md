---
title: "SSD and HDD setup"
date: 2012-12-24
forum: Hardware
---

### Post by BloodyDream on 2012-12-24
I just built a new computer (Christmas present haha) and I have already installed Ubuntu on the SSD, with the HDD unconnected of course. Now do I just simply connect the HDD and I'm done? Or is there any additional set up that is necessary? I assume the second option, haha. Any help is appreciated. 
Thanks

---

### Post by whatthefunk on 2012-12-24
It should be detected immediately on boot after you plug it in, but it probably wont auto mount.  It would have been better to connect it before installing the OS so that you could partition in when you installed Ubuntu.  This would have added it to fstab so that it would auto mount on startup.

What youll have to do is partition it how ever you want and add the partitions to /etc/fstab.  Not too hard really.

---

### Post by ahallubuntu on 2012-12-24
Use Gparted to partition the new drive.  Decide how you'd like to set it up.  For /home?  Do you want to share it with another operating system?  (Windows?)  If no other OS, you'll probably be best using ext4.  Do you want one big partition or several?  These choices are up to you.

Yes, you can add your new partition(s) to the /etc/fstab file.  After you've changed that file, be sure you issue this command:

```
sudo mount -a
```

to make sure you've edited fstab successfully.  Otherwise, if there's an error in that file, Ubuntu won't boot the next time.

---

### Post by BloodyDream on 2012-12-25
Everyone told me to install the OS first, to make sure that it installed correctly. I don't want to partition it or anything, I just want it to be storage.

---

### Post by BloodyDream on 2012-12-25
I don't think that I clarified well, I just want the HDD as storage, not another boot.

---

### Post by ahallubuntu on 2012-12-25
You should still make ONE partition with Gparted, even if that single partition takes up the entire drive.  Gparted is just the easiest tool to use.

I understood that you didn't want to put another OS on this 2nd drive, but I wasn't sure if your SSD had more than one OS on it or not.  That's what I meant about sharing.

The other question you need to ask is: how do I want to store and sort my data?  There are various ways to do it.  You could store it in /home under your user account (which is what Ubuntu tends to do by default).  If so, then it might make sense to put make this 2nd disk a big /home partition.  In that case, make the partition (probably one big ext4 partition), copy everything under /home to the top directory of the new partition, then change /etc/fstab to mount /home on the new partition.  

If you don't want to use /home for storage, choose somewhere else.  Sometimes I make a folder called /shares in my top level directory for shared drives.  It's really up to you, as long as you are consistent and make it easy for yourself to find and store your data.

---

### Post by BloodyDream on 2012-12-25
I want to do that, so basically all I do is connect it and make a partition? That seems simple, haha. Gparted is pretty easy to use too. Now, once I make the portion, will it just automatically save stuff there or will I have to select it or what? Thanks, love the name by the way haha.

---

### Post by ahallubuntu on 2012-12-25
> **BloodyDream said:**
> I want to do that, so basically all I do is connect it and make a partition? That seems simple, haha. Gparted is pretty easy to use too. Now, once I make the portion, will it just automatically save stuff there or will I have to select it or what? Thanks, love the name by the way haha.

I assume you are familiar with Windows?  Windows tends to default to saving stuff in My Documents (photos in "My Pictures," etc.).  Many installed programs in Ubuntu do the same thing with /home .  

So as I said, if you mount the new partition as /home, then YES, it will "automatically save stuff there."  Or at least many programs will.  You can always choose to save whatever files you want in your home directory in /home .

Again, if you're going to do that, copy the existing contents of /home to the top directory of the new partition before changing fstab and mounting it as /home.  Otherwise, you won't be able to login next time.  Some other important stuff is saved in your home directory.

This is what was meant above about having the drive setup during Ubuntu installation.  All of this /home stuff could have been done for you almost automatically instead of having to do it all manually.  No matter, at least you will learn a little more this way!

---

### Post by BloodyDream on 2012-12-25
It's cool, not very hard. Especially since I haven't saved anything, so I want have to move it haha. Alright, if you will, just tell me step-by-step exactly what to do, so that I can just copy and paste on my phone so that I don't have to come back here to read stuff haha. Thanks so much for all of the help.

---

### Post by whatthefunk on 2012-12-25
I do it slightly different.  I have home on my SDD in a seperate partition and I have my HDD mounted at /home/username/Storage

---

### Post by BloodyDream on 2012-12-25
This may be stupid, and it probably has an easy and obvious fix but I figured that I should ask. I still haven't installed the HDD but the SSD that I'm using has been split. One consisting of 34GB and the other 56GB. Under the disks thing, the 34GB's contents are swap and the 56GB is ext4. Why did it do this and how do I change it so that all 90 are together? ALso, under gparted it shows a little red circle with an exclamation point next to it. It doesn't show the drive as being partitioned though. Should I just clear everything and reinstall Ubuntu? I don't have anything saved so that's possible.

---

### Post by ahallubuntu on 2012-12-25
You want SOME swap but not 34GB of swap!  I'm not sure why it's so large.

The general rule is to make your swap size 1.5X the size of your RAM  - so if you have 8GB of RAM, make a 12GB swap.  In practice you can use less nowadays.  My rule is to make the swap at least as large as the RAM (so you can hibernate, which uses your swap to dump RAM contents).

To change the sizes, boot up your live CD and start up Gparted. Shrink your swap partition down to (perhaps) the size of your RAM, then resize the other one to use the new free space.  Should be pretty quick.  Then, reboot.

---

### Post by BloodyDream on 2012-12-25
Well, I have 32GB of RAM so I suppose that that's why haha.

---

### Post by whatthefunk on 2012-12-25
32 GB of ram?  Thats totally unnecessary and you probably dont even need swap.  Might want to allocate a couple GB just in case, but 32 GB of swap is insane.

---

### Post by BloodyDream on 2012-12-25
> **whatthefunk said:**
> 32 GB of ram?  Thats totally unnecessary and you probably dont even need swap.  Might want to allocate a couple GB just in case, but 32 GB of swap is insane.

I found a deal, 32GB of 1866 RAM for like $80. That's barely more expensive than 16GB, I couldn't pass that up xD But how do I go about changing it? I've tried a couple of things and I can't find anything.

---

### Post by whatthefunk on 2012-12-25
> **BloodyDream said:**
> I found a deal, 32GB of 1866 RAM for like $80. That's barely more expensive than 16GB, I couldn't pass that up xD But how do I go about changing it? I've tried a couple of things and I can't find anything.

Change what?  Swap size?

---

### Post by oldfred on 2012-12-25
I do not have any swap on SSD, but just a little on hard drive. I only have 4GB of RAM and almost never use swap. I would not expect you to ever use swap. Also with an SSD you will boot so fast the hibernation does not really save much.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

            [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

I do like to not have one very large partition on a drive. fsck can then take forever if needed. Or if partition issues then all data is gone. Of course if drive issues then backups are the only recourse anyway. 

 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive. Now with my SSD I keep my working install on my SSD, but have a second install and several test installs on my hard drive each in 25GB / (root) partitions and all data is shared with data partition.

---

### Post by BloodyDream on 2012-12-26
Yes, to change swap size. I never use hibernation anyway, the only reason my boot time takes more than 10 seconds is because I had to encrypt it and therefore I have to enter an extra password. 

Oldfred, you somehow always help when I post something, so again thanks haha.

---

### Post by BloodyDream on 2012-12-26
As a matter of fact OldFred, your reply on another thread just helped me. The reason that it isn't showing up in Gparted is because the SSD is encrypted. So does this mean that I'm just kinda screwed?

---

### Post by oldfred on 2012-12-26
I have see a lot of users encrypt /home and then gparted does not show swap as when /home is encrypted, swap also is  encrypted and gparted does not 'see' the format.
 Once encrypted the partition is not parseable, so gparted things it is damaged.

I do not have encryption, but since there are a lot of questions, I have a link.
       [https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

---

### Post by BloodyDream on 2012-12-26
What exactly does opening it do?

---

### Post by oldfred on 2012-12-26
To mount and open an encrypted partition, you have to use your pass phrase. So you cannot just click on it like a normal partition.
If encrypted always best to have really good backup procedures as there is no way to scan partition and find data. Repairs are usually impossible or at best less likely. The whole purpose of encryption is to prevent others from accessing a partition so without the pass phase it cannot be seen.

---

