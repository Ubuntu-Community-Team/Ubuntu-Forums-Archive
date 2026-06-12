---
title: "Rebooted, lost USB Drive"
date: 2015-04-12
forum: Hardware
---

### Post by feartheterrapin on 2015-04-12
I have a 2 TB Western Digital USB3 drive (not bootable, FAT 32) I use for Ubuntu 12.04  back ups.  I had the drive mounted backing up files, rebooted and suddenly I see no files.  However, the available free space on the drive seems to be unchanged, 1.3TB.  So I assume my data is still on the disk.   Is it possible that only the file allocation table is messed up.  

Running TestDisk I get the following results:
 ```
TestDisk 6.13, Data Recovery Utility, November 2011 

 Christophe GRENIER <grenier@cgsecurity.org> 

 http://www.cgsecurity.org 
  
 Disk /dev/sdd - 2000 GB / 1862 GiB - CHS 243198 255 63 
  
 The harddisk (2000 GB / 1862 GiB) seems too small! (< 4719 GB / 4395 GiB) 
 Check the harddisk size: HD jumpers settings, BIOS detection... 
  
 The following partition can't be recovered: 
      Partition               Start        End    Size in sectors 
 >  FAT16 <32M           405651 229 42 573757 164 10 2700618764 
   
 [ Continue ] 
 1382 GB / 1287 GiB 

``` 

 I am able to list files with TestDisk, but the names listed are random characters.
 
I ran  dosfsck and got the following:
 ```
$ sudo dosfsck -t -a /dev/sdd1 
 
 dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN 
 There are differences between boot sector and its backup. 
 Differences: (offset:original/backup) 
   65:01/00 
   Not automatically fixing this. 
 FATs differ but appear to be intact. Using first FAT. 
 / 
   Cluster 0 (2) is unreadable. Skipping it. 
 / 
   Start cluster beyond limit (18446744073709551615 > 122032956). Truncating file. 
 Bad FAT32 root directory! (bad start cluster) 
```
 
 I have also attached a screenshot shot from UFS files Explorer and from running TestDisk. 

[ATTACH=CONFIG]261241[/ATTACH]

  I am not sure how to proceed.  I see the following options:
   
[LIST=1]
[*]UFS File Explorer?  The only     option I see is to recover files. 
[*]TestDisk.  But not sure what to     do.  Do I now write? 
[/LIST]
 
Any suggestions are appreciated.

---

### Post by user_of_gnomes on 2015-04-12
I'd clone the drive with DD to have a back-up ready and then run Windows checkdisk on it, see if that can fix it. I assume you made it FAT32 to keep it compatible with a Windows computer.

---

### Post by Keith_Helms on 2015-04-12
> **feartheterrapin said:**
>  I had the drive mounted backing up files, rebooted and suddenly I see no files. 

Were you actually in the process of backing up files when you rebooted?  It sounds like your FAT32 drive has been corrupted.  You can try to recover it as described here:

