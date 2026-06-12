---
title: "[SOLVED] Low-level copy (HD to HD)"
date: 2008-10-09
forum: General Help
---

### Post by altonbr on 2008-10-09
I've purchased a 250GB hard drive so I can completely back up my current hard drive in its current state. This way, if my house were ever to burn down or if I had my computer stolen, I would have a complete, bootable backup of all my files - including Ubuntu - so long as it was stored at a second location.

I asked my local computer store if they could do it for me and they said they could for $70-80 CDN.

I was reading about cluster computers when I found an article [1] that stated

> Disk cloning in progress. I used Fedora 8, and the command "dd" to clone the discs from the bootable System rescue CD disc.

> dd if=/dev/sda of=/dev/sdb

If I were to plugin both my hard drives to a neutral PC and ran the above command, would it be a sufficient low level copy that they would be verbatim to each other?

Or can I not use Linux to preform a low-level copy?

It can not be rsync or cp or anything of the like because I have multiple paritions and I need everything to be intact, as is.

[1]http://helmer.sfe.se/

---

### Post by jerome1232 on 2008-10-09
Yes dd makes an exact image of the drive, it copies bit for bit.

You usually want to use the exact type of disk but it should work as long as the target disk is the same size or bigger than the source disk.

man dd for more info about how to use dd.

You may be also interested in PING (Partimage Is Not Ghost) It does it faster than dd (it doesn't read the free space while dd does) and has a gui to help.

---

### Post by EmanresuusernamE on 2008-10-09
Burn a Clonezilla LiveCD and then just run it on your computer. It will use dd, ntfsclone or partimage depending on if the program will run or not.  And it can just make an image for you, and if you like, compress the image to save space.

I use Clonezilla a lot to make images of system, including the partition and MBR data.  Not the greatest of GUIs, but then again, it's meant to work hard, not look good.

---

### Post by az on 2008-10-09
YOu can also use dd to copy to file (just is a filename for the "of" argument).  That way, you can image a smaller drive onto a bigger drive and still use the leftover space or other things.

Just format the filesystem to ext3 or NTFS so that it can handle large files (FAT filesystem cannot).

You can use any of the other tools mentioned in that way, too.

---

### Post by caljohnsmith on 2008-10-09
In case you decide to use the dd command, the dd command by default uses a block size of 512 bytes (1 sector), which is can make copying a whole HDD really slow. A quicker way is to specify a larger block size and use the "conv=notrunc" option so that you still get a perfect copy even if the block size you use is not an exact multiple of the total number of blocks you are copying:
```
sudo dd if=/dev/<input HDD> of=/dev/<destination HDD> bs=10M conv=notrunc
```

---

### Post by altonbr on 2008-10-09
Thanks everyone for your input.

I guess this would be a good method for wiping a hard drive clean too right?

```
sudo dd if=/dev/urandom of=/dev/sda1
```

I know that hardcore forensic computer scientists could still read some sort of data on the disks, but not the casual user.

---

### Post by andrewc6l on 2008-10-09
To wipe the whole drive, you'd probably want to use /dev/sda instead of /dev/sda1 - that will just wipe the first partition. But that is a good (although slow) way to get rid of the data. Best to do it after booting from a CD, since you don't want to overwrite your swap file with random data while you're running :-)

---

### Post by altonbr on 2008-10-09
> **andrewc6l said:**
> To wipe the whole drive, you'd probably want to use /dev/sda instead of /dev/sda1 - that will just wipe the first partition. But that is a good (although slow) way to get rid of the data. Best to do it after booting from a CD, since you don't want to overwrite your swap file with random data while you're running :-)

Haha, oh that's funny. Didn't notice I only had the first partition.. force of habit writing that word I guess.

Thanks for the info!

---

### Post by altonbr on 2008-10-11
> $ sudo dd if=/dev/sda of=/dev/sdb bs=10M conv=notrunc
23841+1 records in
23841+1 records out
250000000000 bytes (250 GB) copied, 5072.8 s, 49.3 MB/s


Amazing. Thank you.

---

### Post by Abdul Haqq on 2008-10-22
I need to double check this before I go out spending.

I want to dual boot my laptop currently it is running Vista. So I buy a new 320G HDD and put it into a 2.5 USB case.

I run Ubuntu Live and execute dd and clone my 160G internal to the new 320G external then just physically swap them.

Is there any problem with this scenario? :confused:

---

### Post by altonbr on 2008-10-23
> **Abdul Haqq said:**
> I need to double check this before I go out spending.

I want to dual boot my laptop currently it is running Vista. So I buy a new 320G HDD and put it into a 2.5 USB case.

I run Ubuntu Live and execute dd and clone my 160G internal to the new 320G external then just physically swap them.

Is there any problem with this scenario? :confused:

There's no problem with this, but you'll have that extra ~160GB free sitting on the end of the 320GB hard drive, so you'll need to use gParted (System > Administration > Partition Editor) to get that space back.

Does that make sense?

---

### Post by jerome1232 on 2008-10-23
One, grub  will be install to the boot sector of that new drive, so you will need to either set it as the first bootable drive and configure grub to boot vista, or install grub to the boot sector of drive that has vista and it should configure itself to boot both os's.

---

