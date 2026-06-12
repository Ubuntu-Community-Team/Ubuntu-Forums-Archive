---
title: "RAID 10 failure, how to recover data?"
date: 2012-10-18
forum: Hardware
---

### Post by mowgliee on 2012-10-18
ubuntu 10.04 server on ibm 366 xseries w/ raid 10 using adaptec hardware raid card over array of 4 total drives (ea 70GB).  drive 0 & 1 mirroring pair 1, drive 2 & 3 mirroring pair 2.  pair 1 striping pair 2 (so appears as 1 140GB drive).  one morning I/O error so rebooted server & raid reported missing or bad raid member & wouldnt boot.

tried r-tt.com r-studio & other recovery apps but preserved drive order & data always.  r-studio does recognize all 4 drives as 1 140GB drive so i cant/dont need to use virtual raid feature.  (using 2 of the striped drives appears as 1 140GB drive too.)  see lots of files & data but loses filenames & directory structure so unusable recovery.

did not initialize drives in raid config, but did try to remove raid 10 to mount drives on alternate identical spare server.  no luck but fear slight data loss as result.  cant mount drives elsewhere b/c mount cant recognize ddf_raid_member. fdisk = partition table missing.

server is zimbra mailserver.  last backup 3 weeks old (yes dumb i know).  server has nightly backup on it, so i'm happy if i can recover that 1 11GB bz2 file or the entire /opt/zimbra dir (dir preferred).  need nothing else on it.

i can make all 4 drives remotely available via ubuntu live CD & ssh, but they ea appear only as /dev/sdX (X = a-d).

adaptec raid does store raid info on card & on drives.

