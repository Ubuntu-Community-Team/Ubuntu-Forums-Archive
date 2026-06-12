---
title: "Ext.HD locked by win8"
date: 2014-01-27
forum: Hardware
---

### Post by patriq on 2014-01-27
Good day Ubuntu Community,

My issue is simple, I've been using an external HD on my uduntu 12.10 box with no problems of any kind, until the one singular time I plugged the ext.HD into my win8 box. The HD took its time to mount, but I just figured win8 is dumb, however since the whole drive is now read-only to my ubuntu box.

I tried to right-click the volume drive and change permissions to read and write and click apply to all, but nothing changes.
I plugged the drive back into my win8 box, emptied the bin and ejected the drive, still no change.

Here's hoping there's a simple solution..., Thank you Ubuntu community.

Cheers.

---

### Post by bapoumba on 2014-01-27
What kind of file system is on the drive ?

---

### Post by patriq on 2014-01-27
Hello! Thank you for inquiring, sadly I don't know how to answer that question, I can tell you that it was once the HD in an apple laptop with os X.6 and when the logicboard failed for the sixth time we opened the box to salvage the HD. I plugged it into my ubuntu box and it worked and I've been using it thus for over a year. It wasn't until last night when I plugged the HD into my new win8 for the first time that this issue occurred. I can read the files and copy but nothing else. I get the following error when I try to copy a file to my ext.hd

Error while copying "wine label standards.gif". 

Error opening file '/media/patrix/4B51-F92C/Patrik/wine label standards.gif': Read-only file system


When I go to the properties of the mounted icon for the HD I get this: filesystem type: msdos 
(which scares me) because if I could flush ms from my new box and load it with something sane I would


I hope this offers some insight...

---

### Post by oldfred on 2014-01-28
msdos or MBR is the partitioning type not the filesystem format.

I do not know OSX, but it may be different.

What does this show?

sudo parted -l
and or for whatever drive it is (bit more detail):
       sudo parted /dev/sdb unit s print

---

### Post by patriq on 2014-01-28
patrix@patrix:~$ sudo parted -l
Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system     Flags
 1      1049kB  159GB  159GB  primary   ext4            boot
 2      159GB   160GB  937MB  extended
 5      159GB   160GB  937MB  logical   linux-swap(v1)




