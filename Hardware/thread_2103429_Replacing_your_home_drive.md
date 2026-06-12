---
title: "Replacing your /home drive"
date: 2013-01-10
forum: Hardware
---

### Post by j.daniel on 2013-01-10
**Hi,**

Just want to share this with you all since when I googled this, I found a lot of different advice on the 'net on how to move your /home partition to a different drive.

  I was running Ubuntu 10.04 on my old desktop-turned-file-server which this is all about.

  Google gave me a lot of different advice on the topic of changing the /home partition, ranging from the quite unhelpful "you should have thought on that when installing" and "don't do it", to more informative ones using everything from dd, tar, cpio, cp and rsync to clone the old /home partition.

 This is how I made it work. "Your mileage may vary" as they say - **remember that if you do not know what you are doing and make mistakes (especially when editing /etc/fstab) your system may become totally unusable, so I make no guarantees whatsoever that this will work for you**.
 
 Anyway: just giving the command lines is useless without the reasons why I chose the commands and flags I did, so here is some background:


**Background**
  To make a long story short, I happend to have two 1Tb drives in perfect condition (and one old LaCie external USB aluminium drive casing that looked like it had been hit by an RPG) and wanted to put them in my file server.

  Since my computer only had 4 SATA ports of which 3 were in use, I decided to replace the old 250Gb /home drive with one of these 1Tb monsters and fit the other one in the remaining, 4th slot.

  Further (just to make this even more fun), I have an nfs file server running and I have put the nfs root under /home and gathering the different drives and data using bind mounts (unfortunately required by nfs). (FYI: bind mounts are like 'super-hard links', the file system has basicly no idea that they are there. They are defined in /etc/fstab and cannot be removed once set up without a reboot).

  Also, my /home drive also had the swap partition on it, so both partitions needed to be replaced by the new drive.

  So these are the steps that I went through:


**1 Install drive**
I installed one of the 1Tb drives in the computer's 4th slot and used GParted to partition & format the new drive. I copied the size of the old swap partition and used the rest of the 1Tb drive for the new /home partition. The new partition has the label 'Idrive D 1Tb'. In gnome it auto-mounts as that under /media when clicking on the drive icon.


**2 Copy information**
For a lot of reasons, I chose rsync as my weapon of choise, but it is easy to get lost in the tons of flags that it has available. To summarize my concerns that had to be adressed in the cloning:

  - Regular file must be copied with the permissions and time stamps intact.

  - Symlinks should be preserved 'as is', i.e. they should not be translated or parsed in any way since the new drive will swap places with the old one.

  - Some applications use special files like sockets etc for communication (for instance dropbox use a few). These need not be copied as these applications will/should/ought to re-create them when they start up. These files can be recognized by the permission string beginning with odd characters like 's' when doing `ls -lh` (not to be confused with the "set uid" flag that can appear as one of the 'rwx' characters).

  - bind mounts should not be copied (since their data is somewhere else).

  - Since I'm the only user, I do not need to run it as root (no need to worry about different user ID:s).

  I did this several times while perfecting the flag setup in a small script (one of the reasons that rsync is better than a straight cp in this case), but in the end, the effective command line I issued was (should all go on one line if you want to try it):

```
> nice rsync
    --human-readable  
    --verbose         
    --progress        
    --perms           
    --times           
    --links           
    --acls            
    --xattrs          
    --recursive       
    --one-file-system 
    --exclude=/nfs_root/music --exclude=/.Trash-0  
    --delete          
    --delete-after    
    /home/ /media/Idrive\ D\ 1Tb/

```

  Lets walk through the flags, use `man rsync` and in there the search function (i.e. type `/--progress` to jump though the massive amounts of information) for specifics on each flag:

[I]  --human-readable
  --verbose
  --progress   [/I]: To see what's happening

[I]  --perms
  --times     [/I]: Preserve permissions and time stamps intact on regular files
  
*  --links:    *: To copy symlinks 'as is', i.e. no translation of the symlink path.
[I]
  --acls
  --xattrs    [/I]: Seemed to be a good idea, don't know if XFS use these.

*  --recursive  *: Copy everything, descend into directories

*  --one-file-system *: Do not jump to another filesystem when recursing (i.e. avoid that data in bind mounts to other drives are copied).

*  --exclude=/nfs_root/music *: This is a bind mount to another location on the same drive (my home folder), rsync has no way of detecting this, so excluding it was the only way I could figure out.
  
*  --exclude=/.Trash-0 *: Not accessable to normal users. It is not important either, so I skipped it to avoid rsync errors.

[I]  --delete
  --delete-after [/I]: Since I kept doing this over and over again, I wanted that files deleted in /home was also deleted on the new drive.
                 
  Now many rsync users would comment that a straight '--archive' could replace some of these flags (and add a few more), and yes - it can. However I wanted to explore the differences and I ignored some root only options like --owner, --group, --devices and --specials.

  If I had had a multi-user home drive, I would have gone with --archive instead and run it as root (sudo).

  The initial 'nice' command ensures that rsync does not hog the CPU while it is running.

  Then it was time for tea, a tv show and some general rolling of thumbs.

  Afterwards, I compared the used space between /home and "/media/Idrive D 1Tb" using
```
> df -h
```
  ...which matched - at least on the Gb level.


**3 Edit fstab**
Then it was time for some fstab magic. This is where you can trash your system so be careful. I actually don't know what happens if an invalid /home is specified - perhaps it boots anyway? I managed at first to forget that the swap partition had changed as well and that did not prevent booting at least.

  I started by listing the UUIDs of all drives by issuing
```
> sudo blkid
```
     
  Noting the UUIDs of the new /home and swap partitons, I made a backup of the old fstab before firing up gedit:
```
> sudo cp -i /etc/fstab /etc/fstab_backup
> gksudo gedit /etc/fstab
```
  
  FYI: My fstab have all drives identified by their UUID like this:
```
UUID=e9bbc6ec-937f-2faa-9ffa-25c4a504462e /home xfs defaults 0 2
```
  
  I commented out the old /home and swap lines by adding a '#' in the beginning of these lines - I usually like to keep the old ones as a reference until the new setup is up and running.
  
  Then I copied the /home and swap lines (without the inital '#') and replaced the UUIDs with the new home and swap partition UUIDs. Since both the old and new drive use the XFS file system, I only needed to swap the UUIDs - otherwise the file system needs to be changed as well of course.
  
  I also added a new line for the old /home drive under /media/OldHome (with 0 2 as the last two digits).


**4 Restart**
Saved, exited, shut down, pulled out the data cable of the old /home drive (just to be sure that it is not in use) and fired it up again. It complained that OldHome could not be mounted, but that was expected (pulled the cable - remember?). Everything worked like a charm!... at least after I remembered to change the swap partition as well... ahem. :oops:
     

**5 Celebrate**
Patted myself on the back for being such a badass linux hacker ;)


Anyway; I hope this can help someone out there! Good luck.

Cheers!
/ Daniel

---

