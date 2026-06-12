---
title: "Cloned WinXP hard disk freezes on login."
date: 2009-01-09
forum: Hardware
---

### Post by DigiTan on 2009-01-09
Backstory:

This is my first-ever time running Linux.  I have my stuff on a small hard disk (**sda**) all on one partition.  I want to clone it all over to a larger disk (**sdb**) and then install Ubuntu permanently onto the old one.

I have the live recovery CD and a friend talked me through most of the process.  So it went pretty well until I tried to boot WinXP off the clone by itself.  Now windows just sits there frozen right before you get to login.
--------------------------

Before anybody gets antsy, I already read [the thread here](http://ubuntuforums.org/showthread.php?t=719913&highlight=ntfsclone+xp) but my situation's a little different to where I want to verify some stuff before I continue.  This was my process...

1.  **Installed the new drive and booted Live CD**.  Before doing anything, I found the terminal and verified the names of the drives with a quick peek at gparted.

2.  **Saved the old MBR.**
[COLOR="Red"]sudo dd if=/dev/sda of=./drive.mbr bs=512 count=1[/COLOR]

3.  **Saved partition table**
[COLOR="Red"]sudo sfdisk -d /dev/sda > partition.table[/COLOR]

4.  **Wrote the MBR to the new disk.**
[COLOR="Red"]sudo dd if=./drive.mbr of=/dev/sdb[/COLOR]

5.  **Edited partitions table with nano.**  Basically I just swapped all the "sda"s with "sdb"s.  Saved.  Exited.

6.  **Wrote the partitions table to the new disk**
[COLOR="Red"]sudo sfdisk /dev/sdb < partition.table[/COLOR]

7.  **Cloned with ntfsclone**.  I checked with fdisk before doing this too look for anything that seemed "not right."
[COLOR="Red"]sudo ntfsclone --overwrite /dev/sda1 /dev/sdb1[/COLOR]
...you really gotta hand it to these guys for switching the syntax on such a risky command.  I almost didn't find out in time.

8.  **Edited partition data using fdisk.**
[COLOR="Red"]sudo fdisk /dev/sdb[/COLOR]
[COLOR="Red"]p[/COLOR] (Just to read and jot down everything first)
[COLOR="Red"]d[/COLOR] (To delete the partition.)
[COLOR="Red"]n[/COLOR] (To create new partition.  I made it the primary part and set the start/end to span all available space)
[COLOR="Red"]t[/COLOR] (Changed type to NTFS)
[COLOR="Red"]a[/COLOR] (To make it a bootable partition)
[COLOR="Red"]w[/COLOR] (Saved and exited)

9.  **Resized with ntfsresize**.  I just typed...
[COLOR="Red"]sudo ntfsresize /dev/sdb1[/COLOR]
...and it took just a couple seconds to finish.  Exited terminal and shut down.

10.  **Plugged the new drive into the old one's SATA cord.**  And I left the old one unplugged.  When I booted and got to WinXP, it showed the light blue screen and did a disk error check and said all was well before it rebooted.

11.  **Watched WinXP freeze** just before you get to see the login screen.  The cursor can move but that's about it.  I mean, I don't get it.  I thought ntfsclone was supposed to...you know...*clone* things.  How the heck can windows tell the difference?!?  I also ran the WinXP Recovery CD's **fixboot **utility and it had no effect.

----------------------------------
Where I am now:
I'm going to try the [method shown here](http://www.tech-archive.net/Archive/WinXP/microsoft.public.windowsxp.general/2006-12/msg11236.html) Friday to re-write the partition's NT boot sector but it seems overblown.  ...Like I'm just doing ntfsresizes' job.  I was my impression my 12th step would involve watching windows auto-detect, editing boot.ini, and if I'm lucky drinking an ice cold (root)beer.

Why is my WinXP locked up like the rusty tin man?  Maybe I was supposed to [COLOR="Red"]unmount [/COLOR]or [COLOR="Red"]chown [/COLOR]this drive like [perixx](http://ubuntuforums.org/showthread.php?t=719913&highlight=ntfsclone+xp) did?  Or do I have to edit the NT boot sector too?  Thanks.

---

### Post by DigiTan on 2009-01-11
Whoa, guys!  One answer at a time!  One at a time!

I'm gonna take a second try at the this, but the more I keep guessing around like this, the more likely I am to accidentally damaging the disk that actually works.  C'mon people, I can't be the only guy here to clone a WinXP disk.

---

### Post by jocko on 2009-01-11
I've never tried to clone an xp install, but from what I can see you are doing things more complicated than they really are. You'll probably need a windows install cd (with recovery console) and a linux live cd (or just run linux from the old hd).
From [this post]("http://ubuntuforums.org/showpost.php?p=4490352&postcount=2")[COLOR=Teal][COLOR=Red](with my comments in red)[/COLOR][/COLOR]**[COLOR=Teal]Preparations:[/COLOR]**

[COLOR=Orange]**1)**[/COLOR] You'll need to install the following packages, if you don't already have them:
- ntfsprogs (includes ntfsclone)
- ntfs-3g
- hexedit (simplified: needed, when cloning XP to partitions to others than the first, primary one)[COLOR=Red] <-- You don't need this[/COLOR]
    ```
sudo apt-get install ntfsprogs ntfs-3g [COLOR=Red]hexedit [/COLOR]

```[COLOR=Orange]**2)**[/COLOR] The TARGET partition was built with Gparted first, a little larger than the actual XP partition. [COLOR=Red]<-- You probably don't need to format this partition, just create a partition without formatting should be enough, if it's possible. Leave the rest of the drive empty for now.
[/COLOR]
[COLOR=DarkOrange]**3)**[/COLOR] Created a backup of the TARGET bootsector/MBR in a file on /media/sda5 for recovery purposes first, with [COLOR=Red]<-- Don't see why this is necessary, as nothing you do here should mess with the boot sector, but it may be good to have a backup in case you mess things up... [/COLOR]
     ```
sudo dd if=/dev/sda1 of=/media/sda5/original_sda.mbr bs=446 count=1 
```[COLOR=Orange]**4)**[/COLOR] Both TARGET and SOURCE need to be unmounted prior to the procedure, with:```
sudo umount /dev/[TARGET]
sudo umount /dev/[SOURCE]
```[COLOR=Orange]**5)**[/COLOR] the TARGET partition needs to be 'owned' before beginning: [COLOR=Red]<-- As you run ntfsclone with sudo, I don't see why you (USER) would need to own it. Try without it.[/COLOR]
     ```
sudo chown USER /dev/sda1 

```**[COLOR=Blue]Procedure:[/COLOR]**

