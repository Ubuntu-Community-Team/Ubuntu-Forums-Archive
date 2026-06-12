---
title: "Partitioning Stuff..."
date: 2008-09-10
forum: General Help
---

### Post by beagler on 2008-09-10
So, I first installed ubuntu on this machine I'm using right now and didn't know what i was doing, really. I went for the manual route since i didnt want to erase all the data off the hard drive i wanted to put ubuntu on. Luckily I backed it up since i ended up erasing the whole partition and then still manually putting ubuntu on it. 

I guess I used all four primary partitions when I tried to install. Im pretty sure you don't need any more then 2 primaries to install ubuntu(main and swap?). So, as you can see in the .png i attached, I have 4XX gigabytes which are totally unused. I want to format it as fat 32 so I can store all my movies and songs on there and access from windows and ubuntu easily. Do I need to re-install ubuntu totally or is there something else I can do? 

If i re-install I could fix it but i'd like not to do that since I already have everything set up just how I like it. Thanks in advance for any help.

---

### Post by hyper_ch on 2008-09-10
(1) turn swap off
```

sudo swapoff -a

```

(2) delete the swap partition

(3) create an extended partition

(4) create a new swap partition inside the extended one

(5) create a new ext3 or ntfs partition inside the extended one ( windows drivers for ext2/3: [http://www.fs-driver.org](http://www.fs-driver.org) ), for ntfs in linux use ntfs-3g

(6) edit fstab to alter the swap entry
```

sudo nano /etc/fstab

```

(7) alter the swap entry to something like
```

/dev/sdb5  swap  swap defaults 0 0

```
right now it will probably reference by the UUID

(8) exit and save nano

(9) activate swap
```

sudo swapon -a

```

That's it

---

### Post by deb_untu on 2008-09-10
> **beagler said:**
> So, I first installed ubuntu on this machine I'm using right now and didn't know what i was doing, really. I went for the manual route since i didnt want to erase all the data off the hard drive i wanted to put ubuntu on. Luckily I backed it up since i ended up erasing the whole partition and then still manually putting ubuntu on it. 

I guess I used all four primary partitions when I tried to install. Im pretty sure you don't need any more then 2 primaries to install ubuntu(main and swap?). So, as you can see in the .png i attached, I have 4XX gigabytes which are totally unused. I want to format it as fat 32 so I can store all my movies and songs on there and access from windows and ubuntu easily. Do I need to re-install ubuntu totally or is there something else I can do? 

If i re-install I could fix it but i'd like not to do that since I already have everything set up just how I like it. Thanks in advance for any help.

Use Gparted and partition the unallocated space to any number of partitions and format it as fat32.

Hope you have windows OS on /dev/sdax.

---

### Post by beagler on 2008-09-10
Thanks a bunch to both of you. I'm currently at work so i cannot try the complicated reply out, but it sounds good and i'll give it a shot once i get home.

deb_ubuntu, thanks so much for your reply. It would be very easy to do it that way, but i accidentally made all four of the current partitions into primary partitions, and there is a limit of 4 primary partitions per hard drive. So, in other words, i dont think that I can do that method, although i'd love for it to be that simple. 

I'll let you guys know how the tough method goes, thanks.


PS: Windows is on a totally separate hard drive.

---

### Post by beagler on 2008-09-11
Hmmm...

Something isn't working quite as I had expected. I don't know what I could have done wrong, as your directions seemed fairly straightforward and accurate to my knowledge. But, something must have gone craazy, since it came up with an error and said it could only complete 3 of the 4 actions. I took another screen shot since they're worth 1XXX words.

---

### Post by hyper_ch on 2008-09-11
well, you still need to formate the new partition (and then also add to fstab but I've forgotten to write that above)

---

### Post by beagler on 2008-09-22
I Still haven't gotten around to this. I've been busy and forced to boot into windows lately. Thanks for the help, though, and i'll let you know if i run into more trouble.

---

