---
title: "Hard Disk fail"
date: 2011-10-13
forum: Hardware
---

### Post by hartz on 2011-10-13
This morning my laptop was hanging (I could still move the mouse.  Caps Lock still worked.  Num Lock did not.  Clicking on anything had no effect.  Ctrl-Tab, Ctrl-arrows, Ctrl-F1, Ctrl-Alt-BS, etc all had absolutely no effect

Right-click did not bring up any context menus any more.

I eventually decided that I had tried everything and held down the power button and waited for the machine to shut down.

When I powered the computer back on, I first just got nothing after the BIOS stage.

After another cold reset Ubuntu started to present the grub menu on boot-up, but a normal boot-up still produced nothing.

Resetting BIOS to defaults still had no positive effect, or in fact any visible effect at all.

Selecting the recovery option on the BIOS shows that Linux was in fact loading but after a few seconds of fast scrolling messages it went into a loop complaining about disk errors.

The boot process progresses far enough to prove that at least some of the drive is (was) still readable.  I recently reformatted my USB drive and can't right now find a bootable Linux CD, so right now I have nothing else I can boot from.  Therefore I decided to put the drive into an external drive bay and connected it to another Ubuntu computer (A netbook)

It mounted both partitions (OS and home), so I unmounted them and unplugged the drive, fearing at this point that leaving the drive powered when not actively getting data from it is just giving it an opportunity to get worse.

I then bought a new drive onto which to recover my data (No, I don't have backups.  I do have backup software and it is configured to ftp everything onto a server on the Internet every day.  It fails every day.  It has never worked.  I've been meaning to find a way to fix it.)

My home dir is about 600 GB, most of it is ISOs, Virtual Box images and my photos.  A substantial portion is also my collection of technical documents (AIX, Sun, etc).  Almost all of this is near impossible to recover.

Now the second volumes is refusing to mount, complaining about file system corruption.  I also unmounted the first volume since being mounted will just cause random file system updates whenever the OS thinks it is a good idea. Presently I am busy copying the disk using rdd-copy to an image on the new drive (it is progressing at about 10% per hour, now at 60%).  

I've never in earnest used forensic software, and still hope that I won't have to.  My plan is to first let the rdd process finish, then attempt to fsck / fix the file system on the actual drive.

If that works, I may be able to selectively copy what I want off the drive.

If not, I fear I will be forced to try to recover data from the image.  The next option will be to try to mount the image.  Knowing that it is presently a corrupted file system, my first question is:  How would I do this?

My last option will be to try to use a recovery programs such as autopsy, sleuthkit or foremost.

If it comes to this, is there someone here who can guide me since I doubt that this will be plain sailing.

My last question, and the most important one:  Am I going about this the right way, and what other avenues are there that I have not yet thought of?

Cheers,
  _hartz

---

### Post by oldfred on 2011-10-13
Good to have image backup just in case.

I would run e2fsck on each partition.
#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

You can also try alternative superblocks it necessary.

I have used photorec.
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by hartz on 2011-10-14
Hello and thank you oldfred.

This morning I checked the command completion and the rdd process finished seemingly without errors:  The output ended like this:
```

626.766 GB done (100.00%), average speed 18.496 MB/s 
=== done ***
seconds: 34700.380
bytes written: 672998096896
bytes lost: 0
read errors: 0
zero-block substitutions: 0
MD5: 159d2539ddda8b4c0a637ae73d8adb83
SHA1: <none>
```

So keep all your combined fingers crossed for me :-)

---

### Post by hartz on 2011-10-16
I have not had much time to work on this despite being without my laptop causing me to feel like a junky without his drugs.  What I have done is to try fsck on the drive itself (after the image created with rdd-copy was completed without any errors)

fsck keeps on "repairing" the same errors every time I run it.  It seems that fsck THINKS it is actually repairing problems but in fact nothing is changing on the drive.  I ran fsck 4 times and got the exact same result each time.

I have not tried to do any work on the image that I made.  I have discovered (via the links provided by oldfred) that I should use GNU ddrescue, so right now I am making a new image of the disk.  So far I still am not getting any read errors from ddrescue, but the errors in kern.log when Gnome tries to mount the disk looks like this:

