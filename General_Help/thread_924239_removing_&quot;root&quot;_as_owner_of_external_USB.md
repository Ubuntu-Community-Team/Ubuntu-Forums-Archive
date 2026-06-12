---
title: "removing &quot;root&quot; as owner of external USB drive"
date: 2008-09-19
forum: General Help
---

### Post by gregconquest on 2008-09-19
This seems like such a simple question, but nowhere have I been able to find a simple, complete answer.

I have formatted one partition of an **external USB drive** as ext3 using GParted. The partition was created as being **owned by root**.

I intend to **use this drive to share** between several Linux, Mac, and Windows computers. So, I need to change permissions on the whole partition to "777", and I think I should change the owner as well.

Can someone tell me how to do this, please? Everything I read about this seems to assume that I'm going to be changing one folder, but I want to **change the whole partition**. 

TIA.
Greg

---

### Post by iaculallad on 2008-09-19
Change the Ownership:

```
sudo chown user:group /mnt/usb_drive
```

Optional: change permissions:

```
sudo chmod 777 /mnt/usb_drive
```

---

### Post by gregconquest on 2008-09-19
OK. Great. Thank you, iaculallad. That is so simple. I should just use the path instead of the folder or filename . . . 

Now, though, what group (and other) should I assign?

G-)

---

### Post by iaculallad on 2008-09-19
> **gregconquest said:**
> OK. Great. Thank you, iaculallad. That is so simple. I should just use the path instead of the folder or filename . . . 

Now, though, what group (and other) should I assign?

G-)

Actually, the group parameter is optional. Group indicates which the target is associated. (i.e: user or admin groups)

For more info on chown:

```
man chown
```

You could also use:

```
sudo chown -R username /mount_point/folder
```

-R switch will recursively own the sub-folders of a folder.

---

### Post by gregconquest on 2008-09-19
```
ls -l /dev/sdf1
```yields:
brw-rw---- 1 root disk 8, 81 2008-09-20 00:25 /dev/sdf1

```
sudo chown -R greg /dev/sdf1
```then:
```
ls -l /dev/sdf1
```yields:
brw-rw---- 1 **greg** disk 8, 81 2008-09-20 00:25 /dev/sdf1
   ... good, the owner is changed -- now for the permissions ...
```
sudo chmod -R 777 /dev/sdf1
```and finally:
```
ls -l /dev/sdf1
```yields:
brw**x**rw**xrwx** 1 greg disk 8, 81 2008-09-20 00:25 /dev/sdf1

It all appears to have worked. Remounting, and . . .
 
[COLOR="Red"]Noooooo![/COLOR] I still can't write to the partition. 

Now, if I enter:
```
ls -l /dev/sdf1
```I get:
brw**-**rw**----** 1 **root** disk 8, 81 2008-09-20 00:36 /dev/sdf1

It's all back to the way it was before. What happened?

---

### Post by gregconquest on 2008-09-19
I unmounted after resetting the owner and permissions by right-mouse clicking on the drive on the desktop and selecting "unmount". Then I unplugged the drive and then replugged it in to remount it. That wouldn't have made any difference, would it?

---

### Post by gregconquest on 2008-09-20
If you're just dropping in on this thread, please look at post #5 above. It is the one with the current state of affairs.

I appear to be doing everything right, and getting the right results, but upon remounting, none of the permissions or owners has changed.

Thanks,
Greg

---

### Post by iaculallad on 2008-09-20
In reply for post number 5:

If you're trying to change the permission of an NTFS external USB drive, then  , it's not possible (could be done only if auto mounting with fstab). What you can do is format it as Ext3/Ext2 so you could apply/change Linux drive permission persistently. (That's only if you don't use the drive on windoze)

---

### Post by gregconquest on 2008-09-20
This *is* an ext3 partition on a USB drive that I am trying to set permissions for. And I do not want to do this via fstab as it will not help when I hand the drive to a friend for him to connect to his computer.

Is it not possible, nor advised, to change the permissions and owner to the most liberal for a shared data drive? Just think of a drive of music and videos that a circle of friends pass around to each other. No one is going to put anything sensitive on it . . .

