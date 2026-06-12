---
title: "Mounting NTFS partition at boot with NTFS-3G and making it show up (and be accesible)"
date: 2019-06-12
forum: Hardware
---

### Post by andrasol on 2019-06-12
I have a NTFS partition (without Windows having ever been installed in it) that I want to mount automatically after boot - but specifically using NTFS-3G so `chown` and `chmod` can be used on its folders.

Here is what I added to my `/etc/fstab`:

```
     UUID=[partition-uuid] /mnt/mydisk ntfs-3g auto,permissions,x-gvfs-show 0 1
```

Now, when I boot, the partition is indeed automatically mounted and the root can change ownership and permissions of folders in the NTFS partition - just as I wanted. Thanks to the `x-gvfs-show` option, the partition also shows up in software like Files and Nemo.

However, when I click on it in Files or Nemo, I get an error message with title "Unable to mount" that says:

[HTML] operation permitted for root only[/HTML]

If I then open Files or Nemo elevated as root, then when I click on the partition, I get the error message again with title "Unable to mount" but now saying:

[HTML] Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command.[/HTML]


In case I include the option `user` in my `/etc/fstab` mounting, i.e.:

```
     UUID=[partition-uuid] /mnt/mydisk ntfs-3g auto,user,permissions,x-gvfs-show 0 1
```

Then, regardless of opening Files or Nemo as root or not, when I click on the partition, I get the error message with title "Unable to mount" and saying:

[HTML] Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command.[/HTML]


How could I have it such that my NTFS partition is automatically mounted using NTFS-3G and be accessible via user interface software like Files and Nemo?

---

### Post by TheFu on 2019-06-12
This lack of POSIX permissions working has been bothering a bunch of us here for years. 

I've never seen *permissions* work after mount for NTFS that wasn't in a corporate environment with admins maintaining the Windows-userid --to-- Unix-userid mappings.  I'll do some testing today. Ok, the permissions option isn't working here ... without the .NTFS-3G/UserMapping  file. That file is required relative to the mount point.

So .... 
TOP_MNT=/misc/250G   # this is my mount point directory.
mkdir $TOP_MNT/.NTFS-3G
vi $TOP_MNT/.NTFS-3G/UserMapping
# If you don't need Windows compatibility, put these lines into the file
```
1000:1000:S-1-5-21-3141592653-589793238-462643383-1000
1001:1001:S-1-5-21-3141592653-589793238-462643383-1001
1002:1002:S-1-5-21-3141592653-589793238-462643383-1002
1003:1003:S-1-5-21-3141592653-589793238-462643383-1003
1004:1004:S-1-5-21-3141592653-589793238-462643383-1004
1005:1005:S-1-5-21-3141592653-589793238-462643383-1005
1006:1006:S-1-5-21-3141592653-589793238-462643383-1006
1007:1007:S-1-5-21-3141592653-589793238-462643383-1007
1008:1008:S-1-5-21-3141592653-589793238-462643383-1008
[COLOR="#FF0000"]1009[/COLOR]:[COLOR="#FF0000"]1009[/COLOR]:S-1-5-21-3141592653-589793238-462643383-[COLOR="#FF0000"]1009[/COLOR]

```
I made the red parts map 1-for-1 just for consistency.  You only need as many lines as there are users, but having more doesn't seem to matter.

Next, umount the NTFS partition and remount it. The user-mapping file is read at mount time. Now   chown and chmod work as expected.   

Remember, this is for when you DO NOT need to connect the disk to Windows.  If you do, then there is **ntfs-3g.usermap** which will scan the existing directories for Windows user/groups and build the file. See the manpage for that tool if more details are needed.  There are many caveats for this mapping, filenames, and other limitations.

Next, umount the ntfs storage and mount it with the *permissions* as one of the options. They recommend also using uid= and gid= and fmask, dmask options as fallbacks.  Permissions do not change automatically, so any existing files need a chown and a chmod to get the permissions you desire.  I can confirm that this works on 16.04 with an NTFS file system mounted both with a manual mount and through autofs.

I think this is huge for all the admins and people trying to help Windows people get permissions working on their NTFS partitions.

This only works with NTFS, not exFAT or vFAT or FAT32, at least as far as I know.
 
Unrelated: Running GUI programs with sudo can cause problems.  Best to avoid doing that, but if you must, use **sudo -H** to for a change of the HOME directory to the other userid to files in a standard user's HOME don't become owned by root.

---

### Post by oldfred on 2019-06-12
Some knowledgeable users here do not recommend setting permissions into NTFS.
       see comments by Morbius1 - post #11 
    [https://ubuntuforums.org/showthread.php?t=1979873&p=11968070#post11968070](https://ubuntuforums.org/showthread.php?t=1979873&p=11968070#post11968070)

This is a suggest set of parameters for NTFS.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
    
But unless you also have Windows, you should not be using NTFS. It will require chkdsk when it breaks and regular defrag to maintain performance. And you cannot do those from Linux, only from Windows.  You should then at least have a Windows repair disk to do those types of repairs, if you really want to keep NTFS.

---

### Post by TheFu on 2019-06-12
> **oldfred said:**
>  
But unless you also have Windows, you should not be using NTFS. It will require chkdsk when it breaks and regular defrag to maintain performance. And you cannot do those from Linux, only from Windows.  You should then at least have a Windows repair disk to do those types of repairs, if you really want to keep NTFS.

There are times when even without Windows, we need NTFS.  I have some video recording hardware. It stores the recordings on USB storage - either NTFS or FAT32.

But I will agree, that using ext4, xfs, or zfs would be preferred, if that could work.

About every month, I have to reformat the disk due to corruption problems.  Just modified the script for that to include creating the UserMapping file.  For me, the disk is for extremely temporary stuff.  I don't trust NTFS for anything important.  

The warnings I see in those links are without the UserMapping file, at best, it won't work and at worst, funky permissions are caused on Windows.  Lots of caveats.  Lots.

My NTFS mount options:
```
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002
```
I don't have UTF8 in there and probably should.  The uid/gid options are fallback is "permissions" doesn't work. That is according to the manpage.

---

### Post by TheFu on 2019-06-12
More testing data .... 

I connected the NTFS drive to a Windows machine here to see what happened.

Using Disk Manager of Windows7, it refused to run Scandisk.  The error was a generic - Cannot complete operation - type error. That wasn't the exact error. It refused to do it.  I didn't try it from a shell and didn't try chkdisk either. Sorry.

Went in under Win7 and added my local Windows account to the file and directory permissions for all files on the partition.  Attempts to remove "Everybody" from access gave errors.  I didn't research it too much, something about the parent permissions not allowing that. I moved up to the mount and changed the permissions there. Didn't think to try and remove Everybody.  I have a mind like a puppy seeing a squirrel. ;)  10 seconds, everything changes.