```
Oct 16 09:37:18 tv kernel: [  661.220234] sd 6:0:0:0: [sdb] Unhandled sense code
Oct 16 09:37:18 tv kernel: [  661.220276] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_ERROR d
riverbyte=DRIVER_SENSE
Oct 16 09:37:18 tv kernel: [  661.220294] sd 6:0:0:0: [sdb]  Sense Key : Hardware Error [
current] 
Oct 16 09:37:18 tv kernel: [  661.220314] Info fld=0x0
Oct 16 09:37:18 tv kernel: [  661.220322] sd 6:0:0:0: [sdb]  Add. Sense: No additional se
nse information
Oct 16 09:37:18 tv kernel: [  661.220341] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 03 c0 09
 10 00 00 e8 00
Oct 16 09:37:18 tv kernel: [  661.220382] end_request: I/O error, dev sdb, sector 6291688
0
Oct 16 09:37:34 tv kernel: [  677.137240] sd 6:0:0:0: [sdb] Unhandled sense code
Oct 16 09:37:34 tv kernel: [  677.137251] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_ERROR d
riverbyte=DRIVER_SENSE
Oct 16 09:37:34 tv kernel: [  677.137262] sd 6:0:0:0: [sdb]  Sense Key : Hardware Error [
current] 
Oct 16 09:37:34 tv kernel: [  677.137275] Info fld=0x0
Oct 16 09:37:34 tv kernel: [  677.137280] sd 6:0:0:0: [sdb]  Add. Sense: No additional se
nse information
Oct 16 09:37:34 tv kernel: [  677.137292] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 03 c0 09
 18 00 00 e0 00
Oct 16 09:37:34 tv kernel: [  677.137317] end_request: I/O error, dev sdb, sector 6291688
8
```

Any more suggestions before I try to mount the image as a loop device?  Thank you,
  _hartz

---

### Post by hartz on 2011-10-16
No more suggestions?

FTR:

```
~# ./rescue 
DISK=/dev/sdb6
+ DISK=/dev/sdb6
IMAGE=/media/big-disk/ddrescue-sdb6
+ IMAGE=/media/big-disk/ddrescue-sdb6
LOGFILE=/media/big-disk/ddrescue-sdb6.log
+ LOGFILE=/media/big-disk/ddrescue-sdb6.log

ddrescue --no-split $DISK $IMAGE $LOGFILE
+ ddrescue --no-split /dev/sdb6 /media/big-disk/ddrescue-sdb6 /media/big-disk/ddrescue-sdb6.log


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:   491764 MB,  errsize:       0 B,  errors:       0
Current status
rescued:   672998 MB,  errsize:       0 B,  current rate:   29097 kB/s
   ipos:   672998 MB,   errors:       0,    average rate:   19799 kB/s
   opos:   672998 MB,     time from last successful read:       0 s
Finished                   

# Now let it retry previous errors 3 times, using uncached reads:

ddrescue --direct --max-retries=3 $DISK $IMAGE $LOGFILE
+ ddrescue --direct --max-retries=3 /dev/sdb6 /media/big-disk/ddrescue-sdb6 /media/big-disk/ddrescue-sdb6.log


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:   672998 MB,  errsize:       0 B,  errors:       0
Current status
rescued:   672998 MB,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished

# If that fails you can try again but retrimmed, so it tries to reread full sectors:

ddrescue --direct --retrim --max-retries=3 $DISK $IMAGE $LOGFILE
+ ddrescue --direct --retrim --max-retries=3 /dev/sdb6 /media/big-disk/ddrescue-sdb6 /media/big-disk/ddrescue-sdb6.log


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:   672998 MB,  errsize:       0 B,  errors:       0
Current status
rescued:   672998 MB,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished

```

---

### Post by oldfred on 2011-10-16
Were you running fsck or the e2fsck commands I posted?

---

### Post by hartz on 2011-10-17
Your asking this specific question prompts me to re-evaluate my thinking.

I just used fsck, believing that it would invoke e2fsck (or whatever) in the background.

By the way the file system type is ext4.

Right now I must tell you I really badly wish I could snapshot my file systems!

---

### Post by hartz on 2011-10-17
I have now tried the command exactly as you suggested it.  The -p command did nothing (besides telling me not to use -a or -p as it cannot do automatic repair due to unexpected inconsistency.

The second e2fsck command appears to work.  It fixes fewer and fewer problems on each invocation.  After about 5 checks, Ubuntu suddenly mounted the drive - I did not notice because the file manager window opened behind other windows.

When I tried it [the command] again I got a warning that it [the file system] was already mounted.  I found the browser window snd noticed that the disk is excruciatingly slow....

I unmounted the file system and ran the e2fsck command once more - it came up clean for the first time.

I am still concerned about how slow the drive is.  For example if I now unplug and re-connect the drive, the gvfs-gdu-volume-mounter process hogs all the mount points for about 10 minutes (during which I can not unmount the drive)
 
I have now started, for what it is worth, to go through the same process on the "root file system" partition (Nothing on there that I can't get again...)  After this, the slow disk operation seems to have been resolved.

This appears to create two possible paths:  I can now try to recover data directly from the mounted partitions, or from the image file(s) that I have created.

P.S. And where is the option to disable auto-mounting of any new USB drives?

P.P.S I record (script) the sessions whenever I do any work, in case anybody wants to look at anything.

P.P.P.S ... are the reported I/O errors necessarily and definitely an indication of a hardware failure?  Could severe file system corruption alone be the cause of my pains?

---

### Post by oldfred on 2011-10-17
I am afraid I do not know enough to be helpful. Are you able to recover all your data.

You can check hard disk status in Disk Utility. But all I know is if smart status is green it is good, but it has lots of detail for those who may know more.

---

