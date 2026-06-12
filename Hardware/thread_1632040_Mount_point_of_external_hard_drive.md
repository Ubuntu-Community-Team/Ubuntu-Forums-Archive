---
title: "Mount point of external hard drive"
date: 2010-11-27
forum: Hardware
---

### Post by Jebus721 on 2010-11-27
I recently purchased a 2 TB external hard drive and wanted to format it. Being a linux newbie, I wasn't sure the best way to go about this, so, I turned to the internet.
[This]("http://www.ehow.com/how_1000631_hard-drive-linux.html") is the page that I followed to format my 2 TB, making one 1 TB partition and leaving the rest as blank space, for future installations of Debian or the like.
Now, after restarting, it is all mounting perfectly fine, except that it is mounting with an odd name (92bccb85-37be-4ca1-b0bf-70c90cfda755) that I really would prefer not typing in every time... Is there any way to fix this? It is mounting under /media, just for clarification, but it is not in my fstab, and it is always that same name.

---

### Post by Fafler on 2010-11-27
Yes. Just enter the first letter in the name and press tab. Bash will finish as much of the word as possible. Every one should know that trick.

Back to what you really asked about. I'm pretty sure, that if you give the partition a label, it's going to mount it under that name instead of the current method, which is based on UUID.

First type
```
df
```
to establish the device name of the drive. It's probably /dev/sdb1 or similar.

Now change the label with
```
tune2fs -L newlabel /dev/sdb1
```

Change newlabel and /dev/sdb1 to the actual name you want and the right devicename.

---

### Post by coffee412 on 2010-11-27
> **Jebus721 said:**
> I recently purchased a 2 TB external hard drive and wanted to format it. Being a linux newbie, I wasn't sure the best way to go about this, so, I turned to the internet.
[This]("http://www.ehow.com/how_1000631_hard-drive-linux.html") is the page that I followed to format my 2 TB, making one 1 TB partition and leaving the rest as blank space, for future installations of Debian or the like.
Now, after restarting, it is all mounting perfectly fine, except that it is mounting with an odd name (92bccb85-37be-4ca1-b0bf-70c90cfda755) that I really would prefer not typing in every time... Is there any way to fix this? It is mounting under /media, just for clarification, but it is not in my fstab, and it is always that same name.


Well, Im old school here and I still believe that doing it by command line is the best way to do it. So, Ill show you how I would do it. Keep in mind there is always more than one way but this should do.

First we need to know what the drive is called when its plugged in. Its going to actually be a device name like /dev/sdd. We can find this by looking thru our logs. Specifically the file /var/log/messages. Since this file is so large and full of stuff we dont need we will filter it for only hard drives. Type the following in - 

sudo cat /var/log/messages |grep sd

We are looking for the the lines that discribe your new drive you plugged in. For examples sake we will assume its /dev/sdd ok?

Now lets partition it. If all your using it for is your linux install I recommend a ext3 partition. If you want to be able to plug it into a windows box  then use fat32.

fire up fdisk and partition it:

sudo fdisk /dev/sdd

Choose P for printing out the partition info. If there are already partitions on it then you can delete them. Otherwise choose N for new partition and choose ext3. Then select W to write the info to the drive and exit. The partitioning is done.

Now we want to format it. I assume that you created one large partition so here is the command for formatting it.

sudo mkfs.ext3 /dev/sdd1

Notice the one at the end of the device? Thats the first partition (and your only one).

There you go! Now you can unplug it and just plug it in again and it will mount it.

I do believe that Ubuntu uses the UUID of the drive when mounting it. Dont let it bother you. It will always be mounted in /media though. Good spot for it.

:p

---

### Post by Jebus721 on 2010-11-27
Haha, thank you for that tip! That tab thing is really interesting, and something I actually didn't know... Now, another question from what you posted Fafler: with that command, is it giving a label to the sdb1 partition? That is what the partition is in my /dev, but I was wondering how that would act if I plugged in a flash drive and then plugged in my external after that. Would I get the name that I labeled sdb1 for my flash drive?

---

### Post by Fafler on 2010-11-27
Linux is full of neat little tricks like that.

The device name (eg. /dev/sdb) are dynamically given to each device every time you connect a new block device (flash, external hd, SATA, you name it). Your internal harddrive is probably /de/sda. If you connect a flash drive, it will be /dev/sdb, and now if you connect you external drive, it will be /dev/sdc. As we can never be sure, we are going to mount according to the label instead of the device name. Right now the part of Ubuntu that determines the mount point already does something similar and uses the UUID to determine the mount point. I think the behaviour will change when a label is added. Atleast, it does that with FAT formattet driver and theres no reason why this should behave different.

Jusk make sure you use the right devicename and give it the label you want.

---

### Post by Jebus721 on 2010-11-27
Okay, well thank you both very much! It all seems to be working so far, and I feel I have learned a lot already!

---

### Post by Fafler on 2010-11-27
You're welcome.

---

### Post by Jebus721 on 2010-11-27
Okay... New problem: it seems that that partition is being automatically mounted with only root permissions. I know how to solve this with an fstab file, but I can't seem to make it work with the tune2fs.

---

### Post by Fafler on 2010-11-27
If we knew that, we could have used the UUID from the start.

Look at the line in fstab to mount /boot:
```
UUID=d46dd72a-05a5-4608-afc7-28901802fcda /boot           ext2    defaults        0       2

```

Just copy the UUID= method or use LABEL= in the same way.

---

