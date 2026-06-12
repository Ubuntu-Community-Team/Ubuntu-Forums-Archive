---
title: "USB flash pen drive possibly corrupt - no partition table detected -cover data?"
date: 2012-03-14
forum: Hardware
---

### Post by RememberWhenItRained on 2012-03-14
Hello Ubuntu community.

  My friend gave my his USB pen/flash drive to try and see if i could recover the files off of it. I am not sure what happened, but i'm guessing he accidentally pulled it out during a read/write.

So - here's the deal: it does not seem to automount, and attempting to manually mount proves to be a chore that falls through (where the heck is /media anyway?)

I know the drive is detected, and it has an LED indicated it is working/plugged in. I ran GParted, it found it as /sdb but says there is not partition table data. No luck attempting to recover data with GPart. Also, no luck with TestDisk analyzing sectors as it also cannot find partition data.

Now I know I could simply reformat, but is there a way to recover data? I know the drive is there, because entering the following in the terminal
```
sudo fdisk -l /dev/sdb
```
yields
```
Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a56f

Disk /dev/sdb doesn't contain a valid partition table
```

and ```
lsusb
``` finds
```
Bus 002 Device 009: ID 05dc:c753 Lexar Media, Inc.
``` among other things.

also
```
collin@collin-Inspiron-1440:~$ dmesg | tail
[15608.328403] scsi12 : usb-storage 2-1:1.0
[15609.330121] scsi 12:0:0:0: Direct-Access     Lexar    USB Flash Drive  8.07 PQ: 0 ANSI: 2
[15609.331580] sd 12:0:0:0: Attached scsi generic sg2 type 0
[15609.335065] sd 12:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[15609.335628] sd 12:0:0:0: [sdb] Write Protect is off
[15609.335635] sd 12:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15609.337575] sd 12:0:0:0: [sdb] No Caching mode page present
[15609.337581] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[15609.340330] sd 12:0:0:0: [sdb] No Caching mode page present
[15609.340334] sd 12:0:0:0: [sdb] Assuming drive cache: write through

```

what am i missing/where am i going wrong? any suggestions? Thanks folks.

{I'm running 12.04 Beta1 if that matters, but i don't think it does.}

---

### Post by winh8r on 2012-03-14
When you ran testdisk did you also run a check using the "none" option in the partition type menu?

Also if you know what data is on there, you can run photorec(part of testdisk) and recover different data by filetype.

---

### Post by RememberWhenItRained on 2012-03-14
> **winh8r said:**
> When you ran testdisk did you also run a check using the "none" option in the partition type menu?

Also if you know what data is on there, you can run photorec(part of testdisk) and recover different data by filetype.

I did indeed. No fruitful results. I also thought about changing geometry, but i don't know if that's safe or what to look for.

Unfortunately, i'm not sure about the data type. I can ask though.


There was an app i used to use for Windows- Recuva - Ubuntu have anything like that? I think there would be plenty that would do the trick but the invalid partition table doesn't help.

---

### Post by RememberWhenItRained on 2012-03-14
attached screenshot

---

### Post by winh8r on 2012-03-14
Knowing the data type is not absolutely necessary as Photorec will recover everything by default. The problem is that the filenames will be messed up and it is often easier to recover say, all the jpegs to one folder then all the docs to another, or else it all just gets recovered in the order it is written on the disk, can be a bit of a headache having to go through a 10GB file and rename everything.

you might want to take a look at 


scrounge-ntfs

and 

gddrescue

they are both in the Ubuntu repositories and available from the software centre.

I have not used scrounge-ntfs, but have used both testdisk/photorec and gddrescue many times to recover data from accidentally deleted or corrupted partitions.

Hope this helps you in some way.



EDIT***** I have just done an experiment on a 1Gb USB drive and removed it while data was being written to it, also used disk utility to format it to FAT and not partition it to try and mess it up as much as possible and I have  ended up with same result as your screenshot above but photorec is now running and recovering all data.

---

### Post by RememberWhenItRained on 2012-03-14
> **winh8r said:**
> Knowing the data type is not absolutely necessary as Photorec will recover everything by default. The problem is that the filenames will be messed up and it is often easier to recover say, all the jpegs to one folder then all the docs to another, or else it all just gets recovered in the order it is written on the disk, can be a bit of a headache having to go through a 10GB file and rename everything.

