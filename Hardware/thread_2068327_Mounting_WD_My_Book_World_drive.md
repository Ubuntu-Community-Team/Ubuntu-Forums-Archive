---
title: "Mounting WD My Book World drive"
date: 2012-10-08
forum: Hardware
---

### Post by butch81385 on 2012-10-08
Hello,

My WD My Book World drive has crapped out on me.  I took the hard drive out of the case and put it into my desktop.  I am now trying to access the drive with the only purpose of recovering data (and if the drive is still good, wiping it clean and formatting it to work in windows).

After reading countless threads, I believe that the file system is xfs. However, trying to mount gives me "Can't read superblock".  

Any ideas?

---

### Post by Bucky Ball on 2012-10-08
Are you using Ubuntu???

---

### Post by butch81385 on 2012-10-08
Sorry, I've been driving myself crazy with this that I missed some important info!

I am using a ubuntu live cd (created a couple of months ago) for doing all of this.

The hard drive is a WD Green 1TB that came from a first gen (blue rings) My Book World Edition.

I know my way around a computer, but my linux knowledge is very limited.

---

### Post by cprofitt on 2012-10-08
You may want to use 'Disk Utility' to determine if you are correct about it being XFS or not. My MyBook Live is using ext3 and ext4 and not XFS.

There is a chance to recover as the article below shows, but I think knowing 100% what the file system is will be crucial.

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by butch81385 on 2012-10-08
I will check on that tomorrow. Some people said it was ext3, some said it was a raid stup, bt trying to mount as an ext3 (or 2) gave the error that the FS was wrong. I also tried to follow directions for using mdadm with no luck (the drive shows 4 partitions. 3 are 1-3GB each and the last is 999GB. Using the disk utility (I think that was the name) it shows it correctly with the right overall size, but says "unknown" for each partition.

---

### Post by butch81385 on 2012-10-09
Used Disk Utility. Partition types are all listed as unknown. Partitioning is "Unknown Scheme"

Tried the dumpe2fs from the link you provided. Response was "Couldn't find valid filesystem superblock."

---

### Post by butch81385 on 2012-10-09
Following the suggestion of another website, I tried the command dmesg | grep "[sh]da"

a ton of similar results popped up.  A typical one looked like:
[ 940.967521] sd 2:0:0:0 [sda] CDB: Read(10): 28 00 00 7b cb 39 0 00 08 00
[ 940.967540] end_request: I/O error, dev sda, sector 8112953
[ 940.967581] sd 2:0:0:0 [sda] Unhandled error code
[ 940.967586] sd 2:0:0:0 [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

That repeats dozens of times with either the first number in brackets changing, the sector changing, or both.

Do you think that the hard drive fried when the enclosure died?

---

### Post by Bucky Ball on 2012-10-09
That might be the case. It would be good to confirm what those file systems were, though, but that is going to be difficult.

---

### Post by butch81385 on 2012-10-09
Tried using Photorec, both for ext2/ext3 file systems and for "other" file systems.  For both the bottom line always reads "Error reading sector (sector number)" and says 0 files found.

My assumption is that this drive is toast (or at least the data on it is corrupted beyond repair). Fair assumption?

Luckily I have backups of my most important photos, but lost a bunch of other stuff (this was my backup, and my old laptop just had it's hard drive die around the same time, so anything that didn't get transferred to the new comp is gone). 

Unless anyone has anything else to try, I am guessing my next step is to format the drive to see if it is usable for anything.

---

### Post by Bucky Ball on 2012-10-10
I wouldn't rush. The boot partition looks like the sectors are out of whack, quite understandable considering what happened. You might have a look here:

[http://www2.uic.edu/~aciani1/sector_blues.html#3.5](http://www2.uic.edu/~aciani1/sector_blues.html#3.5)

... or dig for this error:

 "Error reading sector (sector number)"

If you can fix that sector, though I don't know how others will, you have a better idea. I'd try do that before killing it.

PS: I looked for WD Smartware that would probably remedy this but as old drive they have no relevant software for  the World.

PPS: I'm wondering if restoring the boot sector would remedy this? Shouldn't kill the data and if it doesn't work then that's ruled out and no worse off. This might give some clues:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A2oKmMqs93RQPDIAw6gK5gt.?p=restore%20boot%20sector%20external%20hard%20drive&fr=altavista&fr2=sfp](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A2oKmMqs93RQPDIAw6gK5gt.?p=restore%20boot%20sector%20external%20hard%20drive&fr=altavista&fr2=sfp)

---

### Post by butch81385 on 2012-10-10
Everything I found for fixing sector read errors were things that I already did with the exception of the dos program HDAT2. Unfortunately I ran that and it gives me an error:
"ERROR reading of the IDENTIFY DEVICE data ata error FFH: Media error/time limit out".

Not looking promising...

---

### Post by Parker32 on 2012-10-11
According to the manual, the MyBook supports both the CIFS/SMB and the NFS protocols.

CIFS/SMB is the protocol natively used by Windows for accessing network drives. You should be able to access the MyBook on a Linux/Unix system by using the smbclient or mount.cifs, e.g. to access (mount) the "public" folder on MyBook on the local directory /mnt you would issue (from a root terminal):

mount.cifs //ip.address.of.mybook/public /mnt -o username=admin,password=admin_passwd_on_mybook
or, equivalently:

mount -t cifs -o username=admin,password=... //ip.address.of.mybook/public /mnt
where:

you can substitute "public" with "download" (to access the pre-defined download share) or any share name that you have created with the MyBook storage manager.

username/password can be those of any user that you have created on the MyBook storage manager interface; or just use -o guest instead of -o username=...,password=... to specify "Guest" access.

Access by the NFS protocol is not enabled by default; you have first to enable it in the "Advanced" tab of the MyBook storage manager, then you can mount the disk shares via NFS with:

mount -t nfs ip.address.of.mybook/nfs/public /mnt

Again, "public" can be any defined share name.

---

### Post by Bucky Ball on 2012-10-11
@ Parker32: No offense but I think you are missing the point. This drive is probably toast, has a messed up boot sector and the user can't mount it at all. In the first post OP states that the drive is not in an external box anymore but in the computer so, as informative as your post is, it is redundant. ;)

---

### Post by butch81385 on 2012-10-11
Bucky,  I got fed up late last night and just tried to format it...  Wouldn't format via drive utility (input/output error) nor could I delete anything using any dos based hard drive zero-er.  To me that means that the drive is fully toast.

Thanks for all of your help, and you too cprofitt.

---

### Post by Bucky Ball on 2012-10-11
Yep, that really cooked it by the sounds. Hard luck ...

Please mark thread as 'Solved' from Thread Tools. ;)

---

### Post by cprofitt on 2012-10-11
> **butch81385 said:**
> Bucky,  I got fed up late last night and just tried to format it...  Wouldn't format via drive utility (input/output error) nor could I delete anything using any dos based hard drive zero-er.  To me that means that the drive is fully toast.

Thanks for all of your help, and you too cprofitt.


Sorry to hear that it is toast... thinking I might need to get a second 'backup' drive now.

---

### Post by Bucky Ball on 2012-10-11
> **cprofitt said:**
> ... thinking I might need to get a second 'backup' drive now.

Ha, yea. Happens everytime I see this happen! ;)

---

### Post by m3topaz on 2012-10-25
I mount the MyBookLive drive the 'long' way:

$ sudo mount -t cifs -o username=<mybookusername>,password=<mybookpwd>,rw,users,uid=1000 //192.168.1.200/<mybooksharename> /localfolder

Then for backup I use rsync:

$ rsync -avv --delete /home/<homefoldername> /localfolder

12.10 Note:
I had just updated to Quantal and this process actually failed, with an error in dmesg as follows -
"cifs_mount failed w/return code = -22"
Solved and back to normal now with the install of cifs-utils:
$ sudo apt-get install cifs-utils

---

### Post by Bucky Ball on 2012-10-25
[B][I]Thread Closed

Reason:[/I][/B] Done, dusted and 'Solved'. Nothing more to add.

---