Copied over a tiny file from Windows onto the NTFS partition, unplugged it and reconnected it under Ubuntu. Did **not** mount it. Ran **sudo ntfs-3g.usermap /dev/sdc1**, which outputs Windows mappings, but asks for Unix uid or usernames to be provided.  The output was this:
```
:1000:S-1-5-21-643769535-2472160946-3813763046-513 
1000:1000:S-1-5-21-[COLOR="#A52A2A"]3141592653-589793238-462643383[/COLOR]-1000
Undecided :
```
The fact that the number is pi, 3.1415......, shows that someone has a sense of humor.  Thinking about this a little more, it could be from the left over UserMapping file I'd already created, since they map 1-for-1, but the group mapping from Windows is very different.  Probably an error on my side. Would MSFT make the default first local userid on Windows based on pi or would they try to make it random?

If I were doing this over again, I'd have a blank NTFS disk, then from Windows, I'd have each local userid copy at least 1 file over to the NTFS disk, then move the connection to Linux and run the sudo ntfs-3g.usermap /dev/sdXn tool again.  Perhaps naming the files to be copied over initially with the Windows username would make it easier to answer the Linux uid/gid questions?  IDK.

You really need to want this to work, but it isn't THAT much hassle.  How much is having chmod work on NTFS worth to you?  For me, it is of limited use due to my reason for using NTFS, but I'm glad I bothered.  

I just hope that people don't get this confused with Samba permissions. Two completely different things. Totally unrelated.

---

### Post by andrasol on 2019-06-12
Hi all, many thanks for the detailed reply.

Let me start by addressing a couple of points that were raised. First, I still do not have Windows installed but I will have shortly. That is why I need a partition to be NTFS; this is a hard requirement, no flexibility there. Second, I need that partition to (a) be auto-monunted every time computer starts; (b) it should be mounted with permissions and (c) it should be visible in software like Files, Nemo, etc.

The only way I see any of that to be possible is by using ntfs-3g. And indeed, as I said in the OP, it does work well for my purposes: I can set permissions and I can easily make it auto-mount. The only thing I can't have working is to have the partition be accessible in the left menu of Files, Nemo, etc. When I click on their link within those software, I get the errors mentioned in the OP. However, interestingly, if I directly navigate to the /mnt/ address of the partition within Files or Nemo, no error is raised and I can normally access the partition.

So, it seems that in my case, the issue is not related to needing to configure a ntfs-3g user mapping, isn't it?


Also, today I found the following. If i drop the 'x-gvfs-show' from my fstab entry and instead mount the partition in /media/, all works (including seeing and accessing it via Files or Nemo). That is, the issue only happens when trying to mount outside /media/ plus using 'x-gvfs-show'.

---

### Post by TheFu on 2019-06-13
> **andrasol said:**
>  
So, it seems that in my case, the issue is not related to needing to configure a ntfs-3g user mapping, isn't it?
 

When you connect to a Windows system, the lack of a mapping file will be a problem.  Access to the files will be seen as foreign and might be blocked.  You'll need a mapping file sooner or later.

Over the decades, experience as taught me never to mount storage to /media/  since that area is maintained by the gvfs tools.  Long ago, bad things could happen.  It has worked well for me.  I only mount things under /mnt/ for temporary admin use, as spelled out in the Linux File System Hierarchy Standard. [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) Following well-considered standards is helpful.  

Many people here use separate data partitions and create symbolic links from our HOME directories to the other partition for easy access.  No need to seek a button on the left of 1 specific GUI, when the link(s) in our HOME is available to any program, all the time.  Symbolic links are very useful. Something you might consider.

And please use the big_writes mount option.  It does help performance greatly.

Lastly, thanks for posting the issue.  I've been using the permissions with a mapping file the last day. It is nice to see expected permissions for data files on the NTFS partition. It will reduce my anxiety. So far, I haven't seen any issues.

---

### Post by TheFu on 2019-08-29
Update - permissions broke.  I don't know exactly when they stopped working.

It has been a few months and I haven't been checking the permissions on the files on my single NTFS partition.  Checked it yesterday and none of them were working.  The mount for that device hadn't been changed all this time. I use autofs.
Did a little troubleshooting and nothing helped.

Came back today and did some more troubleshooting. No joy.  The permissions that worked in June aren't working anymore.  No chmod or chown.  I did disable the autofs mount and used a direct CLI mount command to have direct control.  

Perhaps another night to sleep on the problem will get me some new ideas?

---

