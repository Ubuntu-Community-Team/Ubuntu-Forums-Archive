---
title: "Basic Questions - Formatting, flash drives, etc."
date: 2008-11-22
forum: General Help
---

### Post by Roasted on 2008-11-22
So, I have a flash drive... Sandisk Cruzer Micro 8gb. It kept coming up as "disk" and I wanted it to mount as "Sandisk"... so I searched forums and found that if you delete the partition in Gparted, add a new partition, and where the "label" section is you can put in the name there. I typed Sandisk. Now it mounts as /media/Sandisk. Okay great!

But, BEFORE all of that, I was transferring stuff off of it and didn't realize it was still in the process of transferring. I thought it was unmounted. I pulled the drive out and got an error. Ehh, crap.

So I decided to just format it, because I have a backup of the data that was on the flash drive anyway. I go to format it and label it as Sandisk. It says operations successful, but I get an error. Something about being unable to mount.

I was confused. So I tried it again... same deal. Then I decided to format the drive to fat32 (as I had been doing) but not label it. I formatted it in gparted and it came back as /media/disk. Okay, back to square one.

So I delete the partition, add a new one, and label it Sandisk. Apply operations and BAM. Works. /media/Sandisk, no errors, mounted fine... etc.

My question is, why did that happen? Was it the fact I pulled out the drive without properly unmounting it that resulted in that error? After that error came up, I assume the fix for it was to format it as FAT32 WITHOUT a label, then afterwards, reformat it WITH a label??

---

### Post by beno1990 on 2008-11-22
It was probably the fact you yanked it without unmounting it. If the disk is having data written to it or read from it at the time you yank it out (including "invisible" operations, ones you don't see or control directly) it risks corrupting the data structure of the drive. Sometimes it'll completely fry the disk, other times, just a single file. Other times, the partition table and you need to reformat/repartition.

The moral of the story is, always double check that your drives are unmounted before yanking them out. ;)

---

### Post by Roasted on 2008-11-22
This is the error I was getting, despite gparted saying it was successful.

Error org.freedesktop.Hal.Device.UnknownError.

I also got this one.

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

EDIT - I don't know what was up with it. There were times I'd format it, I'd get the error, and it would come back in gparted as "unknown" under the file system type. So, I just delete it and reformat it. Seems to work then. I don't know if I were doing things in a weird order or not.

I guess what it comes down to is that when formatting these devices with a label, it seems (in my short experience) that if you format it first, THEN format it again WITH the label, that it seems to work without errors. If I just format it and label it in the same step, I get the error. But if I format it to FAT32, then re-format it to FAT32 and label it, it seems to work fine. I have no problems then. Hmmmmmmm....

---

