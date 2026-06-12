---
title: "How to make ubuntu see my raid1 setup?"
date: 2013-12-20
forum: Hardware
---

### Post by michaeljj2 on 2013-12-20
[COLOR=#333333][FONT=UbuntuRegular]I have raid1 setup that i was using in windows. Now I want to see it under ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Under Disks>Devices I see the 2 x 500gb hard disks as sdb and sdc (on sda is ubuntu) and Contents says "Intel matrix raid member" for both of them[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]also there is another device under "Other devices" that's called 500gb block device and is /dev/dm-1[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]so how do i mount/see that so i can use it in the file manager?[/FONT][/COLOR]

---

### Post by michaeljj2 on 2013-12-22
no one has experience with raids?

---

### Post by michaeljj2 on 2013-12-31
please

---

### Post by steeldriver on 2013-12-31
I don't have any experience with Intel matrix raid and only a littlewith softraid (mdadm), however AFAIK 'matrix raid' should be supported via the dmraid module - is the dmraid package installed? do you have a symlink to /dev/dm-1 in /dev/mapper?

What filesystem is on the raid? if you're not sure then try

```
sudo file -sL /dev/dm-1
```

After that it should just be a matter of creating a mount point and mounting it

---

### Post by michaeljj2 on 2013-12-31
thank you for your answer!
dmraid is installed
in /dev/mapper i have symlink just to cryptswap1 which is the swap partition obviosly
the file system of the raid is NTFS

do i need to create symlink? will installing mdadm help me?

---

### Post by steeldriver on 2013-12-31
I don't really like giving advice that I can't test on my own systems, but my understanding is that newer versions of Ubuntu *should* detect and map dmraid volumes automatically, my guess is if that is not happening it's because the array is in an inconsistent state. The first (guaranteed non-destructive) thing you could try is looking in the logs to see if there's any evidence of attempts to activate the raid e.g.

```
dmseg | grep 'dm-1'
```
or
```
grep 'dmraid' /var/log/syslog
```

(I don't honestly know which log - dmesg or syslog - or what exact term to grep for, you will need to experiment)

Beyond that it *should* be safe to at least try to activate the array manually

```
sudo dmraid -ay
```

There is also a 'dmraid -r' option that I *think* should attempt to discover any raid metadata and report on the status without modification - **don't** add -E else it may erase metadata (not necessarily a bad thing, but let's not go there yet)

There are a couple of real raid experts on the forum (e.g. rubylaser) so depending how important this data is you may wish to wait for them to check in

---

### Post by michaeljj2 on 2013-12-31
ok i'll look into that.
But just to make sure in the meantime, since the Disks utility reports them as raid members and i can see the block device, is there any chance that simply manually mounting the block device /dev/dm-0 to something in /media/ make it visible?
Also maybe it's important to mention that the whole raid partition is encrypted by TrueCrypt. 
Which by the way doesn't see it and can't mount it, when telling it to auto find mountable volumes for that password.

---

### Post by michaeljj2 on 2014-01-01
i couldn't do much with the logs since i'm quite new to linux but when did
sudo dmraid -ay

i got message that the raid set is already active (for both hdds)

so does that mean that i'm very close to actually seeing them?

---

### Post by steeldriver on 2014-01-01
well I would have expected a /dev/mapper/xxxx link to have been created but I don't think there would be any harm trying to mount the /dev/dm-1 device directly - however you may want to pm one of the raid experts before proceeding

```

sudo mkdir /mnt/raid

sudo mount -t ntfs-3g /dev/dm-1 /mnt/raid

```

---

### Post by michaeljj2 on 2014-01-01
thank you very much for all the help!
I'll try that tomorrow, hopefully the experts will show up in the meantime :)

---

### Post by michaeljj2 on 2014-01-02
still haven't tried it so if someone else wants to chip in... :)

---

### Post by michaeljj2 on 2014-01-07
> **steeldriver said:**
> well I would have expected a /dev/mapper/xxxx link to have been created but I don't think there would be any harm trying to mount the /dev/dm-1 device directly - however you may want to pm one of the raid experts before proceeding

```

sudo mkdir /mnt/raid

sudo mount -t ntfs-3g /dev/dm-1 /mnt/raid

```


finally tried that and it gives
Failed to mount /dev/mapper/is_ii...._disk: Invalid Argument
The device doesn't seem to have valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g.  /dev/sda, not /dev/sda1


my guess is that because the whole raid is encrypted with truecrypt it doesn't regonize it as ntfs?

---

### Post by michaeljj2 on 2014-01-09
any ideas? :(

---

### Post by steeldriver on 2014-01-09
sorry I must have missed where you mentioned that the raid was encrypted - that is even further beyond my level of experience - I suggest you PM 'rubylaser' with a quick note + a link to this thread

---

### Post by michaeljj2 on 2014-01-14
I made it!
Here is what i found.
The truecrypt encrypted volume is NTFS but linux doesn't recognize it as a healthy one, so I GUESS that's why it doesn't mount it. Neither auto or from the terminal (gives error in the terminal) For example i can see the partition under windows, but cant' read it either, so I guess linux doesn't even bother to mount it.

TrueCrypt would mount it normally, but because it's raid for some reason it can NOT do it auto. Even if you go to select a device manually in TrueCrypt, you can see the both HDDs that are part of the raid but can't see the raid block itself. I guess they just didn't get to supporting this out of the box in the linux version?
So, you have to mount from the terminal, with truecrypt /dev/dm-1 or whatever the raid block name is. Because the GUI just doesn't see it.

At least that's what  I found. It took me quite some time to find it, so writing it up here for someone else to find when in need.
Please note that i'm linux newbie, so if something that i said doesn't make sense, please correct me.


And thank you steeldriver, for all the help and support, it's truly appreciated!

---

