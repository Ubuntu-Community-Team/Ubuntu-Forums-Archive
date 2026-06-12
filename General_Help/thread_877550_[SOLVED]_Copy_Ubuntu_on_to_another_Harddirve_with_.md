---
title: "[SOLVED] Copy Ubuntu on to another Harddirve with reinstalling?"
date: 2008-08-01
forum: General Help
---

### Post by robotman5 on 2008-08-01
is there Such a Way to do that?:guitar:


also i made a typo i meant "With out Reinstalling"

---

### Post by mdsharp24 on 2008-08-01
Look into the partimage project: [http://www.partimage.org](http://www.partimage.org)

---

### Post by K2712 on 2008-08-01
```
man dd
```

[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

dd attempts to copy byte for byte from one medium to another.  It's a low-level tool, I'm not sure if there are any front-ends to it or not.

---

### Post by robotman5 on 2008-08-01
Shouldnt i just Ghost The Harddrive and put it on the other hardrive?:confused:

---

### Post by mdsharp24 on 2008-08-01
yep, dd is great, read this post: [http://ubuntuforums.org/showthread.php?t=581680](http://ubuntuforums.org/showthread.php?t=581680)

---

### Post by mdsharp24 on 2008-08-01
partimage and dd do the same thing as ghost

---

### Post by dark_phantom on 2008-08-01
I did this once with my laptop, but without changing a disk.  There's no reason why it wouldn't work.  First make a backup with this command.

sudo tar cvpzf /tmp/backup_file.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp /

Then, install your new drive and install ubuntu.  Then to restore your data, type this sudo tar xvpzf backup_file.tgz -C /.

That should be it, the key here is that each hard drive has a unique uuid and therefore you can't simply write the old one.  It won't boot up if you do so, that's why you exclude /etc/fstab

---

### Post by Linja on 2008-08-01
Sure, I have done that in the past. Here is my own approach. It is a bit more work but it has certain advantages. Unlike dd, it doesn't make a clone. dd requires a targer partition that is at least as large as the original, my own approach does not. The advantage over cloning software (such as partimage) is that it uses only a small set of core commands that will reduce the risk of running into bugs; on top of that, it is more flexible: with a little imagination, you can organize your copy differently than the original. For example, if the original is only a single partition, you can split it up into several. This gives you the kind of flexility that you had when you got to choose partition while installing.

Steps to follow:
1 get second hard drive
2 prepare your partitions; you can use gparted to do this from within your current ubuntu install
3 boot from the live cd
4 mount your partitions two at a time. This requires a bit more explanation. First, you need to make mount points on the live cd (you need to do this only once):
sudo mkdir /mnt/from  (this represents a partition you are going to read from)
sudo mkdir /mnt/to (this one is a partition you are going to write/copy to)
5 Next, run sudo fdisk -l to see the names of your partitions and use those to do the mounting. If, say, your current / partition is /dev/sda2, you mount it with:
sudo mount /dev/sda2 /mnt/from/
Then you mount the partition that you are  going to copy to (this will be one on your second hard drive - I will assume that you choose sdb2):
sudo mount /dev/sdb2 
Now change to your /partition and start the copying process:
sudo cp -av * /mnt/to/ 
This part could take quite a bit of time, from a few minutes to at least half an hour.
When the prompt returns, the data have been written. Verify by changing to /mnt/to and doing an ls -al. If you are satisfied, do a cd and unmount both partitions:
sudo umount /mnt/to
sudo umount /mnt/from
Repeat this process for all your partitions, until everything has been copied.
6 Next comes a few vital corrections. The fstab and grub files still point to the original partitions, which won't work, of course. So mount your new / partition on /mnt/to and open fstab:
sudo gedit /mnt/to/etc/fstab
replace the old UUIDs with the names of the relevant partitions on the new drive (sdb2, sb3, ...)
If your boot partition is on the root partition, the next step is:
sudo gedit /mnt/to/boot/grub/menu.lst
If /boot is on a partition of its own, unmount / and mount /boot on /mnt/to, then open the file with sudo gedit /mnt/to/grub/menu.lst.
Look for the line that says root=UUID... and replace it with the identifier of your / partition (sdb2 in my example).
7 That should be it. Unmount /mnt/to and reboot. Go into BIOS and make your computer boot off drive 2. 
Do not delete the original install until you are sure that the copy works fine. It is best to wait at least a few days so you can at least get back to the original should something go wrong.

Of course, it is essential that you follow these steps meticulously. Not doing so will result in a failed copy at best and a borked original at worst. In fact, if you have not customized too much yet, it will be a lot more convenient (and faster) to do a reinstall.

---

### Post by mdsharp24 on 2008-08-01
I agree the above tar command would work, and I know this is HIGHLY debatable, but if you use the above tar command as stated, I would do it in recovery mode to limit the number of open files. Again, many ppl will come behind me and argue that, but thats my thought.

---

### Post by Linja on 2008-08-01
Never mind. I am messing with the submit options ...

---

### Post by Linja on 2008-08-01
Yes, tar would work. It could be more convenient but it could also break a few things (e.g. if the original uses soft links).

---

### Post by robotman5 on 2008-08-01
or i could format both harddrives (im dualbooting but just want Linux)

then ill do a Fresh Install of Ubuntu on the 80.00GB harddrive then just get recordmydesktop back and Xchat



ah ill just ask my dad on how to do it.:guitar:

---

