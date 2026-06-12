---
title: "fsck error on &quot;autocheck&quot; at boot-up"
date: 2008-08-09
forum: General Help
---

### Post by Bruce M. on 2008-08-09
Hi Folks,

It's "*autocheck the hard drives time*" on my machine and I'm getting an error that causes me to have to **[Ctrl]+D** to continue.

In the message I get, it says to run fsck manually without any options, so I did and get this:
```
bruloo@bruloo:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve '**UUID=7bb7ef81-4028-4838-9d42-93e544bec8d1**'
bruloo@bruloo:~$
```

Hmmmmmm...

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
**UUID=7bb7ef81-4028-4838-9d42-93e544bec8d1** /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=7f38d049-469a-4381-9f34-141617bf30e7 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=a8d5dcf9-0f8f-48e9-8c8d-013c703c95d2 /media/Data     ext3    relatime        0       2
# /dev/sda3
UUID=f06facd8-c5c1-460a-99a2-b42b704c97ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
Ouch, my [SIZE="2"]**/**[/SIZE] partition.

Any help out there?

Thanks
Bruce

---

### Post by Herman on 2008-08-09
Maybe your file system UUID number for your / (root) file system has changed somehow.
Can you remember doing something recently that might have caused it to change?

The following code can be used to check and see what your new file system UUID is in /dev/sda1.
```
sudo vol_id -u /dev/sda1
```You probably need to copy that new number to your /etc/fstab file and overwrite the out-of-date UUID number that is there at the moment.

How could it have been changed though?

Regards, Herman :)

---

### Post by Bruce M. on 2008-08-09
> **Herman said:**
> Maybe your file system UUID number for your / (root) file system has changed somehow.
Can you remember doing something recently that might have caused it to change?

The following code can be used to check and see what your new file system UUID is in /dev/sda1.
```
sudo vol_id -u /dev/sda1
```You probably need to copy that new number to your /etc/fstab file and overwrite the out-of-date UUID number that is there at the moment.

How could it have been changed though?

Regards, Herman :)

Hi Herman,
Thanks for responding. However:
```
bruloo@bruloo:~$ sudo vol_id -u /dev/sda1
[sudo] password for bruloo: 
7bb7ef81-4028-4838-9d42-93e544bec8d1
bruloo@bruloo:~$
```
... the results are the same nimber. :(

Next...
Bruce

---

### Post by Herman on 2008-08-09
That's very strange...

Okay, boot a Live CD and try this then, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

That should fix it or tell you why not.

Regards, Herman :)

---

### Post by Bruce M. on 2008-08-10
> **Herman said:**
> That's very strange...

Okay, boot a Live CD and try this then, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

That should fix it or tell you why not.

Regards, Herman :)

OK, from the LiveCD I did what you asked, saved the results to an SD disk in my Palm and here's the results:

**[COLOR="Red"]EDIT:[/COLOR]** 1 hour later: Just noticed what's in red below. See next post.
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
**[COLOR="Red"]/dev/sda1 is mounted.[/COLOR]**  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
                                                                               
  126352 inodes used (13.77%)
     865 non-contiguous inodes (0.7%)
         # of inodes with ind/dind/tind blocks: 6421/81/0
  888927 blocks used (24.27%)
       0 bad blocks
       1 large file

  100748 regular files
   10565 directories
      69 character device files
      26 block device files
       2 fifos
     479 links
   14931 symbolic links (14248 fast symbolic links)
       2 sockets
--------
  126822 files
ubuntu@ubuntu:~$
```
I am "assuming" the above is good as there isn't an error message.
However when I rebooted to the HD it failed on sda2 this time. :(

Will try this again tomorrow on sda2.

Bookmarked your site too.
VERY NICE STUFF!!!!!!!!!!
Bruce

---

### Post by Bruce M. on 2008-08-10
I don't believe what I didn't notice as I was doing that command .... **stupid, stupid, stupid!**

I used gparted to un-mount the partition then ran the terminal command, so I wasn't really expecting it.

Anyway, I thought I would use gparted for the whole thing (from the LiveCD)

Sure enough I had to "unmount" /dev/sda1 because "check" was greyed out.

After unmounting "unmount" was grey and check was black.

I hit "check" and expanded each section under details as they appeared.

The last thing I see is something like this:

/dev/sda1 is mounted
fsck .......
check abandoned or cancelled, I can't recall which.

Tomorrow I "reinstall".

Good night,
Bruce

---

### Post by Herman on 2008-08-10
Will running e2fsck again help? I suppose you will already have tried.
:( I'm sorry to read that your troubles got worse.

---

### Post by Bruce M. on 2008-08-10
> **Herman said:**
> Will running e2fsck again help? I suppose you will already have tried.
:( I'm sorry to read that your troubles got worse.

I'm not sure I want to ... it said the volume was mounted when I unmounted it.

And this morning I got this on booting after starting the autocheck of HDs:
```

/dev/sda2
64%                 Stage 1/5 1292/1394
run fsck MANUALLY
     (i.e.  without -a or -p option)
fsck died with exit status 4

```
I hit [Ctrl]+D, and ran fsck before anything else. The terminal is still open:
```
bruloo@bruloo:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=**7bb7ef81-4028-4838-9d42-93e544bec8d1**'
bruloo@bruloo:~$ 
```
That's the same as the very first one ... **sda1** not **sda2** where it died this morning.

Maybe I should check the HD's first for errors. My 200GB (sda1) is three or four years old and the 80GB (sda2) one year old.

Have a nice day.
Bruce

---

### Post by Herman on 2008-08-10
> I'm not sure I want to ... it said the volume was mounted when I unmounted it. I don't know why it would mount without being told, was this in a Ubuntu 'Desktop' Live/Install CD? I'm trying that out right now in a Ubuntu Interpid Ibex Alpha 3 Live CD that I just downloaded and I'm running e2fsck on file systems in my hard drive.

I already checked my Gutsy Gibbon, and now I'm running e2fsck in my Backups partition.
I typed the 'mount' command first to make sure nothing is mounted, but normally they don't mount by themselves in a Live CD.
I have had times when Gnome Partition Editor (GParted) in the Live CD can't umount a file system because it was mounted at the command line.

> And this morning I got this on booting after starting the autocheck of HDs:
     Code:
     /dev/sda2
64%                 Stage 1/5 1292/1394
run fsck MANUALLY
     (i.e.  without -a or -p option)
fsck died with exit status 4
```
sudo e2fsck -y -f -v /dev/sda2
```You need to run [SIZE=-1][FONT=Bitstream Vera Sans Mono]'sudo e2fsck -y -f -v /dev/sda2'[/FONT][/SIZE]on it.

> Code:
     bruloo@bruloo:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=**7bb7ef81-4028-4838-9d42-93e544bec8d1**'
bruloo@bruloo:~$ 
That's the same as the very first one ... **sda1** not **sda2** where it died this morning.

Yeah, that's a weird one. I don't know why it's doing that. Maybe checking your hard drives would be a good idea, although it sounds like they're still relatively new, but maybe they've been used a lot.

Well, all I can say is, don't let one bad experience put you off file system checking, because running a file system check is normally a good thing to do, as long as the file system isn't mounted at the time.
If it was me I'd still be trying to file system check my way back out of trouble. :)

---

### Post by Herman on 2008-08-10
```
sudo dumpe2fs -h /dev/sda1 
```Maybe try taking a look at the output from this command and see if gives us any clues.

[FONT=Bitstream Vera Sans Mono][/FONT]

---

### Post by webaake on 2008-08-10
I've recently had the same problem with one of my older disks. I noticed that it occasionally didn't show in bios. Does your disk always show up in bios?

Try to disconnect it physically and reconnect it in order to check the cabling.

I'm keeping an eye on this issue, it might even be some bug in Hardy after an update, but resetting the cabling seems to have solved my problems.

---

### Post by Bruce M. on 2008-08-10
> **Herman said:**
> ```
sudo dumpe2fs -h /dev/sda1 
```Maybe try taking a look at the output from this command and see if gives us any clues.

[FONT=Bitstream Vera Sans Mono][/FONT]

Sure hope you can figure it out, it's all Martian to me  (sorry if there are any Martians reading this).
```
bruloo@bruloo:~$ sudo dumpe2fs -h /dev/sda1
[sudo] password for bruloo: 
dumpe2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          7bb7ef81-4028-4838-9d42-93e544bec8d1
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              917504
Block count:              3662812
Reserved block count:     183140
Free blocks:              2786883
Free inodes:              791205
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      894
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Fri Aug  1 18:00:30 2008
Last mount time:          Sun Aug 10 09:22:20 2008
Last write time:          Sun Aug 10 09:22:20 2008
Mount count:              7
Maximum mount count:      32
Last checked:             Sun Aug 10 01:14:20 2008
Check interval:           15552000 (6 months)
Next check after:         Fri Feb  6 02:14:20 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       720912
Default directory hash:   tea
Directory Hash Seed:      9f1af5d9-2638-43dc-a042-3580f7316291
Journal backup:           inode blocks
Journal size:             128M

bruloo@bruloo:~$
```
My back-up is done and I'm heading to Ubuntu 64bit v8.04.1 in less than an hour.

Bruce

---

### Post by Bruce M. on 2008-08-10
> **Herman said:**
> I don't know why it would mount without being told, was this in a Ubuntu 'Desktop' Live/Install CD? I'm trying that out right now in a Ubuntu Interpid Ibex Alpha 3 Live CD that I just downloaded and I'm running e2fsck on file systems in my hard drive.

I was using the Xubuntu 64bit v8.04.1 LiveCD. I used gparted to check if the partitions were mounted, it said they were, I unmounted them and ran the code you gave me, and I see the error that the disk is mounted.  :(

> **Herman said:**
> I already checked my Gutsy Gibbon, and now I'm running e2fsck in my Backups partition.
I typed the 'mount' command first to make sure nothing is mounted, but normally they don't mount by themselves in a Live CD.
I have had times when Gnome Partition Editor (GParted) in the Live CD can't umount a file system because it was mounted at the command line.

```
sudo e2fsck -y -f -v /dev/sda2
```You need to run [SIZE=-1][FONT=Bitstream Vera Sans Mono]'sudo e2fsck -y -f -v /dev/sda2'[/FONT][/SIZE]on it.

Yeah, that's a weird one. I don't know why it's doing that. Maybe checking your hard drives would be a good idea, although it sounds like they're still relatively new, but maybe they've been used a lot.

Well, all I can say is, don't let one bad experience put you off file system checking, because running a file system check is normally a good thing to do, as long as the file system isn't mounted at the time.
If it was me I'd still be trying to file system check my way back out of trouble. :)

Don't know, but put this error with the fact my wife wants something GNOME has that Xfce doesn't ... guess what I'm doing. I'll miss Xfce but ....

Have a nice day
Bruce

---

### Post by Bruce M. on 2008-08-10
> **Herman said:**
> Well, all I can say is, don't let one bad experience put you off file system checking, because running a file system check is normally a good thing to do, as long as the file system isn't mounted at the time.
If it was me I'd still be trying to file system check my way back out of trouble. :)

You can bet I'll be going though the link you gave me with a fine tooth comb.

Thanks for your help.
Have a nice day.
Bruce

---

### Post by Herman on 2008-08-11
:) Well, your /dev/sda1 superblock looks okay to me. It looks pretty much the same as mine, and it says it's clean.
Regards, Herman

---

### Post by Bruce M. on 2008-08-11
> **Herman said:**
> :) Well, your /dev/sda1 superblock looks okay to me. It looks pretty much the same as mine, and it says it's clean.
Regards, Herman

Well, I think I'm looking at the same problem with Ubuntu (GNOME) 64bit.
I installed it last night, and this morning I did this:
```
bruloo@bruloo:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=ef966559-3f71-4e75-901b-5259113afaf7'
bruloo@bruloo:~$
```
and **sda1**:
```
bruloo@bruloo:~$ sudo dumpe2fs -h /dev/sda1
[sudo] password for bruloo: 
dumpe2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          ef966559-3f71-4e75-901b-5259113afaf7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              917504
Block count:              3662812
Reserved block count:     183140
Free blocks:              2751543
Free inodes:              781924
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      894
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Sun Aug 10 19:11:31 2008
Last mount time:          Mon Aug 11 09:20:51 2008
Last write time:          Mon Aug 11 09:20:51 2008
Mount count:              6
Maximum mount count:      24
Last checked:             Sun Aug 10 19:11:31 2008
Check interval:           15552000 (6 months)
Next check after:         Fri Feb  6 20:11:31 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       901132
Default directory hash:   tea
Directory Hash Seed:      5e6f8772-a4e9-4f71-a0de-217f0f6242bc
Journal backup:           inode blocks
Journal size:             128M
```
and **sda2:**
```
bruloo@bruloo:~$ sudo dumpe2fs -h /dev/sda2
dumpe2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          29dba414-3e7e-4a0e-96e5-9d3bc2ab1abe
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              11419648
Block count:              45654721
Reserved block count:     2282736
Free blocks:              44622233
Free inodes:              11407761
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1013
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Sun Aug 10 19:11:37 2008
Last mount time:          Mon Aug 11 09:20:52 2008
Last write time:          Mon Aug 11 09:20:52 2008
Mount count:              6
Maximum mount count:      36
Last checked:             Sun Aug 10 19:11:37 2008
Check interval:           15552000 (6 months)
Next check after:         Fri Feb  6 20:11:37 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      1aa08784-890d-455c-8281-5b4cc6d2e302
Journal backup:           inode blocks
Journal size:             128M
```
Both say **"clean"** but *fsck* by itself has a problem.

Not a happy camper.
Bruce

---

### Post by Herman on 2008-08-11
:) Okay, I tried with the same command and that command doesn't work at all for me either,
```
herman@intrepid-ibex:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=8b6b6d3e-759e-4ba4-8125-775f471b5de5'
```See? Probably we need to add 'sudo' to it and then maybe it'll work,
```
herman@intrepid-ibex:~$ sudo fsck
[sudo] password for herman: 
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda6 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
herman@intrepid-ibex:~$ 
```Okay, now what I'm doing wrong is, I didn't specify some other file system (one which is not mounted), to be checked. My command is for trying to check the file system I'm running at the moment, which is not a good idea.
Maybe I could try checking some other file system in my machine, by specifying one that is not mounted,
```
herman@intrepid-ibex:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
HARDY: clean, 200056/1327104 files, 1928157/5291401 blocks
herman@intrepid-ibex:~$ 

```That didn't seem to do anything much, it only paused for half a second. 
Probably if the file system really needed checking, it probably would have done something.

I don't really like fsck much. It's a good enough tool to run from a pprogram or a script for running file system checks on unidentified file systems.
What most people don't seem to realize about fsck is that it's a 'front end' for all the other file system checking programs. You can run a file system check on almost any file system with fsck, and if it's an ext3 file system, it will run e2fsck for you, but without any special options.
I would rather run e2fsck myself, with the options I want,
```
herman@intrepid-ibex:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  200056 inodes used (15.07%)
    2844 non-contiguous inodes (1.4%)
         # of inodes with ind/dind/tind blocks: 13065/161/0
 1928157 blocks used (36.44%)
       0 bad blocks
       1 large file

  156039 regular files
   21254 directories
      69 character device files
      26 block device files
       2 fifos
     436 links
   22649 symbolic links (20837 fast symbolic links)
       8 sockets
--------
  200483 files
```That took a few minutes and actually would have fixed my file system (if it needed fixing), or not me why not. :)

You should make sure to run your file system check from a live CD or if you do it from another hard disk installed Linux, just make sure the file system you want to check isn't mounted.
Normally, a live CD doesn't mount any hard disk file systems unless you tell it to, I don't know what went wrong with yours in that eariler post.
I prefer to run the file system specific command rather than just a vague fsck, and make sure you remember to specify the file system you want to have checked. :)

Regards, Herman :)

---

### Post by Bruce M. on 2008-08-11
Hi Herman,

Wow, thanks for all that.
Like I said I'll be reading those links and have this saved as well.

Once I get this set up just right, I'll try again.
Bruce

---