Maybe excluding executables might be wise, otherwise, it seems what I am trying to do is the best. I just can't figure out why it's not working . . .

---

### Post by gregconquest on 2008-09-20
Bumping myself . . . This seems so easy, and I'm so close. Someone please take a look at post #5 above and help me out. Why can I not make the changes stick?

TIA.
Greg

---

### Post by mb_webguy on 2008-09-20
I'm laboring under the apparent delusion that ownerships of partitions on removable drives are determined upon being mounted.  When I plugin one of my several external drives, it mounts as owned by root:root, but with universal r/w/x permissions.  The contents, however, could have different ownership and permissions, but those could be easily changed with a recursive chown statement.

---

### Post by gregconquest on 2008-09-20
> **mb_webguy said:**
> I'm laboring under the apparent delusion that ownerships of partitions on removable drives are determined upon being mounted.  When I plugin one of my several external drives, it mounts as owned by root:root, but with universal r/w/x permissions.  The contents, however, could have different ownership and permissions, but those could be easily changed with a recursive chown statement.

So, you're saying that a(n ext2/3) partition cannot have different permissions and owners -- only directories have this flexibility? If you are right, then that is the route I'll have to go.

However, even though my command line attempts have not yet worked, I did launch nautilus as root and I did successfully change the owner and permissions of the whole partition last night. However, this is not the best way to do this. I feel like I am cheating somehow . . . And bearing this out, when I plug in the drive now, two instances of nautilus are launched for each partition. One of the FAT32 partition nautilus wondows says at launch, "You do not have the permissions necessary to view the contents of "FAT32_160_"." The owner and group are listed as "root", and no one can read or write to it. The other Fat32 nautilus window, for the same partition, says that root can read and write at the folder level.

 The same split happens with the NTFS partition. One nautilus window says anyone can read and write, the other is all grayed out.

Only the ext3 partition has the same owners and permissions across both windows.

Somehow, maybe since I changed the owners and permissions from nautilus as root, nautilus is mounting each partition as both root and user??? I don't know what is going on, but I feel vindicated in trying to do this from the command line from the beginning.

But why am I not getting the answer here? Online documentation, as far as I can find it, misses this rather general scenario.  Most guides/tutorials/discussions simply say to use fstab. The others say to use Fat32. This all seems rather retarded to me. I know what I want, but I'm not getting the answer even when asking in the ubuntu forum.

Is the level of supprt so low that getting a good answer to a linux question is a crapshoot? How many times do I have to "bump" my own question? Do I have to pay? Where do I go if I want to pay for a linux answer? Of course, I'd immediately post the answer for all to see . . . . . . .

Frustrated,
Greg

PS The current situation is still all laid out in post 5.

---

### Post by mc4man on 2008-09-21
this has become more confusing then it should be. I don't have a mac here today so thats' a bit of a wild card (will tommorrow night.
So just in terms of windows and linux.  (using a simple example of 2 partitions - theory holds for more
(keeping in mind windows can access Ext 2/3 with ext2fs or similar)

If the intention is that windows users can only access the fat 32 partition then use primary partitions and make the fat32 the *first one*.

If the intention is that windows users can access both the fat32 and ext2/3 (I'd use Ext2 in this case) then make the **whole drive** an *extended partition* with fat32 and Ext2 partitions inside. (logical drives

For the Ext2 all you need to do then is connect the drive (on your linux install), find the *mount point of the Ext2 partition* and do this

```
sudo chown [COLOR="Red"]doug[/COLOR]:[COLOR="Red"]doug[/COLOR] [COLOR="Red"]/media/disk[/COLOR]
```
 adjust red for your user name and mount point of the ext2 partition

At this point all linux users can read and write to both partitions (see last line), windows will see both partitions and with ext2fs can assign a drive letter and read /write to the Ext2.

If you were using primaries then at this point windows will only see the fat32 and again linux users will see both and have rw as above.

I can't account what you've done previously so I'd start over.

If you want I'll test mac access tom. night

**If** any linux users have a problem with the Ext2  have them run the exact same command (adjusting as needed to *their *username/mount point), only needs to be done once.

---