Model: SAMSUNG HM250JI (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End    Size   Type     File system  Flags
 1      512B   250GB  250GB  primary  fat32




patrix@patrix:~$ sudo parted /dev/sdb unit s print
[sudo] password for patrix: 
Model: SAMSUNG HM250JI (scsi)
Disk /dev/sdb: 488397168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End         Size        Type     File system  Flags
 1      1s     488392064s  488392064s  primary  fat32

---

### Post by oldfred on 2014-01-29
Not sure what Windows may have done.
You have a FAT32 formatted partition on your 250GB drive.

You cannot change permissions and ownership on Windows type formats as they do not support those features. You set defaults as you mount the partition. But usually default mount by Nautilus works.
Partition may need chkdsk from Windows.

You can try this.
       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck -t vfat /dev/sdb1
see also 
man fsck

      
 [URL="http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt"]http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt
[/URL]
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy Is NTFS but vfat similar with settings in link above. Have not used vfat for ages so not sure of latest info.
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

[URL="http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt"]
[/URL]

---

### Post by patriq on 2014-02-02
Hello, I'm sorry the delay in getting back to you, I had some deadlines to meet.

Here is the result of the code you suggested, I don't know if I did it right, I'm not sure what you mean by [COLOR=#000000]<the fat32 device> so I just plugged the code into the terminal as you see here[/COLOR]


patrix@patrix:~$ sudo /sbin/fsck.vfat -V
[sudo] password for patrix: 
usage: /sbin/fsck.vfat [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -p       same as -a, for compat with other *fsck
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck


patrix@patrix:~$ sudo fsck -t vfat /dev/sdb1
fsck from util-linux 2.20.1
dosfsck 3.0.13, 30 Jun 2012, FAT32, LFN
Long filename fragment ":2Xt:5OV:Fqb:Egv:56X:2KJ:3vZ:1ka:FQ-:4O8:DCk:4ww:2gR" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)
1: Delete fragment
2: Leave it as it is.
3: Set start bit
? 




Not knowing what to do, I closed the terminal to kill the process. Then I relaunched and typed the last:


```
FSCK(8)                      System Administration                     FSCK(8)


NAME
       fsck - check and repair a Linux filesystem


SYNOPSIS
       fsck  [-lsAVRTMNP]  [-C  [fd]]  [-t fstype] [filesys...]  [--] [fs-spe&#8208;
       cific-options]


DESCRIPTION
       fsck is used to check and optionally repair one or more Linux  filesys&#8208;
       tems.   filesys  can  be  a device name (e.g.  /dev/hdc1, /dev/sdb2), a
       mount point (e.g.  /, /usr, /home), or an ext2 label or UUID  specifier
       (e.g.   UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root).  Nor&#8208;
       mally, the fsck program will try to  handle  filesystems  on  different
       physical  disk  drives  in  parallel to reduce the total amount of time
       needed to check all of them.


       If no filesystems are specified on the command line, and the -A  option
       is  not  specified,  fsck  will  default  to  checking  filesystems  in
       /etc/fstab serially.  This is equivalent to the -As options.


       The exit code returned by fsck is the sum of the following conditions:
            0    - No errors
            1    - Filesystem errors corrected
            2    - System should be rebooted
            4    - Filesystem errors left uncorrected
            8    - Operational error
            16   - Usage or syntax error
            32   - Fsck canceled by user request
            128  - Shared-library error
       The exit code returned when multiple filesystems  are  checked  is  the
       bit-wise OR of the exit codes for each filesystem that is checked.


       In  actuality,  fsck  is  simply a front-end for the various filesystem
       checkers (fsck.fstype) available under Linux.  The  filesystem-specific
       checker  is  searched for in /sbin first, then in /etc/fs and /etc, and
       finally in the directories listed in  the  PATH  environment  variable.
       Please  see  the  filesystem-specific  checker manual pages for further
       details.


OPTIONS
       -l     Lock the whole-disk  device  by  an  exclusive  flock(2).   This
              option  can be used with one device only (this means that -A and
              -l are mutually exclusive).  This  option  is  recommended  when
              more  fsck  (8)  instances  are  executed in the same time.  The
              option is ignored when used for multiple  devices  or  for  non-
              rotating disks.  fsck does not lock underlying devices when exe&#8208;
              cuted to check stacked devices (e.g. MD or DM) --  this  feature
              is not implemented yet.


       -s     Serialize  fsck  operations.   This  is  a  good idea if you are
              checking multiple filesystems and the checkers are in an  inter&#8208;
              active  mode.   (Note:  e2fsck(8) runs in an interactive mode by
              default.  To make e2fsck(8) run in a non-interactive  mode,  you
              must  either specify the -p or -a option, if you wish for errors
              to be corrected automatically, or the -n option if you do not.)


       -t fslist
              Specifies the type(s) of filesystem to be checked.  When the  -A
              flag  is  specified,  only  filesystems  that  match  fslist are
              checked.  The fslist parameter  is  a  comma-separated  list  of
              filesystems  and  options specifiers.  All of the filesystems in
              this comma-separated list may be prefixed by a negation operator
              'no'  or  '!',  which  requests  that only those filesystems not
              listed in fslist will be checked.  If none of the filesystems in
              fslist  is  prefixed  by  a  negation  operator, then only those
              listed filesystems will be checked.
              Options  specifiers  may  be  included  in  the  comma-separated
              fslist.   They  must  have  the  format  opts=fs-option.   If an
              options specifier is present, then only filesystems  which  con&#8208;
              tain  fs-option  in their mount options field of /etc/fstab will
              be checked.  If the options specifier is prefixed by a  negation
              operator, then only those filesystems that do not have fs-option
              in their mount options field of /etc/fstab will be checked.


              For example, if opts=ro appears in fslist, then only filesystems
              listed in /etc/fstab with the ro option will be checked.


              For compatibility with Mandrake distributions whose boot scripts
              depend upon an unauthorized UI change to the fsck program, if  a
              filesystem  type of loop is found in fslist, it is treated as if
              opts=loop were specified as an argument to the -t option.


              Normally, the  filesystem  type  is  deduced  by  searching  for
              filesys  in  the  /etc/fstab  file  and  using the corresponding
              entry.  If the type can not be deduced, and there is only a sin&#8208;
              gle  filesystem given as an argument to the -t option, fsck will
              use the specified filesystem type.  If this type is  not  avail&#8208;
              able, then the default filesystem type (currently ext2) is used.
       -A     Walk  through  the /etc/fstab file and try to check all filesys&#8208;
              tems in one run.  This option is typically used from the /etc/rc
              system  initialization  file,  instead  of multiple commands for
              checking a single filesystem.


              The root filesystem will be checked first unless the  -P  option
              is  specified  (see  below).   After  that,  filesystems will be
              checked in the order specified  by  the  fs_passno  (the  sixth)
              field  in  the  /etc/fstab  file.   Filesystems with a fs_passno
              value of 0 are skipped and are not checked at all.   Filesystems
              with  a  fs_passno value of greater than zero will be checked in
              order, with filesystems with the lowest fs_passno  number  being
              checked  first.  If there are multiple filesystems with the same
              pass number, fsck  will  attempt  to  check  them  in  parallel,
              although it will avoid running multiple filesystem checks on the
              same physical disk.


              fsck does not check stacked devices (RAIDs,  dm-crypt,  ...)  in
              parallel    with    any    other    device.    See   below   for
              FSCK_FORCE_ALL_PARALLEL setting.  The /sys filesystem is used to
              detemine dependencies between devices.
              Hence, a very common configuration in /etc/fstab files is to set
              the root filesystem to have a fs_passno value of 1  and  to  set
              all other filesystems to have a fs_passno value of 2.  This will
              allow fsck to automatically run filesystem checkers in  parallel
              if  it  is  advantageous  to do so.  System administrators might
              choose not to use this configuration if they need to avoid  mul&#8208;
              tiple  filesystem checks running in parallel for some reason ---
              for example, if the machine in question is short  on  memory  so
              that excessive paging is a concern.


              fsck  normally does not check whether the device actually exists
              before calling a filesystem specific  checker.   Therefore  non-
              existing devices may cause the system to enter filesystem repair
              mode during boot if the filesystem specific  checker  returns  a
              fatal  error.  The /etc/fstab mount option nofail may be used to
              have fsck skip non-existing devices.  fsck also skips non-exist&#8208;
              ing devices that have the special filesystem type auto


       -C [  fd  ]
              Display  completion/progress  bars for those filesystem checkers
              (currently only for ext2 and ext3) which  support  them.    Fsck
              will  manage  the  filesystem  checkers so that only one of them
              will display a progress bar at a time.  GUI front-ends may spec&#8208;
              ify  a file descriptor fd, in which case the progress bar infor&#8208;
              mation will be sent to that file descriptor.


       -M     Do not check mounted filesystems and return an exit  code  of  0
              for mounted filesystems.


       -N     Don't execute, just show what would be done.


       -P     When  the  -A flag is set, check the root filesystem in parallel
              with the other filesystems.  This is not the safest thing in the
              world  to  do,  since  if the root filesystem is in doubt things
              like the e2fsck(8) executable might be corrupted!   This  option
              is  mainly provided for those sysadmins who don't want to repar&#8208;
              tition the root filesystem to be small  and  compact  (which  is
              really the right solution).


       -R     When  checking  all  filesystems with the -A flag, skip the root
              filesystem.  (This is useful in case  the  root  filesystem  has
              already been mounted read-write.)


       -T     Don't show the title on startup.
       -V     Produce  verbose  output, including all filesystem-specific com&#8208;
              mands that are executed.


       fs-specific-options
              Options which are not understood  by  fsck  are  passed  to  the
              filesystem-specific  checker.   These  arguments  must  not take
              arguments, as there is no way for fsck to be  able  to  properly
              guess which options take arguments and which don't.


              Options  and  arguments  which  follow  the  --  are  treated as
              filesystem-specific options to be passed to the  filesystem-spe&#8208;
              cific checker.


              Please  note  that fsck is not designed to pass arbitrarily com&#8208;
              plicated options to  filesystem-specific  checkers.   If  you're
              doing something complicated, please just execute the filesystem-
              specific checker directly.  If you pass fsck some horribly  com&#8208;
              plicated  options  and  arguments,  and  it  doesn't do what you
              expect, don't bother reporting it as a bug.  You're almost  cer&#8208;
              tainly doing something that you shouldn't be doing with fsck.


       Options  to  different filesystem-specific fsck's are not standardized.
       If in doubt, please consult the man pages  of  the  filesystem-specific
       checker.   Although not guaranteed, the following options are supported
       by most filesystem checkers:


       -a     Automatically repair the filesystem without any  questions  (use
              this  option with caution).  Note that e2fsck(8) supports -a for
              backward compatibility only.  This option is mapped to  e2fsck's
              -p  option  which is safe to use, unlike the -a option that some
              filesystem checkers support.


       -n     For some filesystem-specific checkers, the -n option will  cause
              the fs-specific fsck to avoid attempting to repair any problems,
              but simply report such problems to stdout.  This is however  not
              true  for  all  filesystem-specific  checkers.   In  particular,
              fsck.reiserfs(8) will not report any corruption  if  given  this
              option.  fsck.minix(8) does not support the -n option at all.


       -r     Interactively  repair  the  filesystem  (ask for confirmations).
              Note: It is generally a bad idea to use this option if  multiple
              fsck's  are  being  run  in  parallel.   Also  note that this is
              e2fsck's default behavior; it supports this option for  backward
              compatibility reasons only.


       -y     For  some filesystem-specific checkers, the -y option will cause
              the fs-specific fsck to  always  attempt  to  fix  any  detected
              filesystem corruption automatically.  Sometimes an expert may be
              able to do better driving the fsck manually.  Note that not  all
              filesystem-specific checkers implement this option.  In particu&#8208;
              lar fsck.minix(8) and  fsck.cramfs(8)  do  not  support  the  -y
              option as of this writing.


AUTHOR
       Theodore Ts'o (tytso@mit.edu)


AVAILABILITY
       The  fsck  command  is  part of the util-linux package and is available
       from [ftp://ftp.kernel.org/pub/linux/utils/util-linux/](ftp://ftp.kernel.org/pub/linux/utils/util-linux/).


FILES
       /etc/fstab.


ENVIRONMENT VARIABLES
       The fsck program's behavior is affected by  the  following  environment
       variables:


       FSCK_FORCE_ALL_PARALLEL
              If  this environment variable is set, fsck will attempt to check
              all of the specified  filesystems  in  parallel,  regardless  of
              whether  the filesystems appear to be on the same device.  (This
              is useful for RAID systems or high-end storage systems  such  as
              those  sold  by  companies  such  as IBM or EMC.)  Note that the
              fs_passno value is still used.


       FSCK_MAX_INST
              This environment variable  will  limit  the  maximum  number  of
              filesystem  checkers  that  can  be  running  at one time.  This
              allows configurations which have a  large  number  of  disks  to
              avoid  fsck starting too many filesystem checkers at once, which
              might overload CPU and memory resources available on the system.
              If this value is zero, then an unlimited number of processes can
              be spawned.  This is currently the default, but future  versions
              of fsck may attempt to automatically determine how many filesys&#8208;
              tem checks can be run based on gathering  accounting  data  from
              the operating system.


       PATH   The  PATH environment variable is used to find filesystem check&#8208;
              ers.  A set of system directories  are  searched  first:  /sbin,
              /sbin/fs.d, /sbin/fs, /etc/fs, and /etc.  Then the set of direc&#8208;
              tories found in the PATH environment are searched.
       FSTAB_FILE
              This environment variable allows  the  system  administrator  to
              override  the  standard  location of the /etc/fstab file.  It is
              also useful for developers who are testing fsck.


SEE ALSO
       fstab(5), mkfs(8), fsck.ext2(8) or fsck.ext3(8)  or  e2fsck(8),  cramf&#8208;
       sck(8),   fsck.minix(8),   fsck.msdos(8),   fsck.jfs(8),   fsck.nfs(8),
       fsck.vfat(8), fsck.xfs(8), fsck.xiafs(8), reiserfsck(8).


util-linux                       February 2009                         FSCK(8)

```




There's a lot in there, I hope it will provide an answer. Again, thank you for taking the time to help me. 

Cheers

---

### Post by oldfred on 2014-02-02
Please use code tags in long text output. You can add easily by highlight text and click # in edit panel in advanced edit screen.
You last entry now in code tags is just the man page for fsck. q to exit
man fsck

This says you have corruption.
> Long filename fragment ":2Xt:5OV:Fqb:Egv:56X:2KJ:3vZ:1ka:FQ-:4O8:grin:Ck:4ww:2gR" found outside a LFN sequence.
  (Maybe the start bit is missing on the last fragment)

Best to have all data backed up, you you have to fix this to have it work with Linux. Perhaps the other systems ignore the issue?

Did you try to write a file over 4GB as FAT32 does not support it.

---

### Post by patriq on 2014-02-03
I don't think so, I plugged it into my ms box, after 10 minutes of 'loading' I simply unplugged it and it's been like this since.

Do you think I could just delete the fragment, reboot and pray?

---

### Post by oldfred on 2014-02-03
Unplugging in the middle of things almost always corrupts something.

Not sure where fragment is, but I think that is the only way to get it to work again.

You can also try Windows chkdsk but it should do the same thing.

---