[http://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system](http://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system)

---

### Post by feartheterrapin on 2015-04-12
> **Keith_Helms said:**
> Were you actually in the process of backing up files when you rebooted?  It sounds like your FAT32 drive has been corrupted.  You can try to recover it as described here:

[http://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system](http://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system)

I did follow those instructions.  I posted my results in my original post.  I am not sure how to proceed.

> **user_of_gnomes said:**
> I'd clone the drive with DD to have a back-up ready and then run Windows checkdisk on it, see if that can fix it. I assume you made it FAT32 to keep it compatible with a Windows computer.

Not sure why I started with FAT 32.  I no longer have a windows computer (just Win7 via VirtualBox).  ReDo is my primary image backup tool and FreeFileSync is my primary file back up tool.  I was booted in Ubuntu, backed up my Firefox profile to the USB drive, rebooted to ReDo, ReDo did not see my back up location, rebooted to Ubuntu with the same results.

---

### Post by user_of_gnomes on 2015-04-13
[Before proceeding you should clone your hard drive using DD]("https://wiki.archlinux.org/index.php/Disk_cloning") as a precuation. It doesn't care about whether or not it can read files, it just copies bits.

After that we can attempt to repair the file system but I suspect that we'll have to use Photorec to get your data out ..

---

### Post by feartheterrapin on 2015-04-13
> **user_of_gnomes said:**
> [Before proceeding you should clone your hard drive using DD]("https://wiki.archlinux.org/index.php/Disk_cloning") as a precuation. It doesn't care about whether or not it can read files, it just copies bits.
After that we can attempt to repair the file system but I suspect that we'll have to use Photorec to get your data out ..

I did not have a spare 2TB drive, but did order one last night.  Should arrive tomorrow.

Spare drive to arrive today?  Attached are some screen shots of UFS File Explorer results.  Not sure if this helps.

Also, I noticed in the Disk Utility of Ubuntu 10.04 there is a scan and fix disk option.  Is this a possible solution?

---

### Post by dino99 on 2015-04-14
gparted can check and rebuilt the table if necessary
syslog might help to know what have happened

---

### Post by user_of_gnomes on 2015-04-14
> **feartheterrapin said:**
> Spare drive to arrive today?  Attached are some screen shots of UFS File Explorer results.  Not sure if this helps.

Also, I noticed in the Disk Utility of Ubuntu 10.04 there is a scan and fix disk option.  Is this a possible solution?

I have never seen UFS explorer before.

Did you manage to clone your hard drive?

If file recovery is important to you, you should consider taking the hard drive out of the usb-casing and hooking it up directly to the mainboard. That way we'll also be able to see the S.M.A.R.T-status of your hard drive which I am rather curious about ...

---

### Post by feartheterrapin on 2015-04-14
> **9d9 said:**
> gparted can check and rebuilt the table if necessary
syslog might help to know what have happened

I looked at the syslog at the time I shut-down Ubuntu and got the following:

```
Apr 12 10:19:58 UB64 kernel: [    4.945066] ..............ready
Apr 12 10:19:58 UB64 kernel: [   18.115950] sd 6:0:0:0: [sdd] 3906963456 512-byte logical blocks: (2.00 TB/1.81 TiB)
Apr 12 10:19:58 UB64 kernel: [   18.118584] sd 6:0:0:0: [sdd] Write Protect is off
Apr 12 10:19:58 UB64 kernel: [   18.118588] sd 6:0:0:0: [sdd] Mode Sense: 47 00 10 08
Apr 12 10:19:58 UB64 kernel: [   18.121337] sd 6:0:0:0: [sdd] No Caching mode page found
Apr 12 10:19:58 UB64 kernel: [   18.121346] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Apr 12 10:19:58 UB64 kernel: [   18.127015] sd 6:0:0:0: [sdd] No Caching mode page found
Apr 12 10:19:58 UB64 kernel: [   18.127019] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Apr 12 10:19:58 UB64 kernel: [   18.147700]  sdd: sdd1
Apr 12 10:19:58 UB64 kernel: [   18.153608] sd 6:0:0:0: [sdd] No Caching mode page found
Apr 12 10:19:58 UB64 kernel: [   18.153616] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Apr 12 10:19:58 UB64 kernel: [   18.153623] sd 6:0:0:0: [sdd] Attached SCSI disk
Apr 12 10:19:58 UB64 ata_id[2343]: HDIO_GET_IDENTITY failed for '/dev/sdd': Invalid argument
Apr 12 10:19:58 UB64 kernel: [   18.367587] sd 6:0:0:0: [sdd] Unhandled sense code
Apr 12 10:19:58 UB64 kernel: [   18.367590] sd 6:0:0:0: [sdd]  
Apr 12 10:19:58 UB64 kernel: [   18.367592] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:19:58 UB64 kernel: [   18.367593] sd 6:0:0:0: [sdd]  
Apr 12 10:19:58 UB64 kernel: [   18.367594] Sense Key : Medium Error [current] 
Apr 12 10:19:58 UB64 kernel: [   18.367597] sd 6:0:0:0: [sdd]  
Apr 12 10:19:58 UB64 kernel: [   18.367598] Add. Sense: Unrecovered read error
Apr 12 10:19:58 UB64 kernel: [   18.367600] sd 6:0:0:0: [sdd] CDB: 
Apr 12 10:19:58 UB64 kernel: [   18.367601] Read(10): 28 00 00 1d 20 a0 00 00 20 00
Apr 12 10:19:58 UB64 kernel: [   18.367607] end_request: critical medium error, dev sdd, sector 1908896
Apr 12 10:19:58 UB64 kernel: [   18.367609] quiet_error: 156 callbacks suppressed
Apr 12 10:19:58 UB64 kernel: [   18.367610] Buffer I/O error on device sdd1, logical block 238356
Apr 12 10:19:58 UB64 kernel: [   18.367616] Buffer I/O error on device sdd1, logical block 238357
Apr 12 10:19:58 UB64 kernel: [   18.367618] Buffer I/O error on device sdd1, logical block 238358
Apr 12 10:19:58 UB64 kernel: [   18.367620] Buffer I/O error on device sdd1, logical block 238359
Apr 12 10:19:59 UB64 kernel: [   18.911725] sd 6:0:0:0: [sdd] Unhandled sense code
Apr 12 10:19:59 UB64 kernel: [   18.911729] sd 6:0:0:0: [sdd]  
Apr 12 10:19:59 UB64 kernel: [   18.911730] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 12 10:19:59 UB64 kernel: [   18.911731] sd 6:0:0:0: [sdd]  
Apr 12 10:19:59 UB64 kernel: [   18.911732] Sense Key : Medium Error [current] 
Apr 12 10:19:59 UB64 kernel: [   18.911734] sd 6:0:0:0: [sdd]  
Apr 12 10:19:59 UB64 kernel: [   18.911736] Add. Sense: Unrecovered read error
Apr 12 10:19:59 UB64 kernel: [   18.911737] sd 6:0:0:0: [sdd] CDB: 
Apr 12 10:19:59 UB64 kernel: [   18.911738] Read(10): 28 00 00 1d 20 a0 00 00 08 00
Apr 12 10:19:59 UB64 kernel: [   18.911743] end_request: critical medium error, dev sdd, sector 1908896
Apr 12 10:19:59 UB64 kernel: [   18.911746] Buffer I/O error on device sdd1, logical block 238356
```

Attached is a screen shot of Gparted.  I am not sure what option I use to rebuild table?

> **user_of_gnomes said:**
> 
Did you manage to clone your hard drive?

If file recovery is important to you, you should consider taking the hard drive out of the usb-casing and hooking it up directly to the mainboard. That way we'll also be able to see the S.M.A.R.T-status of your hard drive which I am rather curious about ...

New hardrive arrives later today, then I will clone.

---

### Post by user_of_gnomes on 2015-04-14
See, the thing with data recovery is that you first clone the drive and then work on the clone. You never work on the only source you've got .. Unless the data is completely meaningless to you.

I have a feeling your hard drive is failing which makes leaving it alone until you can clone it all the more important.

---

### Post by feartheterrapin on 2015-04-14
> **user_of_gnomes said:**
> See, the thing with data recovery is that you first clone the drive and then work on the clone. You never work on the only source you've got .. Unless the data is completely meaningless to you.


I agree with cloning first.  So I assume cloning the disk vice the partition is the way to go using the following command:

dd if=/dev/sdX of=/dev/sdY bs=512 conv=noerror,sync 

So is dd the better option over ddrescue?

---

### Post by user_of_gnomes on 2015-04-14
In case of a failing hard drive,[ gddrescue is the superior choice.]("http://www.forensicswiki.org/wiki/Ddrescue") Dd might just give up if it encounters non-readable sectors. Note that the program is called gddrescue but the command is ddrescue. 

the command format for gddrescue is ddrescue infile outfile logfile
For example:

sudo ddrescue /dev/sdX /media/*username*/*mount name*/drive.img /media/*username*/*mount name*/drive.log

Where /dev/sdX is the damaged hard drive in question, drive.img a bit-copy image of sda and .log the log-file that you can use to resume the operation should you cancel it.
Alternatively you could copy directly to another drive by using ddrescue /dev/sdX /dev/sdY /media/*username*/*mount name*/drive.log 
The log is optional but recommended.

(Where sdX would be the input and sdY the output. Make absolutely sure that you have the output and input right! Don't take my word for it, look it up in the respective manuals. [ddrescue does away with the formality of if= and of=]("http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html"))

If you were to use dd the command I would put in: dd if=/dev/sdX and of=/dev/sdY conv=noerror
dd defaults to 512-byte block-size

You can use sync but I don't know if it'll be too useful, it seems to fill gaps in your clone with zeroes. 
When writing to an image, you'll want to add noerror,notrunc.

I prefer working from images so that I can  mount the image as read-only and grab the data without having to worry about altering my clone. You can also mount the image as read-write so that you can alter it its contents if necessary.
Rarely do I dd the image to a hard drive and work from there (like when I need to use Windows to help me recover data) but it helps to keep the original image in tact whenever possible so you can always start from scratch.

If you are going to mount the image you'll need an additional set of instructions but I assume you'll be cloning directly to the new drive unless you have another 2tb of storage space lying around?

---

### Post by feartheterrapin on 2015-04-14
Thanks for detailed explanation.  Creating an image seems the best way, but I am somewhat confused still.

My spare 2TB drive arrived today.  Do I need to reformat?  It is currently formatted NTFS with a bunch of WD software.  Is ext4 OK?

The faulty drive is 2TB as well.  Where does the log file go?  I assume it will make take up too much room to clone a drive.  Can the log file go on a third drive?  How big will the "drive.img" be?

The faulty drive is /dev/sdd and the new drive is /dev/sde (Elements).  DataFile is the third drive.  Would the following command work?

```
sudo ddrescue -v -d -r3 /dev/sdd /dev/sde /media/DataFiles/logfile.txt
```

or for a image:

```
sudo ddrescue -v -d -r3 /dev/sdd /media/Elements/drive.img /media/DataFiles/logfile.txt
```

---

### Post by user_of_gnomes on 2015-04-15
> My spare 2TB drive arrived today. Do I need to reformat? It is currently formatted NTFS with a bunch of WD software. Is ext4 OK?

No, dd will overwrite everything. It doesn't matter what you do with the hard drive before hand. As long as Linux can see the drive and it is in good health, you're pretty much good to go.
Another thing you can (easily) do with ddrescue and dd is write zeroes to every sector to make the data unrecoverable. We're the same thing now except that instead of zeroes, we're using your data to fill up all of its sectors.

> The faulty drive is 2TB as well. Where does the log file go? I assume it will make take up too much room to clone a drive. Can the log file go on a third drive? How big will the "drive.img" be?

the image file will be as large as the hard drive that you are cloning so yes, you probably won't have the room for an image unless you have *another* 2tb-drive lying around. In this case, I'd opt for the drive-to-drive clone. Saves you the bother of having to mount the image.

You could place the log file anywhere you wanted as long as it is NOT on either the input or the output. So a third hard drive would indeed be a good option.

I usually run ddrescue without any options but the ones you have there seem fine. you r3 means it'll re-try 3 times. Default is zero I believe.
From my experience, if it couldn't read it the first time it won't be able to the second or third time either but you might get lucky. Will also increase the time it takes to clone if you have a lot of bad sectors.

Is DataFiles a mount-point or a user name?

this process could take an entire day, by the way, depending on how hard ddrescue is going to have to try. Make sure you hook it up to a usb3-interface for maximum speed.

Still curious about the S.M.A.R.T output, did you see a chance to remove the hard drive from its shell? Or does it report the data through the usb-interface?

---

### Post by feartheterrapin on 2015-04-15
```
Is DataFiles a mount-point or a user name?
```

mount-point

```
Still curious about the S.M.A.R.T output, did you see a chance to remove the hard drive from its shell? Or does it report the data through the usb-interface?
```

Did not remove drive yet, wanted to clone first.  Through the USB I get a "Unknown USB bridge" error when trying to read S.M.A.R.T data.

---

### Post by user_of_gnomes on 2015-04-15
Yeah, I don't think I've ever seen a usb-interface that relayed S.M.A.R.T-output. Anyhow, keep us posted.

---

### Post by feartheterrapin on 2015-04-15
So what did I accomplish?  ddrescue is complete.  I mounted the clone drive and it is identical to the original drive.

 Below is my terminal screen:
```
$ sudo ddrescue -v -d -r3 /dev/sdd /dev/sde /media/DataFiles/logfile.txt -f 
   
 About to copy 2 TBytes from /dev/sdd to /dev/sde 
     Starting positions: infile = 0 B,  outfile = 0 B 
     Copy block size: 128 sectors 
 Sector size: 512  bytes 
 Max retries: 3     
 Direct: yes    Sparse: no    Split: yes    Truncate: no 
  
 Press Ctrl-C to interrupt 
 Initial status (read from logfile) 
 rescued:         0 B,  errsize:       0 B,  errors:       0 
 Current status 
 rescued:        2 TB,  errsize:    4096 B,  current rate:    21504 B/s 
    ipos:   977358 kB,   errors:       1,    average rate:   71816 kB/s 
    opos:   977358 kB,     time from last successful read:       0 s 
 Finished                        
 $  

``` 

 Below is my logfile:
 ```
# Rescue Logfile. Created by GNU ddrescue version 1.14 

 # Command line: ddrescue -v -d -r3 /dev/sdd /dev/sde /media/DataFiles/logfile.txt -f 
 # current_pos  current_status 
 0x3A414E00     + 
 #      pos        size  status 
 0x00000000  0x3A414000  + 
 0x3A414000  0x00001000  - 
 0x3A415000  0x1D184CEB000  +

``` 

 What is next?

---

### Post by user_of_gnomes on 2015-04-16
Well ... I'd run it through chkdsk.exe and see what Windows makes of it. 

You can also try re-running testdisk or dosfsck now you have a known healthy drive and see if it is now capable of repairing the file system.
Try running dosfsck with -r -v and not -a -t 

Alternatively, if I -really- wanted the data I would use photorec to data carve. Unfortunately, that would render your folder structure completely useless and the file names will be randomly chosen.
Photorec comes with testdisk. You could do this -before- you do anything else to at least get a copy of your data and then experiment further.

---

### Post by feartheterrapin on 2015-04-16
Dosfsck provided the following result:
 ```
$ sudo dosfsck -r -v /dev/sde  
 dosfsck 3.0.12 (29 Oct 2011)  
 dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN 
 Currently, only 1 or 2 FATs are supported, not 251.  
 $ 
```
 
 Being lost with ddrescue, I tried recovering lost files using UFS Explorer.  Most if not all files seem to be available including all the files I supposedly permanently deleted.  In addition,  all directories have names different from the original name. So a little challenge sorting through.  
 
 Is there any thing else I could try to restore the HDD to its original state?  With ddrescue only finding one error I was hoping some tool could fix that one 4096 B error.

---

### Post by user_of_gnomes on 2015-04-16
You ran through the options in [this]("http://www.cgsecurity.org/wiki/Advanced_FAT_Repair") guide on the clone?

---

### Post by feartheterrapin on 2015-04-17
Never mind, I found it.  Still searching for table.  Will report back

> **user_of_gnomes said:**
> You ran through the options in [this]("http://www.cgsecurity.org/wiki/Advanced_FAT_Repair") guide on the clone?

Thanks for the link.  However, it says: ```
TestDisk can rebuild a FAT boot sector. Choose **RebuildBS** in the menu - it's safe and doesn't modify the disk. Use **List** to check the result and **Write** if you have been able to list your files.
```

But my menu looks like:```
Disk /dev/sdd - 2000 GB / 1862 GiB - CHS 243198 255 63

 [ Analyse  ] Analyse current partition structure and search for lost partitions
 [ Advanced ] Filesystem Utils
 [ Geometry ] Change disk geometry
 [ Options  ] Modify options
>[ MBR Code ] Write TestDisk MBR code to first sector
 [ Delete   ] Delete all data in the partition table
 [ Quit     ] Return to disk selection


```

---

### Post by user_of_gnomes on 2015-04-17
It's under Advanced -> Boot -> rebuildBS

---

### Post by feartheterrapin on 2015-04-17
I did find it.  I guess my last edit was not clear.  Any way, I see I have been approaching this effort wrong by searching the FAT 32 partition.  I am now searching the non partition as a FAT 32.  Lots found.  But only one directory so far  is recognizable.  Interestingly, hundreds of files/folders labeled as satcodx1.

---

### Post by user_of_gnomes on 2015-04-18
> **feartheterrapin said:**
> I did find it.  I guess my last edit was not clear.  Any way, I see I have been approaching this effort wrong by searching the FAT 32 partition.  I am now searching the non partition as a FAT 32.  Lots found.  But only one directory so far  is recognizable.  Interestingly, hundreds of files/folders labeled as satcodx1.

Did you make any progress?

---

### Post by feartheterrapin on 2015-04-18
It is finding folders.  Only one was recognizable.  The scan is 75% complete as I type.

BTW...When I reformat my new HDD which will be used to hold image back ups and critical file backups, what format do you recommend?  I was using FAT 32 as that is how the HDD was delivered.  Would EXT 4 or some other format be better?  I am backing up mostly Linux partitions and one Windows partition.

---

### Post by user_of_gnomes on 2015-04-18
I use ext4 if I don't have to access the files with Windows. I haven't had any problems so far but I often have to access files with Windows so I use NTFS and FAT32 a lot.
Can't tell you if it'd be easier to recover files from ext4, you'd have to do some research on that.

---

### Post by feartheterrapin on 2015-04-19
I changed the scan from manual to automatic since the scan stopped several times for me to review a directory.  The automatic scan finally finished last night not finding anything.  So I rebuilt the new drive (the one being used as the clone) as my new backup drive.  I have not done anything with the original drive yet.  If not to difficult, I will remove the HDD from the casing and see what S.M.A.R.T says next week when I return home.

---

### Post by feartheterrapin on 2015-04-19
So I rescanned the original drive, selected the non partition, rebuilt partition table and ended with the attached.

I will reformat and drive as back up to back up unless there are future failures.  I will still investigation S.M.A.R.T.

---

### Post by user_of_gnomes on 2015-04-19
Very curious about the S.M.A.R.T-status.

Too bad you couldn't recover anything, you might want to see if there are a few more tools out there that can help you. Data carving is still an option as well using photorec.

---

### Post by feartheterrapin on 2015-04-19
> **user_of_gnomes said:**
> Very curious about the S.M.A.R.T-status.

Too bad you couldn't recover anything, you might want to see if there are a few more tools out there that can help you. Data carving is still an option as well using photorec.

I will do S.M.A.R.T-status in the next couple of weeks.  Like  mentioned earlier, I did recover the few directories I needed via UFS Explorer.  I did find a few directories using TESTDISK, just not the ones of interest.  I was really hoping to repair the disk like it was prior to the reboot that corrupted it.  TESTDISK seems to be a very powerful tool, I just need to learn yo use it better, but then again, it is a tool you hope you never need.

---

### Post by feartheterrapin on 2015-05-28
I know it took a while, but I finally removed the HDD and installed directly to PC.  Drive was not mountable.  SMART data found a few bad sectors.  Results attached. I assume this disk should be trashed.  

I will reformat one more time just to see how it preforms.  I will not use it for anything I need.

---

### Post by user_of_gnomes on 2015-05-29
> **feartheterrapin said:**
> I know it took a while, but I finally removed the HDD and installed directly to PC.  Drive was not mountable.  SMART data found a few bad sectors.  Results attached. I assume this disk should be trashed.  

I will reformat one more time just to see how it preforms.  I will not use it for anything I need.

For personal and professional use, I discard hard drives when they report even one bad sector or when other reports do not match expectations. Cheaper to replace a hard drive than to recover data!

You should use [badblocks]("http://linux.die.net/man/8/badblocks") to check our your harddrive. It is very thorough (and will take a LONG time).
 (badblocks -wsv is recommended if the data on it can be removed, else -nsv)

---

### Post by feartheterrapin on 2015-05-29
> **user_of_gnomes said:**
> For personal and professional use, I discard hard drives when they report even one bad sector or when other reports do not match expectations. Cheaper to replace a hard drive than to recover data!

You should use [badblocks]("http://linux.die.net/man/8/badblocks") to check our your harddrive. It is very thorough (and will take a LONG time).
 (badblocks -wsv is recommended if the data on it can be removed, else -nsv)

When attempting to reformat, the process failed with an I/O error.  I tried to reboot so I could recreate the error, however, I never could get the PC to boot.  Interestingly, during the boot cycle, it seemed to hang on the bios for a long time, got to the GRUB, but then hit an error after the GRUB.  After several failed attempts of rebooting, I removed the bad drive, and the PC boots normally again.  I will discard the drive.  Surprised that a seldom used three year old drive failed.  Also,it is interesting that a non-bootable drive can prevent a PC with a good bootable drive from booting.

---

### Post by user_of_gnomes on 2015-05-29
> **feartheterrapin said:**
> When attempting to reformat, the process failed with an I/O error.  I tried to reboot so I could recreate the error, however, I never could get the PC to boot.  Interestingly, during the boot cycle, it seemed to hang on the bios for a long time, got to the GRUB, but then hit an error after the GRUB.  After several failed attempts of rebooting, I removed the bad drive, and the PC boots normally again.  I will discard the drive.  Surprised that a seldom used three year old drive failed.  Also,it is interesting that a non-bootable drive can prevent a PC with a good bootable drive from booting.

That's most likely because the BIOS is waiting for the drive to get its act together and the drive just can't seem to figure it out. Might not be able to get up to speed or stuck recalibrating. Along with the other data you gathered on the health of your hard drive a sure-tell sign of drive failure.

It's been a while since I read your posts but I recall this drive to be housed in an external casing, right? They often break down after a few years from my experience, even when not used all that often.The PSU in your computer has all sorts of tech to straighten out ripples and interference and the power supply that came with your external hard drive probably has none or very little. Add vibration and moisture to that and you've got yourself a dying hard drive. Like Murphy's law of combat states: Your gun was made by the lowest bidder. 

Did you manage to get any of your data back, though?

---

### Post by feartheterrapin on 2015-05-30
> **user_of_gnomes said:**
> 
It's been a while since I read your posts but I recall this drive to be housed in an external casing, right? 

Did you manage to get any of your data back, though?

Yes, this was a USB drive that failed and I removed the HDD from the casing to view the S.M.A.R.T  data.

I was able to recover all my data using UFS Explorer.  I also ran ddrescue and TestDisk as you recommended.  I did find my data using TestDisk, however, none of the file names were recognizable.  

I do appreciate all of you help/guidance.  This was a good learning exercise for me.  Thanks!
And I now keep a backup of my primary backup drive.

---

### Post by user_of_gnomes on 2015-05-31
No problem! 

I've never tried UFS explorer before, I'm going to give that a shot. Thanks for the feedback.

---

