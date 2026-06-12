---
title: "[SOLVED] Trying to move ubuntu to my main drive"
date: 2008-07-23
forum: General Help
---

### Post by skutter2k on 2008-07-23
Having installed ubuntu to a smaller drive to try it out I have decided to make the jump from windows. Unfortunately I installed Hardy on my slower drive and I want to move it to my faster one. I have managed to get things set up on my faster drive (that has doze on it too) however I got right up to the point where I wanted to boot to the new ext3 and something has gone wrong but I can't figure out what.  Here is my current situation:

drive 1:

ntfs partition - just somewhere to keep old stuff atm
ext3 partition - my current live version of Hardy
swap partition - does what it says on the tin.

drive 2 (the quicker "tareget" drive):

swap partition - (this was one of those awful recovery partitions for doze so I just changed it to be a swap partition ready for later - it's recognised by my existing Hardy installation and has been added on ok).
ntfs partition - my current XP installation.
ext3 partition - Where I would like to run Hardy from in future.

I should point out that I have successfully used rsync to copy my copy of Hardy from drive 1 to drive 2 however while I can see the ext3 partition in drive 2 I cannot mount it any more?! Not sure why that would be - I did try to install grub to this drive but that seemed to go ok and not sure why that would make a partition viewable in parted but unmountable.

The reason for wanting to move the partition rather than do a fresh install is because I have built up a lot of stuff since I installed it to "trial" it and only recently realised how much work I have done in Hardy and how little in doze, lol!

Any help would be most appreciated!

---

### Post by mannheim on 2008-07-23
When you say that it is unmountable, what do you mean?

For example, if you boot from the working ext3 partition on drive 1, and then try and mount the other ext3 partition, do you get an error message. For example, open a terminal and do something like:

```

sudo mkdir /media/test/
sudo mount /dev/xxxx /media/test/

```

where "xxxx" is the ext3 partition on drive 2. Is there an error?

---

### Post by skutter2k on 2008-07-23
aha, I am new to linux so I missed the create a folder bit when trying to mount it.

I get "mount: unknown filesystem type 'promise_fasttrack_raid_member'"

which I suspect stems from an earlier problem I had. After I had successfully copied everything into the new ext3 I installed grub and when I rebooted the drive had vanished. The only way I could get it back was with my raid bios software so I'm guessing that mucked up a flag somewhere.

I have that out of my depth feeling now, lol.

Does this sound fixable or am I best off starting from scratch with the partition again and getting some help when I get to the grub part?!

---

### Post by mannheim on 2008-07-23
If it's a muckked-up-used-to-be-raid problem, then I'm afraid I am out of my depth also. Since copying things over with rsync is fairly painless (once you've figured out how to do it once), my suggestion would be to wipe the ext3 partition on disk 2, and try to recreate it to see if you can get a mountable ext3 partition there before going any further.

---

### Post by skutter2k on 2008-07-23
The odd thing is that the ntfs and swap partitions on that drive are fine, only the ext3 is "broke", lol. Think I will reformat the partition and rsync it again then come back for some grub advice when I get it back to how it was a couple of hours ago, lol.

Thanks for your help.

---

### Post by skutter2k on 2008-07-23
Right, back to where I started but much better this time. I can now see everything in the other partition so everything rsync'd over just fine. I can mount the drive too this time so that's good. All I need now is to get it to boot to the new partition rather than the old one. I've tried making a few changes with grub but I'm a bit wary. Advice would be most welcome please.  I feel like success is just around the corner :)

Thanks

---

### Post by mannheim on 2008-07-24
You could proceed like this. (I am assuming you don't have and have never had a separate partition for /boot.) Doing it this way will still use the grub files on your old partition, but will allow you to boot to the new one. (This is a safe way to start, but don't delete the old partition.)

On the new copy which you created using rsync, you will need to edit the file /etc/fstab. In that file, there will be a reference to your old hardy partition, with a line that instructs linux to mount the old partition at "/". You need to change that line so that it refers to the new partition (either by its name of the form /dev/xxx or by its uuid).

Similarly, in the new partition, you will need to edit the copy of /boot/grub/menu.lst, replacing references to the old partition with references to the new one. These references are in three places. (The second two are only used by the Debian/Ubuntu auto-update-of-grub features.) First, in the "root=xxxxxx" part of the stanzas that look like
```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.24-19-generic root=XXXXXXX ro quiet splash
initrd          /initrd.img-2.6.24-19-generic
quiet

```

Second, in a stanza near the beginning that looks like

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)


```

(Grub numbers stuff starting from 0. This line would be changed to (hd1,3) for the fourth partition on the second drive.) Third, in a line like

```
# kopt=root=XXXXXXX ro
```

After you have replaced all references to the old partition in the new menu.lst, you can proceed as follows. Edit the copy of /boot/grub/menu.lst on your **old** and add a stanza at the end like this:

```
title		Ubuntu on my new partition
savedefault
configfile	(hd1,3)/boot/grub/menu.lst

```

replacing (hd1,3) by whatever grub calls your new partition. This will add a new menu item to the old grub menu. The new menu item will "chain" on to the menu on the new partition. Following this chain, you will be able to boot to the new partition. If it doesn't work, you haven't broken the old setup, so you can boot to the old partition.

Once this works, you can dispense with the old partition by getting grub to go straight to the new partition. To do this, boot to new partition, and then do something like

```

sudo grub-install /dev/sda

```

where (I'm presuming) sda is the disk that your BIOS looks to for the boot loader.

---

