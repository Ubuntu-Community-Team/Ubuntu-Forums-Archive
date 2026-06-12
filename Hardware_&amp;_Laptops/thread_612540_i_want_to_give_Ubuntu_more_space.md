---
title: "i want to give Ubuntu more space"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by linuxuser187 on 2007-11-14
I was wondering if anyone could help me with this problem i'm having. Basically i want to give my ext3 linux partion more space, 

currently the ext3 partition is at 32.59gb and i freed up 52.21gb from my ntfs windows partion using gparted from the ubuntu live cd, gparted is recognizing the unallocated space, the issue is that when i go to resize the ext3 partition it says that the max is 32.59gb and will not let me pass this amount, 

i also made sure that i sudo umount /media/sda2 which is the ext3 partition, so after a while of trying to mess around with resizing i gave up lol, so then i said ok i'll just try setting up a 2nd ext3 partition and i'll transfer all my movies and stuff to that partition,

the partition was setup but when i mounted the volume the only thing i saw in it was a lost&found folder which when i tried to double click on gives me a error saying i do not have permission viewing the folder, when i tried to copy anything to that volume i also get the same error so basically that partition was useless, 

i deleted that partition and with the 52gb of unallocated space i created a extended partition /dev/sda4, once it was created it still showed i had 52gb unallocated and that the size of /dev/sda4 was 52gb but under the column "Used" there was nothing indicating no space was used so i created another ext3 partition under the extended partition and this one was /dev/sda5 which i gave it 52gb, 

it was created and it mounted itself under /media/disk and reported 1gb used, so again i go check out the volume and there's a lost&found folder again which i still can't acess and i get the same error and i still can't copy anything over to the volume as the same error comes up, 

if i right click on the drive and click on properties and go to the permissions tab everything is grayed out, don't know if this will help but i also tried to unmount every volume and set up the partition again and still no good, i could also access my ntfs partition but this info is probably irrelevant.

So that's my problem lol,  i know i'm not doing something right and i can't seem to find out what i'm doing wrong, also when i right click the drive on my desktop and click on properties and click on the volume tab i see setings which you can type in a mount point, file system and mount options

If anyone knows what i could try out or do please let me know or let me know what i'm doing wrong cause i need to give ubuntu more space as it's my main desktop! 

Also i want to have 2 linux partions as i will be installing a fresh copy of 7.10 on one and have all my stuff like movies on the other partion. i'm running 7.04 right now. 

Thank you in advance! :)

---

### Post by bingoUV on 2007-11-14
There is no problem with lost+found folder. It is a remnant of ext2 days, and it will not harm you at all.

You cannot access your mounted partition because it was not mounted with you as the owner. Mount it on a folder of which you are the owner, with the options "users". 
```

mount /dev/sdaX /path/to/your/folder/ -o users

```

Currently you can access those partitions as root.

---

### Post by afonic on 2007-11-14
Actually do yourself a favor and burn a LiveCD like Gparted Live or PartedMagic (I like the second teh most).

It's a really small download and you can use the live cd to move, resize etc your partitions easily.

---

### Post by linuxuser187 on 2007-11-14
Thanks for the tips guys, when i tried to mount like you suggested but i think i'm doing something wrong cause this is what i get

luis@laptop:~$ mount /dev/sda5 /home/luis/mount -o luis
mount: only root can do that
luis@laptop:~$ sudomount /dev/sda5 /home/luis/mount -o luis
bash: sudomount: command not found
luis@laptop:~$ sudo mount /dev/sda5 /home/luis/mount -o luis
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i will download the live gparted cd and try that

---

### Post by linuxuser187 on 2007-11-14
ok so i used the gparted cd and was able to resize the partition but what i really want to do is to setup a second partition to move all my stuff onto that partio so i could format my / and install a clean copy of 10.4, i created the partition as a ext3 and mounted it under /home/luis/mount but still get the same error of "you do not have permission to write to this folder" when trying to copy anything over, any ideas anyone? If i can't find a solution i can always backup my stuff to dvd's and format the 2 partitions but to copy all that stuff wil take forever.  Thx again!

---

### Post by linuxuser187 on 2007-11-14
Now i know why everyone recommends to setup a second partition for you're /home lol, i should have done this to begin with when i was setting up ubuntu

---

### Post by GSBoomer on 2007-11-14
Take a look at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) or any of the other tutorials you'll find if you google: Ubuntu home partition

---

### Post by linuxuser187 on 2007-11-16
Thank You, i will try that!

---

