---
title: "I converted my ntfs hd to linux-swap-- is my data lost?"
date: 2008-10-08
forum: General Help
---

### Post by Finest1 on 2008-10-08
So, I was trying to install Ubuntu Linux for the 2nd time because I forgot my password, and it asked me to choose which disk to install Linux on, and it told me that making a swap space would be a good idea. I chose my main HD for this, because the "format" box wasn't checked, so I thought my files would be safe. Linux tried to install itself, and it stopped halfway through, saying that there was some I/O error. Now, I can't boot into the main HD, or the 2nd one, where I tried to install linux. Now, I don't know if it erased my files, because it takes a lot longer to erase over 100GB on my ATA HD. I booted my computer up in the Ubuntu Live CD, and brought up GParted, only to find that it can't read, check, or read label on Linux Swap discs. Is there the slightest chance that I can recover my files, or convert the file system to something linux can read without deleting everything? Is it all gone already, and there is no use trying? What can I do? Please help me, and I'll be forever in debt to you.

---

### Post by bwang on 2008-10-08
Do not use the hard drive (i. e. do not boot or write to it). Visit this site: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). Note that it says do not let the Live CD use the swap partition. To do this, run:
```
sudo swapoff -a
``` in the Terminal from the Live CD.

---

### Post by jerome1232 on 2008-10-08
Your only hope I fear of recovering anything at this point is testdisk and/or data carving.

testdisk can find and restore partitions (the data isn't ACTUALLY written over during a format)

Photorec, Scalpel, and Foremost are data carving programs that can scan the disk for file types and restore them (you'll need another hard drive to write them to) It can find nearly any personal files you might've had on the disc.

This is a decent resource that should help you with recovering the data
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

This is why I always recommend one make backups before partitioning as disasters can happen.

---

### Post by Jim! on 2008-10-08
You *should* be able to recover some of the files because you didn't format the whole disk (You'll need a more experienced user on this forum to help you with that though:D) Just a general thing here but I'm pretty sure you don't ever use your main HD as swap;)

---

### Post by OutOfReach on 2008-10-08
Some of the files may be recoverable, there is really no sure answer to this question.

---

### Post by Finest1 on 2008-10-08
Wow! 2 replies within 10 mins! Thanks a lot! I used the swapoff command. I had an idea to try to run the installer again, and convert the swap disk back to ntfs, but I don't know if it would want to format that. Thanks for the advice though!

---

### Post by Finest1 on 2008-10-09
Well, I ran testdisk and was able to change the swap partition to ntfs, but it said that I have to reboot to have the changes take effect. Now, do I try to boot to the harddrive, or to the Live CD? Another thing: I have Photorec running here, and it's digging up every file I could ever have touched with my computer, except for .m4a or .mp4 files, which are what I encoded my music mainly in, when I was using windows (and iTunes). I can see a lot of wav files, and some mp3's but no .mp4's. I thought Photorec said it could recover those types of files.

**Edit** It has found an .mp4 file! Please disregard. I'm just impatient.

---

### Post by drs305 on 2008-10-09
Just to be safe, I'd boot to the live cd first. Then mount the device with your files and just see if the partition has been restored. If so, you can then reboot normally. If you can't find any files, there may be other steps you can take.

From the livecd Desktop, open a terminal and:
```

sudo mkdir /mnt/temp
sudo mount /dev/sd**XX** /mnt/temp
ls /mnt/temp

```

Hopefully you will see your root directory on the partition. You can also use nautilus to explore the partition. Open it with sudo in case you will be moving files around:
```
gksu nautilus /mnt/temp
```

Can't help with the PhotoRec question.

---

### Post by Finest1 on 2008-10-09
My harddrive is still linux-swap, according to GParted. My thinking is that it'll re-ntfs itself when I restart it and try to boot into it. Does anyone have any ideas?

---

### Post by iponeverything on 2008-10-09
you could go into linux fdisk and change the partition type back ntfs and then try to mount it under linux to see of the data is still intact.

---

### Post by Finest1 on 2008-10-09
I know that the files are intact, I'm carving them right now, with Photorec. When I tried to use testdisk to change it back to ntfs, it told me I'd need to reboot my system for it to change. Whne I do this, should I boot to the Live Cd, which I'm currently using, or into the disk itself?

---

### Post by jerome1232 on 2008-10-09
> **Finest1 said:**
> I know that the files are intact, I'm carving them right now, with Photorec. When I tried to use testdisk to change it back to ntfs, it told me I'd need to reboot my system for it to change. Whne I do this, should I boot to the Live Cd, which I'm currently using, or into the disk itself?

I would boot into the live cd, mount it as read only and browse around see if it looks intact.

---

### Post by Finest1 on 2008-10-09
Actually, I just did mount it, and am now coping it's entirety to a removable drive. It looks like it's all there. If I had known I could do this, It would have saved me a lot of time, waiting for Photorec. I'm pretty sure that everything is intact, and that I got very lucky this time. I'm going to reboot to the drive and see it it will convert back to ntfs. If it doesn't, I still have a back up!

---

### Post by jerome1232 on 2008-10-09
I yeah but it's better to run data carving before testdisk because testdisk writes to  the volume (possibly truly deleting your favorite picture) I thought testdisk should work since all you did was format.

---