you might want to take a look at 


scrounge-ntfs

and 

gddrescue

they are both in the Ubuntu repositories and available from the software centre.

I have not used scrounge-ntfs, but have used both testdisk/photorec and gddrescue many times to recover data from accidentally deleted or corrupted partitions.

Hope this helps you in some way.



EDIT***** I have just done an experiment on a 1Gb USB drive and removed it while data was being written to it, also used disk utility to format it to FAT and not partition it to try and mess it up as much as possible and I have  ended up with same result as your screenshot above but photorec is now running and recovering all data.

thanks  for the tip on PhotoRec. It seems to freeze though with a little over 5 mins left.

Also, is there a way to auto-rename the files and restore the structure, or will that have to be done manually?

Also, i will want to reformat back to FAT32 before recopying the files back onto the drive, correct?

(sorry for the "dumb-ness" of the questions.)

---

### Post by winh8r on 2012-03-14
The file renaming is unfortunately a manual job! I think the way photorec looks at it is this , "I have done my bit , now you do yours!!"

To reformat the drive, yes use FAT32 as this is the most compatible with different OS (Win, Mac, Linux)

Probably best to do a few test read and writes to and from it before you put everything back on though, just to make sure it is not going to do it again.

When Photorec looks like it is freezing it has probably either encountered a large file (video, .iso etc) or it has found a corrupted part of the file system and is trying and re-trying to trecover whatever fragments it can from there. I usually run it overnight on larger drives and it almost always completes. (If it cannot complete it will exit with an error in most cases rather than just hang)


EDIT** There is no such thing as a "dumb" question, all are valid , that is how mistakes are avoided!!!!!


Glad you got the data back!

Well done

---

### Post by RememberWhenItRained on 2012-03-14
> **winh8r said:**
> The file renaming is unfortunately a manual job! I think the way photorec looks at it is this , "I have done my bit , now you do yours!!"

To reformat the drive, yes use FAT32 as this is the most compatible with different OS (Win, Mac, Linux)

Probably best to do a few test read and writes to and from it before you put everything back on though, just to make sure it is not going to do it again.

When Photorec looks like it is freezing it has probably either encountered a large file (video, .iso etc) or it has found a corrupted part of the file system and is trying and re-trying to trecover whatever fragments it can from there. I usually run it overnight on larger drives and it almost always completes. (If it cannot complete it will exit with an error in most cases rather than just hang)


EDIT** There is no such thing as a "dumb" question, all are valid , that is how mistakes are avoided!!!!!


Glad you got the data back!

Well done

thank you sir! I mistook that at first and killed the process, fortunately, TestDisk was nice enough to ask if i wanted to restore previous session.

I appreciate all your help.

Also, just now got your username. i almost "lol'ed." After trying the consumer preview of Win8, i'm leaning that way too. MS seems to have a great, bad, great, bad, streak going on with their releases. And don't get me wrong, windows itself is alright, but i like linux better because i can be under the hood, have great [free] support, and it costs nothing! :D

As a potential spoiler: Win8 has no {traditional} start menu. you have to do some serious mods to get it there. They basically implanted their MetrOS from their phones into the system. I can see they're shifting towards tablets, but IMHO, it's terrible. Some non-involved users like it, but for anyone who wants to do serious work and/or "get dirty" with the system (in other words, not just a causal, internet-only, kind of user) it's...terrible.

---

### Post by winh8r on 2012-03-14
No problem, glad I could help.

You can mark the thread as [SOLVED] using the Thread Tools at the top of your page.

Good Luck.

---

### Post by RememberWhenItRained on 2012-03-14
how long is normal to wait? (working with a 8GB drive.) Is there a way i can be certain it's not frozen? (screenshot attached, if it helps. It's uptime has been a lot longer than it says.

---

### Post by winh8r on 2012-03-14
Hard to say really without knowing if there were a lot of large files on there to begin with.

Usually if it is all jpegs and docs it is fairly quick, but i have seen USB drives with video files on them take up to 12 hours before.

Let it run as long as possible would be my advice. You can check in system monitor to see if the process is still running and the amount of cpu it is using should indicate whether it is actually working or just hanging, like I said before it rarely hangs without putting out an error message though.

Checking the size of the output file using "properties" and check it again in half an hour and see if it has increased by any amount will also indicate activity.

---