[COLOR=DarkOrange]**1)**[/COLOR] the actual, DIRECT cloning command (no image file used):
     ```
sudo ntfsclone --overwrite /dev/sda1 /dev/hda1
``` This is done in TARGET-SOURCE format, unlike many other commands, be careful not to mix that up!!

[COLOR=Orange]**2)**[/COLOR] Changing ownership back to 'root': [COLOR=Red]<-- If step 1 worked without changing ownership, don't do this. This would only affect the running linux session, and seems rather pointless.[/COLOR]
     ```
sudo chown root /dev/sda1 
```[COLOR=Red]At this point I think you should probably turn off the computer and unplug the old drive before you continue (if both new and old drives are of the same type [IDE or SATA], move the new drive to where the old one was connected).
Also go into the bios settings and make sure the boot order is set to boot from CD first, then the new hard drive (so if the old drive was IDE and the new one is SATA, make sure the bios is set to boot from the SATA controller).[/COLOR]

[COLOR=Orange]**3)**[/COLOR] Rebooting into the XP installation-CD's recovery console (log into the appropriate Windows partition and do:
     ```
chkdsk d: /p
exit 
```[COLOR=Red]Try to boot from the hard drive. If it doesn't  boot at all (you get an "invalid system disk" error from bios), you may need to restore the mbr (run "fixmbr" from a windows recovery console).
If you manage to boot windows, clean the drive (remove temporary files and such) and defragment it as completely as possible (run it several times until the defragmenter doesn't seem to do much), then you can boot a linux live cd and resize the partition to whatever size you want using gparted (you'll probably need to make sure ntfsprogs and ntfs-3g is installed to get gparted to work with ntfs)[/COLOR][COLOR=Red]. It may be necessary to repeat step 3 above after this.
If it works, plug in the old drive again, and re-format it as you like.[/COLOR]

---

