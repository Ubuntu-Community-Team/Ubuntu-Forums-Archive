---
title: "Dmraid not recognizing array"
date: 2008-12-30
forum: Hardware
---

### Post by Cl0cKw0rK on 2008-12-30
My nvidia array is not being recognized by dmraid. I have checked, and everything is supported. dmraid -r and dmraid -ay both return "NO RAID Disks". I am running the latest (2.3.27-9) ubuntu server, and this is the first time i've tried something like this. Any help would be appreciated.
Thanks
~ClOcKwOrK

Edit: fdisk -l shows the array as a 1500gb volume (its 4 500gb in raid 5) and I can see some partitions I had made on there, Kinda. Output is

Disk /dev/sdb: 1500.3 GB, 1500323512320 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fc31fc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       50993   409593240    f  W95 Ext'd (LBA)
/dev/sdb2           50994       76490   204804652+   7  HPFS/NTFS
/dev/sdb5               2       50993   409593208+   7  HPFS/NTFS

I have made those second 2 partitions. The first is beyond my knowledge

---

### Post by hotweiss on 2008-12-31
> **Cl0cKw0rK said:**
> My nvidia array is not being recognized by dmraid. I have checked, and everything is supported. dmraid -r and dmraid -ay both return "NO RAID Disks". I am running the latest (2.3.27-9) ubuntu server, and this is the first time i've tried something like this. Any help would be appreciated.
Thanks
~ClOcKwOrK

Edit: fdisk -l shows the array as a 1500gb volume (its 4 500gb in raid 5) and I can see some partitions I had made on there, Kinda. Output is

Disk /dev/sdb: 1500.3 GB, 1500323512320 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fc31fc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       50993   409593240    f  W95 Ext'd (LBA)
/dev/sdb2           50994       76490   204804652+   7  HPFS/NTFS
/dev/sdb5               2       50993   409593208+   7  HPFS/NTFS

I have made those second 2 partitions. The first is beyond my knowledge

This may sound silly, but did you create the RAID partition in the BIOS?

Here's my dmraid guide for Linux Mint, which is applicable to Ubuntu:

