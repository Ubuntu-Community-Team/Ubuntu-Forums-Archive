---
title: "Formatting Secondary HDD"
date: 2015-03-22
forum: Hardware
---

### Post by ryan148 on 2015-03-22
Hello,

Currently I'm running Ubuntu from a SSD and I also have a 3TB HDD as a secondary drive for storage.  I can't seem to get the drive to partition/format for whatever reason - I keep getting an error message.  I attached a screenshot - any ideas?

Thanks!

---

### Post by yancek on 2015-03-22
It might be because you are using MBR partitioning which has a limit of 2TB for a partition.  Try creating two partitions of 1.5TB each and formatting.  Do an online search for MBR partition limits and you will get a lot of sites explaining it.

---

### Post by ajgreeny on 2015-03-22
I have never used the Disks utility to format or add partitions to a disk but have always used gparted from a live system, although as it is an unformatted disk you should also be able to do this if you installed gparted to your current Ubuntu installed OS.

Does the disk have a partition table at the moment?  I am not even sure if disks utility can create a new partition table, but gparted certainly can.  With a 3TB disk I think you will have to have a GPT partition table for that disk and GPT partitions.

---

### Post by ryan148 on 2015-03-22
@ajgreeny - gparted got the job done- thanks!  

Now that it is correctly partitioned, how do I change the permissions?  I can't drag anything onto it because I don't have permission.  See my screenshot and let me know if you have any ideas.

Thanks!

---

### Post by weatherman2 on 2015-03-22
The easiest way I can think of requires a quick terminal command.  Open a terminal (Ctrl Alt t) and type

```

df

```

to see where the new partition is mounted, if anywhere.  If not mounted yet, then type:

```
sudo mount /dev/sdb1 /mnt
```

to mount the partition temporarily at /mnt .  Replace "/dev/sdb1" with whatever your new partition's device ID is - you can find this in gparted.

Now, after the drive is mounted, type

```

sudo chown -R YOURNAME:YOURNAME /mnt

```

(replace YOURNAME with your Ubuntu username)

(if you had already mounted the partition somewhere besides /mnt, using your mouse, then replace "/mnt" with "/media/YOURNAME/whatever" that would show up in the df command.)

Finally, unmount the partition if you mounted it to /mnt above:

```
sudo umount /mnt
```

---

### Post by ryan148 on 2015-03-22
you guys are good, @weatherman2 this worked perfectly, thanks!

---

### Post by ajgreeny on 2015-03-23
I hope you did not change ownership of /mnt from root to you as user

You should have mounted the disk to a subfolder of /mnt and changed ownership of just that subfolder not /mnt as a whole.

---

### Post by weatherman2 on 2015-03-23
> **ajgreeny said:**
> I hope you did not change ownership of /mnt from root to you as user

You should have mounted the disk to a subfolder of /mnt and changed ownership of just that subfolder not /mnt as a whole.

If he followed my instructions exactly, he would not have changed the ownership of the /mnt subdirectory itself, only of the files/directories in the partition mounted there.  There was no need to make a subdirectory.

---

### Post by ajgreeny on 2015-03-23
Your suggested command was ```
sudo chown -R YOURNAME:YOURNAME /mnt
``` which would change ownership of /mnt and all of the subdirectories and files in /mnt

---

### Post by weatherman2 on 2015-03-23
> **ajgreeny said:**
> Your suggested command was ```
sudo chown -R YOURNAME:YOURNAME /mnt
``` which would change ownership of /mnt and all of the subdirectories and files in /mnt

That was the intention, to change ownership of the top-level directory in the new partition so the user would own it and be able to create files there.

The command does not change the ownership of the /mnt directory itself in the root directory, unless nothing is mounted in /mnt.

---

### Post by ajgreeny on 2015-03-24
> **weatherman2 said:**
> That was the intention, to change ownership of the top-level directory in the new partition so the user would own it and be able to create files there.

The command does not change the ownership of the /mnt directory itself in the root directory, unless nothing is mounted in /mnt.
Are you certain about that because I believe you are wrong?
**man chown** and my own understanding implies that your command will apply to the top folder, ie /mnt in your example,  and all subfolders and files in /mnt; /mnt is not in the new partition as you seem to be suggesting; it is in the root of the main OS as it always is.  I therefore think it is necessary to use the chown command on the full pathway of the mountpoint, not on the /mnt folder that contains the mountpoint folder.

Just as an example I have an external disk with a single ext3 formatted partition which I use for backups.  It automounts when attached to **/media/user/partitionlabel** as you would expect, but in order to be able to write to that disk's partition I have to recursively change ownership of that mountpoint, ie **/media/user/partitionlabel** but not /media itself

---

### Post by weatherman2 on 2015-03-24
> **ajgreeny said:**
> Are you certain about that because I believe you are wrong?

Well, I tried it myself, following my own instructions above with a new partition, and it works just as I said.  The ownership of the original /mnt folder was not changed.  If you still don't believe me, I suggest you try it yourself as well.

---

### Post by ajgreeny on 2015-03-25
I just did and in my case both /mnt and a subfolder of mnt that I added to it became owned by me, just as I expected, so something strange is going on here if that is not what you are seeing.

Has anyone else who has read this got any comments; who is right?
It could be very damaging in many situations if a system folder that has had the chown -R command wrongly applied became owned by a user other than root.

---

### Post by weatherman2 on 2015-03-25
> **ajgreeny said:**
> I just did and in my case both /mnt and a subfolder of mnt that I added to it became owned by me, just as I expected, so something strange is going on here if that is not what you are seeing.

That makes no sense.  If you mount a partition on /mnt and it had subfolders before you mounted there, those subfolders become invisible in the filesystem, because the new filesystem supersedes them.  How could chown operate on them?

Are you sure you really mounted a partition directly in /mnt?

---

### Post by ajgreeny on 2015-03-26
Doh!!!

You are correct, of course.

My problem was not thinking through the mounting of a disk as opposed to simply using the chown command on /mnt with subfolders already in existence.

I had totally forgotten a horror I went through a long time ago when I mounted a separate partition I had made in my own home and then found that all my home folders and files had disappeared.  This was also before I had got into the regular habit of making backups, as I now do, and so I began to think I had lost everything.

Of course a simple unmount of the partition and all my files were back.
Sorry for the confusion, and I am now happy to say again that you were right; I was wrong.

---

### Post by weatherman2 on 2015-03-26
No worries - glad you figured it out!

---

