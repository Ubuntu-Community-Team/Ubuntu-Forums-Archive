---
title: "HD failure on Vista - trying to access with Ubuntu"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by sheldonnbbaker on 2008-02-24
Hello everyone,

New Ubuntu user as of tonight (really liking it so far).

Anyways, I had a bad hard drive failure last night on Vista (I'm on an HP Pavilion dv6000) - and to make a long story short, the hard drive is spinning very slowly and has lots of bad sectors.

I can't boot up vista - I get a "can't locate winload.exe" error (the master boot record is screwy or something). 

And of course, my only backups were on the hard drive 9didn't think to upload the backups to my server).

So, I've booted up Ubuntu from a CD, and am trying to get some of the data back at least (most important is a 1 gig partition that contains all my web development files etc. - my music, software, and personal documents and such aren't as important).

Ubuntu recognizes my partitions (i.e., 1.0 GB Volume, 12.0 GB Volume, etc.), but, when I try to open them: I get this error message: 

             Cannout mount volume... $log File indicates unclean shutdown (0, 0). Failed to mount 'dev/sda7': Operation not supported Mount is denied because *NTFS is marked in use*. If you have Windows (which, I effectively don't)...disconnect the external devices, etc. Choice 2: Use the 'force' option, e.g., mount -t ntfs-3g /dev/sda7 /media/disk -o (had a siimple error message before which I am trying to work out), or add the option to the relevant row in the /etc/ fstab file:      /dev/sda7 /media/disk ntfs-3g defaults,force 0,0 

Like I said,I'm new to Ubuntu, and to the computer hardware environment, so any help here would be much appreciated.

Thanks for the help :)

---

### Post by taurus on 2008-02-24
Applications -> Accessories -> Terminal
```
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sda7 /media/disk -o force
df -h
```

---

### Post by agim on 2008-02-24
I am very new to linux myself, but when I had a similar problem because of Vista crapping out, I run a PCLinuxOS livecd and it was able to read my windows files. I really don't know why. Some people here might be able to show you how to do this through ubuntu, but if things don't work, try the pclos livecd. If you have a quick connection, start downloading it now, you should have it within an hour.

---

### Post by sheldonnbbaker on 2008-02-24
Tried it (for sda1) and it looks like it works - really slow (window goes gray and doesn't respond somewhat - but it looks like it's there. All of Ubuntu is kinda going slow - but I can see the

If it works, I love you. :)

EDIT: IT WORKS!!!! Thank you so so so much! I honestly can't type how thankful I am. 

One more thing - one of the partitions isn't HPFS.NTFS - it's W95 Ext'd (LBA) - how can I access that one? When I use the code you gave me for sda5, it says 'unknown filessytem type 'ntfs-3g'

Also, I now have three disks showing up on 'Computer': disk, disk (2), and disk (3). When I click on disk, however, it opens up (and highlights) disk (3); same with disk (2).

mother or all edits: fixed everything - somehow got all the partitions mounted - just need my flash drive to work so i can put the files on there!!! how do i do that? instead of sda1 or sda7, what is it?

grandmother of all edits: have everything working! but XP (on my other computer)can't open the files from my flash drive! how do i 'eject'/'safely remove hardware' in ubuntu?

---

### Post by sheldonnbbaker on 2008-02-24
Got everything working (tried unmounting the flash Drive as I took it out of the laptop - that somehow worked).

Thank you SO much everyone. You have no idea how much time and money this saved me.

---