would this help? [http://www.unixwiz.net/techtips/recovering-failed-raid.html](http://www.unixwiz.net/techtips/recovering-failed-raid.html)

or would testdisk?

heard about raw data recovery but not sure if thats the right path to follow.

thanx!

---

### Post by darkod on 2012-10-18
First of all, do you know if we are talking about only one failed disk? With one failed disk a RAID10 should keep on going regardless which disk it is.

Why don't you simply replace it with a good disk?

When you are trying the ubuntu livecd, what if you try to activate dmraid first with:
sudo dmraid -ay

Does it show the raid device after that?

This is the problem with hardware raid and why more and more people seem to go with software raid and mdadm. You can connect the disks on any linux machine and assemble the array. Even without a faulty disk.

PS. The thread might have been better in the Server section, not Hardware.

---

### Post by mowgliee on 2012-10-18
good pt on sw raid.  will def consider for future.

i suspect its > 1 failed disk.  otherwise it would have still booted & worked & i could have swapped the bad disk.  it wouldnt even boot.  i changed it to a raid volume vs raid 10 (just to see if i can access or mount drives - probably dumb move), couldnt mount so i changed it back to raid 10 & now system accepts the drives but doesnt boot (my nifty work probably messed up the boot sector or partition table).  the raid card works fine w/ other drives now (tested) & these drives report no errors on boot w/ an identical raid card (or even the same old one).  so i have no clue what really failed.

dmraid -ay results in:

ddf1: virtual drives with CRC 69EAD957, expected E7BAA5F0 on /dev/sda
ddf1: physical drives with CRC 274162EB, expected 475E378E on /dev/sda

then it activates it.  which just makes a device appear in /dev/mapper but i cant mount it.  same errors as trying to mount /dev/sda.

can i move the thread to server section somehow?

---

### Post by NadirPoint on 2012-10-18
> **mowgliee said:**
> i suspect its > 1 failed disk.
I don't understand this statement.  Booting into the Adaptec raid setup/mgt utility tells you exactly which drives are affected.

---

### Post by mowgliee on 2012-10-18
thats the prob.  it didnt.  it just said missing or failed members but when i go into the raid config, all 4 drives there & look fine.  no missing anything!  of course now the drives dont boot, so i cant actually use them.

& after my raid 10 -> volume -> raid 10 attempt (yes i know dumb) i dont even get the missing member error.  everything looks happy except i cant boot.  i know there is tons of data on the drives though (courtesy of r-studio) but cant get access.

---

### Post by NadirPoint on 2012-10-18
Are they connected at the same physical locations as before you had them out troubleshooting?  Occasionally the raid bios will see an anomaly causing it to errantly fail a drive.  You may actually not have a problem at all if you get them properly re-connected.

---

### Post by mowgliee on 2012-10-18
yeah that was my pipe dream too.  but nope/wont boot.  the anomaly explanation does seem to fit what happened though since it accepts all the drives now (but doesnt boot OS).

yes i kept all 4 drives in same order, same slots.  made sure of it.  0-3.

---

### Post by NadirPoint on 2012-10-18
Not knowing exactly which adapter/bios you are looking at - is there a "rebuild array" option available?  If you are sure they are installed correctly that might do it, but also a risk of destroying any data that may still be available otherwise.

---

### Post by mowgliee on 2012-10-18
its adaptec raid; i can get exact data if u want, but there isnt a rebuild.  there is rescan drives which i have done.  no luck.  & initialize drives which i am scared to do for fear of data loss.  i tested it on another raid 10 array & it behaved oddly.  so prob not good idea.

again the raid bios part does go through fine w/o errors now, same 4 drives in same order as raid 10.  just wont boot.

---

### Post by mowgliee on 2012-10-18
hmm i am trying to do the solution in the link above using scandrive.cpp

i tried to compile using g++ but got this error

In file included from scandrive.cpp:114:0:
/usr/include/linux/ext2_fs.h: In function ‘__u32 ext2_mask_flags(umode_t, __u32)’:
/usr/include/linux/ext2_fs.h:180:18: error: ‘S_ISDIR’ was not declared in this scope
/usr/include/linux/ext2_fs.h:182:23: error: ‘S_ISREG’ was not declared in this scope

any advise on what to do? *using ubuntu 12.04

---

### Post by NadirPoint on 2012-10-18
Don't do initialize.  Does the bios report a drive installed after post, then fail to boot?

---

### Post by mowgliee on 2012-10-18
def wont initialize.

yes bios reports 4 drives installed.

any tips on how to get that scandrive to compile?

---

### Post by NadirPoint on 2012-10-18
It should report 1 drive installed if those 4 are supposed to comprise the raid10 you described.

It seems you have lost the raid configuration.  If you have the raid config backed up you could try restoring that to the adapter.  Or you try to manually re-establish the raid config without initializing it.  Not sure about the process to go about that or if it would be non-destructive.

---

### Post by mowgliee on 2012-10-18
i meant the raid sees it as 1 drive.  but i can go into the config & see that its raid 10 across 4 drives.  thats what i meant.  not that its appearing as 4 drives to the bios.

i did exactly what u said to achieve this, recreate the raid array.  & i do fear some data loss as a result.

not sure what to do now.

but do you have any advise on how to compile that scandrive.cpp? i used g++ & it fails w/ the above errors.

---

### Post by darkod on 2012-10-18
If the /dev/mapper device showed, I would also try what testdisk sees. Usually you do it on physical disks, so you select to work with /dev/sda, /dev/sdb, etc. Not sure if you can select /dev/mapper/ or if it will see it at all.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can do all that from live mode. Not sure if you need to activate the array with dmraid every time you boot live mode since the previous change is lost when you shutdown live mode.

In case testdisk can scan it, I suggest first only scanning, the standard quick search, and the deeper search. Note down the partition detected if any.

You can then do the math what to recover and what not because testdisk might find some older partitions that you deleted on purpose with the deeper scan.

---

### Post by NadirPoint on 2012-10-18
> **darkod said:**
> You can do all that from live mode.
That's what I was going to say - boot a live CD and see if you can access it.

---

### Post by mowgliee on 2012-10-18
yes i am doing it w/ a live cd.  i see sda thru sdd.  no sda1 b/c no partition tables i guess.  so cant mount.

running testdisk on sda but it says it expects a 240GB drive when its only 68GB (perhaps due to raid?).  anyway doesnt find any partitions so i chose the partitions: none option & redid search & deeper search.  it finds files galore.  but says due to the drive size error above it thinks the file are corrupt & wont let me copy them.

at the very beginning of either search it says 

Bad root_cluster
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD)
Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD)

