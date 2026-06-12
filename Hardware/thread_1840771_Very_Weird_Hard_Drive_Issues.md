---
title: "Very Weird Hard Drive Issues"
date: 2011-09-08
forum: Hardware
---

### Post by Ericj1186 on 2011-09-08
This is a repost because the forum I posted to couldn't figure it out.

I really don't store much on my laptop, but when I installed Ubuntu, I gave it about 250 GB (half the hdd).

Just now I was alerted that I only had 2GB left. Confused, I checked. My root folder has 122GB and is at 100% full. My home folder, I think was at 118 GB or something and it is at 96% full... When I use the folder explorer, it says I have zero free space left.

Any idea what is causing this and how to fix it?

I went to root and according to the properties, the largest folder is home with 15.5 gigs. This makes no sense.

I did **du -sh *** while under root, and it showed my largest file/folder as my home folder which had a 115GB, but when I check the properties of that folder it only has the aforementioned 15GB.

Stranger still, I used this command
```
find . -type f -size +10000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```
as a super user and it found a file called /.xsession-errors.old at 103GB.  I go to confirm this, but I cannot find this file anywhere.

Anyone have ANY clue what is going on?

---

### Post by YesWeCan on 2011-09-08
Possible fs corruption? Might be worth running e2fsck from live CD.

---

### Post by Ericj1186 on 2011-09-08
What's an fs corruption, how would I have gotten that, and how can I fix that?  Just use the ubuntu live disc or is there a good utility disc to use?

---

### Post by YesWeCan on 2011-09-08
fs=file system
It might not be corrupted but when utilities disagree it raises suspicion. You must not run the check on a running system so thats why you need to boot a live CD or USB first.
Then do
sudo e2fsck /dev/sdxy  (select x and y for your Ubuntu partition)

Then report any errors.

---

### Post by YesWeCan on 2011-09-08
Another thing is to run Disk Utilty and check the SMART data to see if your hard disk is having problems.

---

### Post by YesWeCan on 2011-09-08
> **Ericj1186 said:**
> Stranger still, I used this command
```
find . -type f -size +10000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```
as a super user and it found a file called /.xsession-errors.old at 103GB.  I go to confirm this, but I cannot find this file anywhere.
Being a file that starts with a . it will not show up in the file browser window unless you select the "show hidden files" option. You can list all file types in a terminal in you root directory using
ls -al /

**Run the fs check first** and if ok...
Check whether this file is there. If it is then then delete it. It looks like a log of errors related to your linux x windows system. Have you been having graphics problems?

---

### Post by Ericj1186 on 2011-09-08
I'll run those checks tonight after work.

Graphic issues-wise: not a one.  I get some internet slow down now and then, but really, I haven't had anything of issue.

---

### Post by Grenage on 2011-09-08
Either way, it's obviously worth taking a look at the log, just to see what it's complaining about.  It's likely something insignificant and easy to rectify, and it will stop the same problem occurring.

---

### Post by Ericj1186 on 2011-09-09
> **YesWeCan said:**
> fs=file system
It might not be corrupted but when utilities disagree it raises suspicion. You must not run the check on a running system so thats why you need to boot a live CD or USB first.
Then do
sudo e2fsck /dev/sdxy  (select x and y for your Ubuntu partition)

Then report any errors.

I apologize for the late response.

I had seven different partitions of various lengths.  My message for the one I believe was my Ubuntu boot was (It read System: Linux):

```
/dev/sda6: clean, 344678/8650752 files, 32186619/34573312 blocks
```

Since I was unsure, I checked the rest.  For SDA1 (listed as Unknown under system) and SDA2 and SDA3 (listed as HPFS/NTFS under system)
```
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in superblock while trying to open /dev/sda*

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193
```

For SDA4, which is listed as Extended under the system column, I got this:
```
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
```

For SDA5 and SDA7, which are listed as Linux swap/Solaris, I get:
```

/dev/sda* is mounted.

WARNING!!! The filesystem is mounted.  If you continue you ***WILL*** cause ***SEVERE*** filesystem damage.

Do you really want to continue?
```

I put no to continuing.

I load Disk Utility, and I just have one 320GB HDD, which I do the check File System option AND the SMART data.  The first came clean, and the second showed all good/n/a.

So, how would I find this file?

I mounted my disk on this screen, and it says I have 142GB system (which is correct), and I have 127.3 GB used, with only 2.5 free, which is VERY incorrect.  On that same screen that showed all that, it says "Contents: 285,154 items, totaling 12.1 GB (some contents unreadable)."  Is this difference important?

---

### Post by YesWeCan on 2011-09-10
That all looks fine. You only needed to do the check on your Ubuntu fs which is sda6. The others fail because they are not ext.

So boot your Ubuntu and open a terminal and type
ls -alh

and you should see that 103GB .xsession-errors.old file listed.
Then type
tail .xsession-errors.old

and post the output here. Tail shows the last few lines of a file. In this case the most recent entries.
Then delete it
rm .xsession-errors.old

---

### Post by Ericj1186 on 2011-09-10
> **YesWeCan said:**
> That all looks fine. You only needed to do the check on your Ubuntu fs which is sda6. The others fail because they are not ext.

So boot your Ubuntu and open a terminal and type
ls -alh

and you should see that 103GB .xsession-errors.old file listed.
Then type
tail .xsession-errors.old

and post the output here. Tail shows the last few lines of a file. In this case the most recent entries.
Then delete it
rm .xsession-errors.old

That would be easy except with your first command I get:

```
-rw-------  1 155K 2011-09-09 21:52 .xsession-errors.old

```

From root, I ran du -sh * again to find my biggest files, and the largest was 15GB.  Confused, I check my properties on my navigation folder, and it 104.7GB free.

It fixed itself.

---

### Post by YesWeCan on 2011-09-10
Ah, the Force is powerful in you master Luke.

Don't forget to mark this solved in [COLOR="Red"]Thread Tools.[/COLOR]

---

### Post by Ericj1186 on 2011-09-19
It's back.  My hard drive read 104GB free.  It dropped to 97.7GB, then when I waited, it dropped to 97.5.  

Any ideas on how I can catch this quickly?

Now at 93.3GB.  It's slow to open up my file explorer.

---