[http://seethisnowreadthis.com/2008/12/25/how-to-set-up-soft-raid-dmraid-in-linux-mint-6-felicia/](http://seethisnowreadthis.com/2008/12/25/how-to-set-up-soft-raid-dmraid-in-linux-mint-6-felicia/)

---

### Post by Cl0cKw0rK on 2008-12-31
yes i did. i have the raid working perfectly fine on windows with the mediashield driver, but there is no such for linux. any way i could maybe get the driver working with ndiswrapper?

---

### Post by hotweiss on 2008-12-31
> **Cl0cKw0rK said:**
> yes i did. i have the raid working perfectly fine on windows with the mediashield driver, but there is no such for linux. any way i could maybe get the driver working with ndiswrapper?

The wrapper is only for wireless cards. Did you try following my guide?

---

### Post by Cl0cKw0rK on 2008-12-31
Some of it. I don't see how most of it applies. i installed dmraid, and modprobed it, but all i have in the /dev/mapper is control

---

### Post by hotweiss on 2008-12-31
> **Cl0cKw0rK said:**
> Some of it. I don't see how most of it applies. i installed dmraid, and modprobed it, but all i have in the /dev/mapper is control

Here there is an example with Nvidia's fake raid:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Cl0cKw0rK on 2008-12-31
Hmm, i thank you for the help. it still isnt working. i modprobed dm-raid4-5 (dm-raid45 didn't exist) and raid456 (just something from another article i was reading). im not trying to install to this raid, i have another completely seperate disk running the OS. ethier you didn't know that, or i am comopletely missing something. any more ides? after i added those modules, and i restarted, a dmraid -ay still came up with "No RAID Disks"

---

### Post by fatbotgw on 2008-12-31
Since the partitions are showing up in fdisk -l, have you tried mounting them?  

I am by no means an expert, but it would seem to me that once the partitions are showing up you should be able to mount them.

---

### Post by Cl0cKw0rK on 2008-12-31
I don't know if I want to do that. there is 2 entries in fdisk fro the same location (sdb1 & sdb5). I don't know what will happen if I try something. and i doubt it could recognize it when dmraid wasn't installed by default, and you need software to work this raid.

---

### Post by fatbotgw on 2008-12-31
In your fdisk -l,

Device Boot Start End Blocks Id System
/dev/sdb1 2 50993 409593240 f W95 Ext'd (LBA)
/dev/sdb2 50994 76490 204804652+ 7 HPFS/NTFS
/dev/sdb5 2 50993 409593208+ 7 HPFS/NTFS


Your sdb1 is a logical partition, while sdb5 is a partition inside that logitcal partition.

You can only have 4 primary partitions (sdb1 and sdb2 in your case) total on a hard drive.  While you can have more total partitions if you use logical partions like you did with sdb1/5.

As long as you mount sdb5 you shouldn't have any problems.

---

### Post by Cl0cKw0rK on 2008-12-31
I feel i should tell you all that I am running this server as a vm in windows. i have added the physical disk to be allowed access by the vm. i just realized that i think that the windows mediashield will take control of what i am writing and reading from the raid. my only problem now is when i try to mount it, it says that the ntfs partition is in use (I know, I know, but i created the partition in windows and i would only allow ntfs. if i could change it to something else and not lose all of the data, i would). the partition is not even mapped in windows, let aloine in use by it. i could force the mount, but i don't know what the side effects are. any siggestions?

---

### Post by fatbotgw on 2008-12-31
I don't really know...haven't used VM's much.

The only thing I can think of is the "Shared Folder" option in VM-Ware.  That allows the guest to have access to folders in the host.  However, you would have to have the partition mapped to a drive letter for any of the programs to see and use it.

---

### Post by Cl0cKw0rK on 2008-12-31
not quite. you can "add hardware" what i did was allow the vm to see the raid volume, and then made it so that the raid volume wasn't mapped in windwows, essentially the same as not mounted.

---

### Post by Cl0cKw0rK on 2008-12-31
My main question here is, given that im not going to be writing anything to this partiton in linux, can i safely mount it? (with the force option)

---

### Post by fatbotgw on 2008-12-31
I don't see why you shouldn't be able to.  I'd use the "ro" option just to make sure it's not writeable.

---

### Post by Cl0cKw0rK on 2008-12-31
Hmm. i try this command "sudo mount -rf /dev/sdb5 /mnt" adn i get no response. i try "ls -a /mnt", and i get nothing. trying "umount /dev/sdb5" returns a not mounted error. any ideas?

Edit: i know there is data on the drive

---

### Post by fatbotgw on 2008-12-31
Don't you have to specify the file system???  The -t option?

Also, try a different folder...make a new one inside of /mnt and try mounting to that folder.

something like:  sudo mkdir /mnt/windows

then mount to /mnt/windows

---

### Post by Cl0cKw0rK on 2008-12-31
Now, i think it might be actually mounted. i do "sudo mount -t ntfs /dev/sdb5 /mnt/music -o ro,force" and i get no response. ls-a turns up nothing in music. but now umount does not return a device not mounted error. the question now is WTF is happening???.

EDIT: sorry, its 4 am here

---

### Post by fatbotgw on 2008-12-31
After you mount it, does it show up if you just type "mount"?

If it's actually mounted, it should show up there.

If it does show up and nothing is in the folder, what happens when you try sdb2?

---

### Post by Cl0cKw0rK on 2008-12-31
think i found my problem. it says the type is "fuseblk". never heard of it before, but for some reason it is overridding my ntfs.

---

### Post by fatbotgw on 2008-12-31
fuseblk has to do with ntfs-3g which allows you to write to ntfs drives.

This is what one of my drives shows up with:
/dev/sdc2 on /media/Movies type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)

Did you try another partition?

---

### Post by Cl0cKw0rK on 2008-12-31
new info. After doing some reading, i found that i might need ntfs-config, which i didn't have. installed, and it still mount right. sdb2 mounts the same way.

---

### Post by fatbotgw on 2008-12-31
when you mount it, use "-t ntfs-3g" and see if that helps.

see if that makes a difference.

---

### Post by Cl0cKw0rK on 2008-12-31
Hmm, yep, so fuseblk is acceptable, but i am still not seeing anything in the mounted dir.

---

### Post by Cl0cKw0rK on 2008-12-31
ok, well, the ntfs-3g still produces the fuseblk, which is acceptable, but i still can't see anything.

---

### Post by fatbotgw on 2008-12-31
When it shows up in Windows with it's own driver letter it has stuff there right?

If not, then it won't have anything in ubuntu either.

---

### Post by Cl0cKw0rK on 2008-12-31
yep, just double checked. it still has all of the folders and data.

---

### Post by hotweiss on 2008-12-31
Try to go into your RAID's BIOS, delete the RAID partition, and then create it again. Maybe your old RAID data is screwing things up. I remember when I split my Vista RAID drive and the only used one of the drives for Ubuntu. Ubuntu could see the second drive, but when I would try to format it, gparted would crash.

---

### Post by Cl0cKw0rK on 2008-12-31
that won't preserve the data, will it? I don't want to lose that data.

---

### Post by fatbotgw on 2008-12-31
Nope, you'll need to back it up first.

---

### Post by Cl0cKw0rK on 2008-12-31
any other ideas besides recreating the raid? i want that to be my last step. I have a drive that i can backup the data to, but it will take a long time, and it is a pretty extream step, especially since windwos can see thta daata, and ubuntu sees it as one contiguous drive.

---

### Post by fatbotgw on 2008-12-31
Try a network share.

Setup the share in windows and browse the network in ubuntu.  Since the VM goes through windows for networking it should be pretty simple.

---

### Post by Cl0cKw0rK on 2008-12-31
how do i specify a shared directory with samba?

---

### Post by fatbotgw on 2008-12-31
Specify the share in Windows.  Right click on the folder and click "Sharing"

Then, in ubuntu go to Places -> Network -> Windows Network and browse from there.

---

### Post by Cl0cKw0rK on 2008-12-31
you forget, i have no gui. anybody no how to get to a shared folder in command line, maybe via samba (i have it).

---

### Post by Cl0cKw0rK on 2008-12-31
Alright, the shared folder thing is a good temp fix, but i will need to actually get teh raid working sometime. Anyway, im going to bed now. Good night all, And thanks for the help. If somebody leaves a suggestion i will look at it and respond tomorrow.

---

### Post by fatbotgw on 2008-12-31
That I did...sorry.

Try this:  [http://ubuntuforums.org/showthread.php?t=149844]("http://ubuntuforums.org/showthread.php?t=149844")

---

### Post by hotweiss on 2008-12-31
> **Cl0cKw0rK said:**
> that won't preserve the data, will it? I don't want to lose that data.

Hmmm, I didn't know that you wanted to preserve the data. This problem is then out of my league.

---

### Post by Cl0cKw0rK on 2008-12-31
i can't firgure how to use samab on command line to connect tp a shared folder, anybody with experience or ideas?

---

### Post by fatbotgw on 2008-12-31
What I typed in was this:

smbclient //phoenix/store/

phoenix being my server and store being the shared folder

It asked for my password and then connected.  from there I could see the contents with ls

Also, to get back to the normal command line type "exit"

---

### Post by Cl0cKw0rK on 2008-12-31
It all works now. i don't know whaty i was doing wrong, but i added the appropriate lines in fstab, adn it worked. thanks for all the help guys.

---