### Post by DigiTan on 2009-01-11
Well, even though that's the same thread my link went to, it's good to have a second opinion.  (And the commentary should help too).  Should I try erasing the cloned stuff off my disk before I try again, or would that not make a difference?

---

### Post by DigiTan on 2009-01-12
Okay, I'm going to try this after I've researched the commands a little more.  But something seems to be missing here.  In his topic, perixx never mentioned mounting either drive back after the copy was done.  I looked it up on die.com but I'm still not clear whether that should've been remounted.

---

### Post by DigiTan on 2009-01-14
I tried installing hexedit and it appears I had it all along.  But when I try to use it, I got an error saying I had to enable 'Universal.'  Or something to that effect.  I had just enough time to read that much before my system crashed.  (I'll edit in the full response when I get the chance)

But what's this business about enabling hexedit?  Any idea of what this is telling me?

---

### Post by jocko on 2009-01-14
> **DigiTan said:**
> I tried installing hexedit and it appears I had it all along.  But when I try to use it, I got an error saying I had to enable 'Universal.'  Or something to that effect.  I had just enough time to read that much before my system crashed.  (I'll edit in the full response when I get the chance)

But what's this business about enabling hexedit?  Any idea of what this is telling me?

No idea... And why would you need hexedit? 
As I understand it, that's only if you manually need to edit your boot sector, but I don't see why you would need that.
You just want to copy the first partition of your old drive to the first partition of your new drive, right? I'm pretty sure that doesn't require any advanced editing of your boot sector. In the worst case your drive will not be bootable after you copied the partition to it, but in that case I'm pretty sure it will be fine if you just run "fixmbr" from a windows install cd (or a [Super Grub Disk]("http://www.supergrubdisk.org/")).

As you manage to get to the windows login, I am sure there is nothing wrong with your boot sector and almost sure the file system is fine, as it should be an exact copy of your original file system.
Before you tried to start windows, did you unplug the old drive and moved the new one to the connection where the old one was connected?
Windows can be very picky about changes in the hardware, so if too much is changed it may not boot all the way.
There may be some registry tweaks or other things that you may have to do in your original windows install before you clone it to minimize the risk of running into problems ([see step 3 on this page]("http://www.dominok.net/en/it/en.it.clonexp.html")).

---

### Post by DigiTan on 2009-02-15
Okay I can't quite say my original question was solved, but I got it working just now.


First thing, I undid everything mentioned before and started from scratch.  I took my original SATA disks, plus two more disks that were much larger.

As a backup, I used a straight **sudo dd if=/dev/sda of=/dev/sdb** from the original disk to the extra disks.  As you might guess this took hours, but when it was over I had 2 backups in case of a catastrophic mistake.

I booted off all 3 disks one by one to see if WinXP could still access them.  They all worked.  With that confirmed, I physically mounted the largest disk (the one I want Windows on) and booted into Linux.  I used fdisk to change the partition from 40GB to 250GB--the full size of the disk.

sudo fdisk
[LIST]
[*]p (see disk statistics)
[*]d (delete partition)
[*]n (new partition)
[*]p (for "primary")
[*]1 (for "partition 1")
[*]I set the starting and ending points
[*]t (change partition tyle)
[*]7 (for NTFS filesystem)
[*]a (to make the disk bootable)
[*]w (to save changes)
[/LIST]

Then I verified that all 250GB was partitioned up in GParted.

Next, I tried using ntfsresize to properly size the data to the full 250GB of space.  This didn't work for reasons I don't understand yet, because its response said everything had already sized been correctly.  Which I knew wasn't true.  I even **umount**ed the drive, but got the same response.  So I just ran **ntfsfix** so WinXP would be forced to run a CheckDisk on the next boot.  Rebooted.

I booted into windows and let CheckDisk run.  After another boot, I was able to access WinXP and it did not crash.  But My Computer still thought I had only 40GB of space.  So I booted back into Linux.

This time, I ntfsresize **did** work.  And it only took a few seconds to properly size up the data.  Once again I booted Windows and let it run CheckDisk.

This time, My Computer says I have the full 250GB and WinXP is 100% stable.


...So basically I call this "partially solved."  Unfortunately, because I use **dd** instead of **ntfsclone**, my method lacks in speed.  Maybe on a later date I'll try the more efficient way.  But for now, I'm just happy to have free space.

---