so now what?

honestly i just want to get the /opt/zimbra dir or the bz2 backup file back.  i dont need to resurrect the drive (though that would be easiest outcome for me).  the bz2 is ~ 11GB & its a backup of that dir i want.

---

### Post by mowgliee on 2012-10-18
should i try to run testdisk while both drives of a stiped pair (from the original raid 10) or all 4 drives are in the system booted from live cd?  i am just doing it with 1 drive right now.  just to learn i thought this would be easier but perhaps its wrong to do due to the raid 10?

is photorec something i should consider?

---

### Post by mowgliee on 2012-10-18
results of deeper search:

Disk /dev/sda - 73 GB / 68 GiB - CHS 8925 255 63

The harddisk (73 GB / 68 GiB) seems too small! (< 245 GB / 229 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  ext4                     0 233 40 17713  71 20  284549120 [webmail]
   ext4                     0 233 42 17713  71 22  284549120 [webmail]
   ext4                  1763  58 22 19475 151  2  284549120 [webmail]
   ext4                  1763  58 24 19475 151  4  284549120 [webmail]
   ext4                  2350 169 58 20063   7 38  284549120 [webmail]
   ext4                  2350 169 60 20063   7 40  284549120 [webmail]
   ext4                  2546 122  7 20258 214 50  284549120 [webmail]
   ext4                  2546 122  9 20258 214 52  284549120 [webmail]
   ext4                  2611 191 11 20324  28 54  284549120 [webmail]
   ext4                  2611 191 13 20324  28 56  284549120 [webmail]

[ Continue ]
EXT4 Large file Sparse superblock Backup superblock, 145 GB / 135 GiB

so it doesnt list my bz2 partition (which i did see it find on the previous screen - its called [backups].  hopeful?

---

### Post by darkod on 2012-10-18
I was talking about running it to the whole raid10 array, the /dev/mapper/... device. That is your raid device, that's what you need to work with.

I don't think it can successfully read it from a single disk especially since the array was raid10, not raid1. The 0 means data is split between two devices. You can't recover anything from one disk.

---

### Post by NadirPoint on 2012-10-18
What is the exact message returned when the array fails to boot?  As darkod says, you need to be looking at a dev/mapper device.  You could try running an install and see what the installer thinks about loading that device.  Don't actually complete the install, just see if Ubuntu is going to recognize it as the correctly sized device.

Seems your boot record also went the way of whatever happened to the raid config.  Just install grub?

---

### Post by mowgliee on 2012-10-18
ahhhh ok i get it now.  good makes sense.

how about if i ddrescue to make copies of the 4 drives.  then i do testdisk on the array to try to recover files or resurrect the raid10 drive?  or do i have to use the original 4 drives?

---

### Post by mowgliee on 2012-10-18
nadirpoint, what do u mean by just install grub?  how do i install grub to the array w/o damaging any data?  sorry for noob question on this but i dont understand what you meant by installing grub.

i would definitely like to recover the boot sector if that will recover the drives.

---

### Post by darkod on 2012-10-18
If you are prepared to wait to dd four disks (it will not be fast), you can try. That way you can "play" with the copies, not the originals.

But I don't think testdisk can harm them. First of all, when you open testdisk and it asks you to select a device (disk), you will see immediately if it offers /dev/mapper... as a choice or not. Don't forget to activate it first if needed.

---

### Post by NadirPoint on 2012-10-18
I would install grub on the correct sized, not needing "resurrected" mapper.  If it lets you.

Apparently the only thing wrong with it now is it won't boot.

---

### Post by Cheesemill on 2012-10-18
I think the easiest solution now is just to recreate a new array and restore the data from your most recent backup.

---

### Post by mowgliee on 2012-10-18
nadirpoint, how do you install grub on a mapped device?  i assume dmraid -ay will get the mapper to appear & be correct size.

cheesemill, last back i can locate is 3 weeks old.  yes i know what lunacy on my part.  i have hunting day/night for the real backups but cant find.

darkod, should i testdisk on the mapper using 2 of the striped disks or all 4?  in raid10 the right 2 will get me a full drive.  but if i some of the data is corrupt in 1 pair, using 4 is wiser?  not sure if my understandings are correct about that.

---

### Post by NadirPoint on 2012-10-18
> **mowgliee said:**
> nadirpoint, how do you install grub on a mapped device?s
I can't remember what the install options on 10.04 looked like.

If you boot the install CD you will be presented with a rescue or recovery option that then loads the adaptec driver and allows you the choice to re-install grub at some point.

It can also be done from a root shell with the grub command, again, not remembering the actual syntax without looking it up.

---

### Post by NadirPoint on 2012-10-18
> **Cheesemill said:**
> I think the easiest solution now is just to recreate a new array and restore the data from your most recent backup.
He already re-created the OLD array, so what's that buy him except a total lack of data?  It would still leave him without a viable boot record and exactly where he's at now.  Minus the data.  Are you suggesting he re-install the OS, re-install and re-configure all the applications and THEN restore the data?

Not seeing the easy part there.  :confused:

---

### Post by mowgliee on 2012-10-18
i welcome all ideas/suggestions, even non easy ones.  but as nadirpoint said, i already have a raid10 array that works w/ the original drives but the bad boot sector or partition table renders it unusable.  & i cant reinstall from backup b/c only backup i can find is 3 wks old.

nadirpoint, i didnt know u could install grub (or anything) onto the mapper from the root shell of a live cd.  is that what you are saying i can do?  if so i'll google that.

what do you guys think about the idea in the original link i posted, finding out what the offset for the partitions are & just dd'ing the sectors outside of the offset to a new disc?  the offset would be to get rid of the raid housekeeping portion of the drive so that i can mount it like a regular drive.  i dont know if i would try this w/ 2 of the drives or 4 (would dd the resultant mapper in either case).

---

### Post by darkod on 2012-10-18
Did you try what testdisk says about /dev/mapper/..? Does it show it as device to work with?

The /dev/mapper/ is the whole raid10 device consisting of 4 disks. And that's what I would try in testdisk. The point is to recover the partition table of the whole device, right.

Installing the bootloader later is piece of cake, the problem is recovering the disks into a working state. Even without a bootloader you can copy the data from them then. But now you can't.

---

### Post by mowgliee on 2012-10-18
about to burn knoppix boot cd now.  then will run w/ testdisk as you detailed.  fingers crossed!  will know in few minutes.

(been using ubuntu live cd & its annoying have to apt-get all the pkgs i want on reboot; whereas, knoppix has it all by default, even the superior ddrescue vs dd-rescue).

---

### Post by NadirPoint on 2012-10-18
I think you might be on a good track, assuming knoppix has the right Adaptec driver.  Which Ubuntu install disk were you using?

---

### Post by mowgliee on 2012-10-18
ubuntu 12.04 desktop ed 32 bit.

ok knoppix ready.  here we go!  act 4 ... hopefully the finale w/ a happier ending.

---

### Post by NadirPoint on 2012-10-18
> **mowgliee said:**
> ubuntu 12.04 desktop ed 32 bit.
It is unlikely that CD-ROM has the 366/Adaptec driver.  I thought it was a 10.04 server?

---

### Post by mowgliee on 2012-10-18
the original server is a 10.04.  the live cd is 12.04.  why would it need an adaptec driver?  cd isnt trying to do raid, just access the drives somehow, circumventing raid i thought.  obviously i am not understanding something.  pls explain.

---

### Post by darkod on 2012-10-18
I'm not sure whether it has a driver or not, but of course it needs to see the raid. The hardware card makes the raid but without a driver it can't be understood by the OS. And you need the OS to see the whole array, otherwise it's pointless talking about reading data or recovering partitions.

If they are shown only as single disks, there is no way to get data out of a raid10 array if I'm not mistaken. From raid1 you could try because it's simple mirror, but raid10 is mirror with stripe on top of it, so the striping makes the data divided between at least two disks.

So, reading only one disk, in any way possible, is worthless. That's why the linux distro needs to see the raid fully. Usually if the mapper device is correct size, it means it does see it, and you said you can see the mapper device after using the dmraid activation.

---

### Post by mowgliee on 2012-10-18
i did dmraid -ay on the spare server w/o any raid card installed.  yup, without.  thats when it appeared as 1 device in the mapper.  i've never installed any drivers for adaptec, not even when the original array was working.  why would one?  the hw raid does its thing before the OS even boots doesnt it?  the OS sees it all as 1 device courtesy of the hw raid; the OS doesnt actually manage or instruct the hw raid card, does it?  (sorry for the non tech noob lingo.)

i thought whole point of dmraid was to make drives behave/combine as though they were 1, like in the original raid config, but it doesnt actually use the hw raid card, does it?  dmraid is sw raid, right?

---

### Post by darkod on 2012-10-18
mdadm is sw raid. dmraid is hw raid and fakeraid, as far as I know.

I am also fuzzy on the details but I always thought that dmraid serves as a driver for the hardware raid card. It's true that in real hw raid the card does all the work, but as we all know, without a driver any hardware is useless. Only with windows we are not used to that much, especially with win7 and windows server 2008 that have many drivers already integrated, so it looks like the hw card is doing the job and the OS only sees the array as single disk.

Actually during installing one server 2008 R2 recently it didn't have the driver for one quite old raid card, and didn't see any disks until I managed to find the driver and add it during OS installation.

Sorry, for a bit off topic. It's also very late in my time zone so I'm signing off. I hope you manage to get closer to your data.

PS. In any case, I wouldn't say dmraid assembles the array avoiding the hw card. That wouldn't work, the array needs to be controlled by the same identical controller, not the dmraid in its place. I understand dmraid only as the package in linux talking to the hw cards. I might be wrong though.

---

### Post by mowgliee on 2012-10-18
not sure if you will read this in time, but on ubuntu 12.04 live cd dmraid -ay did assemble the drives into 1 mapper device!

i tried it w/ 4 drives & it said too many drives 4/2 which makes sense since it sees it as 1 raid0 pair so doesnt understand why 4 drives exist.  anyway i will now testdisk on 1 pair.  see what happens.

you have helped me learn/understand a GREAT deal!  so no apologies, keep the comments coming from any corner/angle/subject.  this sponge awaits.  will report results.

---

### Post by NadirPoint on 2012-10-18
The reason you never installed any driver before is because the installer did it for you automagically.   That is why I earlier suggested following the original install/ rescue path (with the 10.04 server CD).

---

### Post by mowgliee on 2012-10-18
nadirpoint, never used a 10.04 cd, used 12.04 & i guess it does install driver b/c dmraid works.  testdisk however has failed to find partition or files it can recover thus far.

mscatopats, i dont need to reuse anything.  i just want the data.

---

### Post by mowgliee on 2012-10-18
btw testdisk says this is the geometry of the mapper device:

Disk /dev/mapper/ddf1_saturn - 73 GB / 68 GiB - CHS 143155200 1 1

can that be right?  1 1?  not 255 63?

---

