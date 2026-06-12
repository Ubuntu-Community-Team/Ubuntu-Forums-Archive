---
title: "Problem with ext3 partition :'("
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Fadeev on 2008-02-06
Hello everyone.

I have a problem. After the increase of one of the sections deteriorated file system. Used Acronis Disk Editor.

The table of sections in order.
Tried fsck:
```
ruslan@ruslan-desktop:~$ sudo fsck -a /dev/sda4
[sudo] password for ruslan:
fsck 1.40.2 (12-Jul-2007)
/dev/sda4: Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

/dev/sda4: Block bitmap for group 1 is not in group.  (block 0)


/dev/sda4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
ruslan@ruslan-desktop:~$ sudo e2fsck -b 32768 /dev/sda4
e2fsck 1.40.2 (12-Jul-2007)
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>



```
Now defined as ext2 partition :'(
	
On the partition was more important 100 gigabytes of information.
How to restore a section?  :confused::(

---

### Post by Fadeev on 2008-02-06
someone please help!

---

### Post by astrotech226 on 2008-02-06
The message about it being an ext2 filesystem is OK.  Ext2 and ext3 are technically the same filesystem with ext3 simply having journaling enabled.  If you want to reanable the journal, you can do this:

$ sudo tune2fs -j /dev/sda4

I don't think that this will make any difference for you.  Did you try the command they suggested by attempting to use an alternate superblock?

$ sudo e2fsck -b 32768 /dev/sda4

---

### Post by Fadeev on 2008-02-06
Journal is not created, an error```
ruslan@ruslan-desktop:~$ sudo tune2fs -j /dev/sda4
[sudo] password for ruslan:
tune2fs 1.40.2 (12-Jul-2007)
Creating journal inode: 
tune2fs: A block group is missing an inode table 
        while trying to create journal file

```

and... about superblock
```
ruslan@ruslan-desktop:~$ sudo e2fsck -b 32768 /dev/sda4
e2fsck 1.40.2 (12-Jul-2007)
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

```
sad :(

---

### Post by astrotech226 on 2008-02-06
This probably won't work either, but does this output anything?

$ sudo dumpe2fs /dev/sda4

You might have to do a "-f" after the dumpe2fs.  Also, have you checked your log files for any error messages?

---

### Post by Fadeev on 2008-02-06
dumpe2fs return:
```
ruslan@ruslan-desktop:~$ dumpe2fs /dev/sda4
dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: Permission denied while trying to open /dev/sda4
Couldn't find valid filesystem superblock.
ruslan@ruslan-desktop:~$ sudo dumpe2fs /dev/sda4
dumpe2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          b8df3e14-9f4a-48a2-ae88-b8325550dc2f
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      dir_index filetype sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              28852224
Block count:              57673349
Reserved block count:     2885385
Free blocks:              13004730
Free inodes:              26397076
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Fri Dec 28 21:38:02 2007
Last mount time:          Tue Feb  5 02:33:17 2008
Last write time:          Wed Feb  6 16:13:26 2008
Mount count:              2
Maximum mount count:      32
Last checked:             Mon Feb  4 22:35:04 2008
Check interval:           15552000 (6 months)
Next check after:         Sat Aug  2 23:35:04 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Default directory hash:   tea
Directory Hash Seed:      0f90ce11-1331-4946-9070-4689efa2028d
Journal backup:           inode blocks
ext2fs_read_bb_inode: A block group is missing an inode table 
1876, 24121878, 24121880-24121881, 24121883-24121884, 24121887, 24121889, 24121891, 24121893, 24121897, 24121900, 24121902-24121904, 24121906-24121907, 24121910, 24121913-24121921, 24121927-24121930, 24121932-24121933, 24121935, 24121937, 24121939, 24121942........manu numbers.................................................................................

```

---

### Post by astrotech226 on 2008-02-06
OK...  Let's try to use one of the superblock backups.  This command will not modify the partition, just simply output some information you are going to need.

$ sudo mke2fs -n -S /dev/sda4

You should get a section that reads: "Superblock backups stored on blocks:"  Take one of the backup numbers (not the 32768 that you used before) and enter it into this:

$ sudo e2fsck -b <one of the backup numbers> /dev/sda4

What does this output?

---

### Post by Fadeev on 2008-02-06
```
 sudo mke2fs -n -S /dev/sda4
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
28852224 inodes, 57673349 blocks
2883667 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1761 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

```
and
```
root@ruslan-desktop:/home/ruslan# sudo e2fsck -b 98304 /dev/sda4
e2fsck 1.40.2 (12-Jul-2007)
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

/dev/sda4 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Special (device/socket/fifo/symlink) file (inode 5196097) has immutable
or append-only flag set.  Clear<y>?
```
try yes?

---

### Post by astrotech226 on 2008-02-06
I would say yes to everything.  We could have passed a flag to do it automatically.

What is this partition used for?

---

### Post by Fadeev on 2008-02-06
How-to do this automatically? there are many of them:
```
Illegal block #1 (2698289364) in inode 7793818.  CLEARED.
Illegal block #2 (2698281172) in inode 7793818.  CLEARED.
Illegal block #3 (2698289364) in inode 7793818.  CLEARED.
Illegal block #4 (2161410260) in inode 7793818.  CLEARED.
Illegal block #5 (2167439572) in inode 7793818.  CLEARED.
Inode 7793818 is too big.  Truncate<y>? yes

Block #6 (4980800) causes symlink to be too big.  CLEARED.
Illegal block #7 (2686550261) in inode 7793818.  CLEARED.
Illegal block #8 (2167406680) in inode 7793818.  CLEARED.
Illegal block #9 (2686517344) in inode 7793818.  CLEARED.
Block #10 (7602284) causes symlink to be too big.  CLEARED.
Too many illegal blocks in inode 7793818.
Clear inode<y>? yes

Inode 7793664 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2686554324) in inode 7793664.  CLEARED.
Illegal block #1 (2686558241) in inode 7793664.  CLEARED.
Illegal block #2 (2698289185) in inode 7793664.  CLEARED.
Illegal block #3 (2686558499) in inode 7793664.  CLEARED.
Illegal block #4 (2148573217) in inode 7793664.  CLEARED.
Illegal block #5 (69509362) in inode 7793664.  CLEARED.
Illegal block #6 (70033441) in inode 7793664.  CLEARED.
Illegal block #7 (70553812) in inode 7793664.  CLEARED.
Illegal block #8 (2686518332) in inode 7793664.  CLEARED.
Illegal block #9 (2686558241) in inode 7793664.  CLEARED.
Illegal block #10 (2686518340) in inode 7793664.  CLEARED.
Too many illegal blocks in inode 7793664.
Clear inode<y>? yes

Inode 7793659 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2161410260) in inode 7793659.  CLEARED.
Illegal block #1 (2149679316) in inode 7793659.  CLEARED.
Illegal block #2 (2161410260) in inode 7793659.  CLEARED.
Illegal block #3 (2698289185) in inode 7793659.  CLEARED.
Illegal block #4 (2698289364) in inode 7793659.  CLEARED.
Illegal block #5 (2698289364) in inode 7793659.  CLEARED.
Illegal block #6 (2161418452) in inode 7793659.  CLEARED.
Illegal block #7 (2698289364) in inode 7793659.  CLEARED.
Illegal block #8 (2686558450) in inode 7793659.  CLEARED.
Illegal block #9 (2700214536) in inode 7793659.  CLEARED.
Illegal block #10 (2163376370) in inode 7793659.  CLEARED.
Too many illegal blocks in inode 7793659.
Clear inode<y>? yes

Inode 7793638 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2161410260) in inode 7793638.  CLEARED.
Illegal block #1 (2161410180) in inode 7793638.  CLEARED.
Illegal block #2 (2161410260) in inode 7793638.  CLEARED.
Illegal block #3 (98599124) in inode 7793638.  CLEARED.
Illegal block #4 (2698289364) in inode 7793638.  CLEARED.
Illegal block #5 (2693046484) in inode 7793638.  CLEARED.
Illegal block #6 (2698289364) in inode 7793638.  CLEARED.
Illegal block #7 (2698289364) in inode 7793638.  CLEARED.
Illegal block #8 (2698289364) in inode 7793638.  CLEARED.
Illegal block #9 (2161410260) in inode 7793638.  CLEARED.
Illegal block #10 (2156135912) in inode 7793638.  CLEARED.
Too many illegal blocks in inode 7793638.
Clear inode<y>? yes

Inode 7793680 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2698280990) in inode 7793680.  CLEARED.
Illegal block #1 (2698289364) in inode 7793680.  CLEARED.
Illegal block #2 (2161410260) in inode 7793680.  CLEARED.
Illegal block #3 (2429845716) in inode 7793680.  CLEARED.
Illegal block #4 (2698249300) in inode 7793680.  CLEARED.
Illegal block #5 (2429849812) in inode 7793680.  CLEARED.
Illegal block #6 (2161418452) in inode 7793680.  CLEARED.
Illegal block #7 (2161418452) in inode 7793680.  CLEARED.
Illegal block #8 (2698289364) in inode 7793680.  CLEARED.
Illegal block #9 (2161410260) in inode 7793680.  CLEARED.
Illegal block #10 (2698281172) in inode 7793680.  CLEARED.
Too many illegal blocks in inode 7793680.
Clear inode<y>? yes

Inode 7793797 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2161410260) in inode 7793797.  CLEARED.
Illegal block #1 (106987773) in inode 7793797.  CLEARED.
Illegal block #2 (2161378920) in inode 7793797.  CLEARED.
Illegal block #3 (2149744885) in inode 7793797.  CLEARED.
Illegal block #4 (2161410226) in inode 7793797.  CLEARED.
Illegal block #5 (2148533880) in inode 7793797.  CLEARED.
Illegal block #6 (2429845716) in inode 7793797.  CLEARED.
Illegal block #7 (2429849633) in inode 7793797.  CLEARED.
Illegal block #8 (2429849633) in inode 7793797.  CLEARED.
Illegal block #9 (2170750596) in inode 7793797.  CLEARED.
Illegal block #10 (2161410339) in inode 7793797.  CLEARED.
Too many illegal blocks in inode 7793797.
Clear inode<y>? yes

Inode 7793829 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2698289364) in inode 7793829.  CLEARED.
Illegal block #1 (2161410260) in inode 7793829.  CLEARED.
Illegal block #2 (2161410260) in inode 7793829.  CLEARED.
Illegal block #3 (2161410260) in inode 7793829.  CLEARED.
Illegal block #4 (2161410260) in inode 7793829.  CLEARED.
Illegal block #5 (2161410260) in inode 7793829.  CLEARED.
Illegal block #6 (2156135924) in inode 7793829.  CLEARED.
Illegal block #7 (2156175572) in inode 7793829.  CLEARED.
Illegal block #8 (100696276) in inode 7793829.  CLEARED.
Illegal block #9 (2698289284) in inode 7793829.  CLEARED.
Illegal block #10 (102761992) in inode 7793829.  CLEARED.
Too many illegal blocks in inode 7793829.
Clear inode<y>? yes

Inode 7793589 has illegal block(s).  Clear<y>? yes

Illegal block #0 (168299008) in inode 7793589.  CLEARED.
Illegal block #1 (2698250772) in inode 7793589.  CLEARED.
Illegal block #2 (2698289364) in inode 7793589.  CLEARED.
Illegal block #3 (2165901860) in inode 7793589.  CLEARED.
Illegal block #4 (2698289433) in inode 7793589.  CLEARED.
Illegal block #5 (170696737) in inode 7793589.  CLEARED.
Illegal block #6 (171213053) in inode 7793589.  CLEARED.
Illegal block #7 (2161410260) in inode 7793589.  CLEARED.
Illegal block #8 (2698281172) in inode 7793589.  CLEARED.
Illegal block #9 (2165940257) in inode 7793589.  CLEARED.
Illegal block #10 (2686558489) in inode 7793589.  CLEARED.
Too many illegal blocks in inode 7793589.
Clear inode<y>? yes

Inode 7793647 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2167439572) in inode 7793647.  CLEARED.
Illegal block #1 (2149679361) in inode 7793647.  CLEARED.
Illegal block #2 (72646868) in inode 7793647.  CLEARED.
Illegal block #3 (2161410290) in inode 7793647.  CLEARED.
Illegal block #4 (73437396) in inode 7793647.  CLEARED.
Illegal block #5 (2168557601) in inode 7793647.  CLEARED.
Illegal block #6 (2167439605) in inode 7793647.  CLEARED.
Illegal block #7 (2429845716) in inode 7793647.  CLEARED.
Illegal block #8 (2161410260) in inode 7793647.  CLEARED.
Illegal block #9 (2429849633) in inode 7793647.  CLEARED.
Illegal block #10 (2161410260) in inode 7793647.  CLEARED.
Too many illegal blocks in inode 7793647.
Clear inode<y>? yes

Inode 7793629 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2170790130) in inode 7793629.  CLEARED.
Illegal block #1 (2149679316) in inode 7793629.  CLEARED.
Illegal block #2 (2686558241) in inode 7793629.  CLEARED.
Illegal block #3 (2698289364) in inode 7793629.  CLEARED.
Illegal block #4 (2161418273) in inode 7793629.  CLEARED.
Illegal block #5 (2698281172) in inode 7793629.  CLEARED.
Illegal block #6 (2698289364) in inode 7793629.  CLEARED.
Inode 7793629 is too big.  Truncate<y>? yes

Block #7 (30179540) causes symlink to be too big.  CLEARED.
Illegal block #8 (2686558241) in inode 7793629.  CLEARED.
Illegal block #9 (2161410150) in inode 7793629.  CLEARED.
Illegal block #10 (2688385126) in inode 7793629.  CLEARED.
Too many illegal blocks in inode 7793629.
Clear inode<y>? yes

Inode 7793632 has illegal block(s).  Clear<y>? yes

Illegal block #1 (2161378112) in inode 7793632.  CLEARED.
Illegal block #2 (2161410260) in inode 7793632.  CLEARED.
Illegal block #3 (2161410180) in inode 7793632.  CLEARED.
Illegal block #4 (2161410301) in inode 7793632.  CLEARED.
Illegal block #5 (2161410260) in inode 7793632.  CLEARED.
Illegal block #6 (2156135240) in inode 7793632.  CLEARED.
Illegal block #7 (2156167380) in inode 7793632.  CLEARED.
Illegal block #9 (2698281213) in inode 7793632.  CLEARED.
Illegal block #10 (2698289364) in inode 7793632.  CLEARED.
Illegal block #11 (2698289284) in inode 7793632.  CLEARED.
Illegal block #-1 (2156135256) in inode 7793632.  CLEARED.
Too many illegal blocks in inode 7793632.
Clear inode<y>? yes

Inode 7793635, i_size is 357087102939734032, should be 0.  Fix<y>? yes

Inode 7793635, i_blocks is 2161410081, should be 0.  Fix<y>? yes

Inode 7793652 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2705162557) in inode 7793652.  CLEARED.
Illegal block #1 (2698289168) in inode 7793652.  CLEARED.
Illegal block #2 (116131548) in inode 7793652.  CLEARED.
Illegal block #3 (117442292) in inode 7793652.  CLEARED.
Illegal block #4 (2705162485) in inode 7793652.  CLEARED.
Illegal block #5 (2156167485) in inode 7793652.  CLEARED.
Illegal block #6 (2693038292) in inode 7793652.  CLEARED.
Illegal block #7 (118005972) in inode 7793652.  CLEARED.
Illegal block #8 (2163376260) in inode 7793652.  CLEARED.
Illegal block #9 (118530290) in inode 7793652.  CLEARED.
Illegal block #10 (2706931986) in inode 7793652.  CLEARED.
Too many illegal blocks in inode 7793652.
Clear inode<y>? yes

Inode 7793782 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2686558241) in inode 7793782.  CLEARED.
Illegal block #1 (2161418273) in inode 7793782.  CLEARED.
Illegal block #2 (2161410260) in inode 7793782.  CLEARED.
Illegal block #3 (2686558241) in inode 7793782.  CLEARED.
Illegal block #4 (2161410180) in inode 7793782.  CLEARED.
Illegal block #5 (159940861) in inode 7793782.  CLEARED.
Illegal block #6 (2161410180) in inode 7793782.  CLEARED.
Illegal block #7 (2164066704) in inode 7793782.  CLEARED.
Illegal block #8 (2698289284) in inode 7793782.  CLEARED.
Illegal block #9 (2698250648) in inode 7793782.  CLEARED.
Illegal block #10 (2163345828) in inode 7793782.  CLEARED.
Too many illegal blocks in inode 7793782.
Clear inode<y>? yes

Inode 7793696 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2156167523) in inode 7793696.  CLEARED.
Illegal block #2 (2153775832) in inode 7793696.  CLEARED.
Illegal block #4 (2698289284) in inode 7793696.  CLEARED.
Illegal block #5 (2156135144) in inode 7793696.  CLEARED.
Illegal block #6 (2700247282) in inode 7793696.  CLEARED.
Illegal block #7 (2698248944) in inode 7793696.  CLEARED.
Illegal block #8 (2698248964) in inode 7793696.  CLEARED.
Illegal block #9 (2165768976) in inode 7793696.  CLEARED.
Illegal block #10 (2687107864) in inode 7793696.  CLEARED.
Illegal block #11 (2153808151) in inode 7793696.  CLEARED.
Illegal block #-1 (2156167264) in inode 7793696.  CLEARED.
Too many illegal blocks in inode 7793696.
Clear inode<y>? yes

Inode 7793644 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2418122785) in inode 7793644.  CLEARED.
Illegal block #1 (2686517800) in inode 7793644.  CLEARED.
Illegal block #2 (2693005872) in inode 7793644.  CLEARED.
Illegal block #3 (2163384532) in inode 7793644.  CLEARED.
Inode 7793644 is too big.  Truncate<y>? yes

Block #4 (37265650) causes symlink to be too big.  CLEARED.
Illegal block #5 (2163376260) in inode 7793644.  CLEARED.
Block #6 (37789938) causes symlink to be too big.  CLEARED.
Illegal block #7 (2161418286) in inode 7793644.  CLEARED.
Illegal block #8 (2161410260) in inode 7793644.  CLEARED.
Illegal block #9 (2161410260) in inode 7793644.  CLEARED.
Illegal block #10 (2161410260) in inode 7793644.  CLEARED.
Too many illegal blocks in inode 7793644.
Clear inode<y>? yes

Inode 7793823 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2159902932) in inode 7793823.  CLEARED.
Illegal block #1 (2156167357) in inode 7793823.  CLEARED.
Illegal block #3 (2161410180) in inode 7793823.  CLEARED.
Illegal block #4 (2161410180) in inode 7793823.  CLEARED.
Illegal block #5 (2163507557) in inode 7793823.  CLEARED.
Illegal block #7 (2418118868) in inode 7793823.  CLEARED.
Illegal block #8 (2163380436) in inode 7793823.  CLEARED.
Illegal block #9 (2170880804) in inode 7793823.  CLEARED.
Illegal block #10 (2159182047) in inode 7793823.  CLEARED.
Illegal block #11 (2163376340) in inode 7793823.  CLEARED.
Illegal block #-1 (2156167410) in inode 7793823.  CLEARED.
Too many illegal blocks in inode 7793823.
Clear inode<y>? yes

Inode 7793703 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2700255341) in inode 7793703.  CLEARED.
Illegal block #1 (2698289213) in inode 7793703.  CLEARED.
Illegal block #2 (2161410150) in inode 7793703.  CLEARED.
Illegal block #3 (2164105277) in inode 7793703.  CLEARED.
Illegal block #4 (105152614) in inode 7793703.  CLEARED.
Illegal block #5 (2158429776) in inode 7793703.  CLEARED.
Illegal block #6 (2158461095) in inode 7793703.  CLEARED.
Illegal block #7 (2686649944) in inode 7793703.  CLEARED.
Illegal block #8 (2691499632) in inode 7793703.  CLEARED.
Illegal block #9 (2164097277) in inode 7793703.  CLEARED.
Illegal block #10 (2161410180) in inode 7793703.  CLEARED.
Too many illegal blocks in inode 7793703.
Clear inode<y>? yes

Inode 7793801 has illegal block(s).  Clear<y>? yes

Illegal block #0 (149200929) in inode 7793801.  CLEARED.
Illegal block #1 (2691530994) in inode 7793801.  CLEARED.
Illegal block #2 (2686517248) in inode 7793801.  CLEARED.
Illegal block #3 (2686558254) in inode 7793801.  CLEARED.
Illegal block #4 (2686517260) in inode 7793801.  CLEARED.
Illegal block #5 (2161418273) in inode 7793801.  CLEARED.
Illegal block #6 (2168291540) in inode 7793801.  CLEARED.
Illegal block #7 (2161377300) in inode 7793801.  CLEARED.
Illegal block #8 (2164097236) in inode 7793801.  CLEARED.
Illegal block #9 (2161377312) in inode 7793801.  CLEARED.
Illegal block #10 (2686550371) in inode 7793801.  CLEARED.
Too many illegal blocks in inode 7793801.
Clear inode<y>? yes

Inode 7793816 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2161410260) in inode 7793816.  CLEARED.
Illegal block #1 (2161410260) in inode 7793816.  CLEARED.
Illegal block #2 (2161410260) in inode 7793816.  CLEARED.
Illegal block #3 (2161410260) in inode 7793816.  CLEARED.
Illegal block #4 (155222228) in inode 7793816.  CLEARED.
Illegal block #5 (2698289364) in inode 7793816.  CLEARED.
Illegal block #6 (156016852) in inode 7793816.  CLEARED.
Illegal block #7 (2156175572) in inode 7793816.  CLEARED.
Illegal block #8 (2693038292) in inode 7793816.  CLEARED.
Illegal block #9 (156803284) in inode 7793816.  CLEARED.
Illegal block #10 (2163376260) in inode 7793816.  CLEARED.
Too many illegal blocks in inode 7793816.
Clear inode<y>? yes

Inode 7793633, i_size is 291612458900291796, should be 0.  Fix<y>? yes

Inode 7793633, i_blocks is 61907156, should be 0.  Fix<y>? yes

Inode 7793709 has illegal block(s).  Clear<y>? yes

Illegal block #1 (2158494256) in inode 7793709.  CLEARED.
Illegal block #2 (2158526676) in inode 7793709.  CLEARED.
Inode 7793709 is too big.  Truncate<y>? yes

Block #3 (37781672) causes symlink to be too big.  CLEARED.
Illegal block #4 (2698289188) in inode 7793709.  CLEARED.
Block #5 (39060040) causes symlink to be too big.  CLEARED.
Block #6 (40632932) causes symlink to be too big.  CLEARED.
Illegal block #7 (2159845588) in inode 7793709.  CLEARED.
Illegal block #8 (2159837396) in inode 7793709.  CLEARED.
Illegal block #9 (2698289340) in inode 7793709.  CLEARED.
Block #10 (41459900) causes symlink to be too big.  CLEARED.
Illegal block #11 (2166915427) in inode 7793709.  CLEARED.
Too many illegal blocks in inode 7793709.
Clear inode<y>? yes

Inode 7793805 has illegal block(s).  Clear<y>? yes

Illegal block #1 (2686550273) in inode 7793805.  CLEARED.
Illegal block #2 (2686558420) in inode 7793805.  CLEARED.
Illegal block #3 (2686558420) in inode 7793805.  CLEARED.
Illegal block #5 (2698289364) in inode 7793805.  CLEARED.
Illegal block #6 (2686558241) in inode 7793805.  CLEARED.
Illegal block #7 (2161377936) in inode 7793805.  CLEARED.
Illegal block #8 (2686517912) in inode 7793805.  CLEARED.
Illegal block #10 (2686517964) in inode 7793805.  CLEARED.
Illegal block #11 (2698248916) in inode 7793805.  CLEARED.
Illegal block #-1 (2160263904) in inode 7793805.  CLEARED.
Illegal block #-1 (1493943594) in inode 7793805.  CLEARED.
Too many illegal blocks in inode 7793805.
Clear inode<y>? yes

Inode 7793697 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2698249124) in inode 7793697.  CLEARED.
Illegal block #1 (2153807968) in inode 7793697.  CLEARED.
Illegal block #2 (2161410180) in inode 7793697.  CLEARED.
Illegal block #3 (2153807968) in inode 7793697.  CLEARED.
Illegal block #4 (2693038292) in inode 7793697.  CLEARED.
Illegal block #5 (62431444) in inode 7793697.  CLEARED.
Illegal block #6 (62947460) in inode 7793697.  CLEARED.
Illegal block #7 (63480020) in inode 7793697.  CLEARED.
Illegal block #8 (2163344344) in inode 7793697.  CLEARED.
Illegal block #9 (65577202) in inode 7793697.  CLEARED.
Illegal block #10 (2698289364) in inode 7793697.  CLEARED.
Too many illegal blocks in inode 7793697.
Clear inode<y>? yes

Inode 7793614 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2164065360) in inode 7793614.  CLEARED.
Illegal block #1 (2161410296) in inode 7793614.  CLEARED.
Illegal block #2 (2164359485) in inode 7793614.  CLEARED.
Illegal block #3 (2163376445) in inode 7793614.  CLEARED.
Illegal block #4 (72909057) in inode 7793614.  CLEARED.
Illegal block #5 (2163344480) in inode 7793614.  CLEARED.
Illegal block #6 (2163376370) in inode 7793614.  CLEARED.
Illegal block #7 (2163376370) in inode 7793614.  CLEARED.
Illegal block #8 (2161410180) in inode 7793614.  CLEARED.
Illegal block #9 (2163344488) in inode 7793614.  CLEARED.
Illegal block #10 (2163541104) in inode 7793614.  CLEARED.
Too many illegal blocks in inode 7793614.
Clear inode<y>? yes

Inode 7793620 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2167447809) in inode 7793620.  CLEARED.
Illegal block #1 (2686519140) in inode 7793620.  CLEARED.
Illegal block #2 (2163572993) in inode 7793620.  CLEARED.
Illegal block #3 (2686519152) in inode 7793620.  CLEARED.
Illegal block #4 (2700216188) in inode 7793620.  CLEARED.
Illegal block #5 (2163384336) in inode 7793620.  CLEARED.
Illegal block #6 (126124048) in inode 7793620.  CLEARED.
Illegal block #7 (2686558241) in inode 7793620.  CLEARED.
Illegal block #8 (2686558241) in inode 7793620.  CLEARED.
Illegal block #9 (2686558241) in inode 7793620.  CLEARED.
Illegal block #10 (2686519180) in inode 7793620.  CLEARED.
Too many illegal blocks in inode 7793620.
Clear inode<y>? yes

Inode 7793653 has illegal block(s).  Clear<y>? yes

Illegal block #0 (129540129) in inode 7793653.  CLEARED.
Illegal block #1 (2168291581) in inode 7793653.  CLEARED.
Illegal block #2 (2700216264) in inode 7793653.  CLEARED.
Illegal block #3 (2686550258) in inode 7793653.  CLEARED.
Illegal block #4 (2429849633) in inode 7793653.  CLEARED.
Illegal block #5 (2686558241) in inode 7793653.  CLEARED.
Illegal block #6 (131598288) in inode 7793653.  CLEARED.
Illegal block #7 (2163541984) in inode 7793653.  CLEARED.
Illegal block #8 (2418118868) in inode 7793653.  CLEARED.
Illegal block #9 (2167447585) in inode 7793653.  CLEARED.
Illegal block #10 (2161410081) in inode 7793653.  CLEARED.
Too many illegal blocks in inode 7793653.
Clear inode<y>? yes

Inode 7793645 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2686558420) in inode 7793645.  CLEARED.
Illegal block #1 (2161418273) in inode 7793645.  CLEARED.
Illegal block #4 (2686517996) in inode 7793645.  CLEARED.
Illegal block #5 (2161410260) in inode 7793645.  CLEARED.
Illegal block #6 (2698289364) in inode 7793645.  CLEARED.
Illegal block #7 (2693759006) in inode 7793645.  CLEARED.
Illegal block #8 (2702803225) in inode 7793645.  CLEARED.
Illegal block #9 (2686558241) in inode 7793645.  CLEARED.
Illegal block #10 (2418082548) in inode 7793645.  CLEARED.
Illegal block #11 (2698289185) in inode 7793645.  CLEARED.
Illegal block #-1 (2161410081) in inode 7793645.  CLEARED.
Too many illegal blocks in inode 7793645.
Clear inode<y>? yes

Inode 7793623 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2168295636) in inode 7793623.  CLEARED.
Illegal block #1 (159416532) in inode 7793623.  CLEARED.
Illegal block #2 (2161410260) in inode 7793623.  CLEARED.
Illegal block #3 (2149679316) in inode 7793623.  CLEARED.
Illegal block #4 (2165932244) in inode 7793623.  CLEARED.
Illegal block #5 (2161410081) in inode 7793623.  CLEARED.
Illegal block #6 (2161410260) in inode 7793623.  CLEARED.
Illegal block #7 (2429845716) in inode 7793623.  CLEARED.
Illegal block #8 (2164101332) in inode 7793623.  CLEARED.
Illegal block #9 (2156167494) in inode 7793623.  CLEARED.
Illegal block #10 (2167439572) in inode 7793623.  CLEARED.
Too many illegal blocks in inode 7793623.
Clear inode<y>? yes

Inode 7793822, i_size is 9291630629282160673, should be 0.  Fix<y>? yes

Inode 7793822, i_blocks is 2156167380, should be 0.  Fix<y>? yes

Inode 7793582 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2698281172) in inode 7793582.  CLEARED.
Illegal block #1 (2698289364) in inode 7793582.  CLEARED.
Illegal block #2 (2161418452) in inode 7793582.  CLEARED.
Illegal block #3 (71868628) in inode 7793582.  CLEARED.
Illegal block #4 (72384545) in inode 7793582.  CLEARED.
Illegal block #5 (72917025) in inode 7793582.  CLEARED.
Illegal block #6 (74227924) in inode 7793582.  CLEARED.
Illegal block #7 (76547208) in inode 7793582.  CLEARED.
Illegal block #8 (77595800) in inode 7793582.  CLEARED.
Illegal block #9 (2698289284) in inode 7793582.  CLEARED.
Illegal block #10 (2156135596) in inode 7793582.  CLEARED.
Too many illegal blocks in inode 7793582.
Clear inode<y>? yes

Inode 7793826 has illegal block(s).  Clear<y>? yes

Illegal block #0 (62391216) in inode 7793826.  CLEARED.
Illegal block #1 (63209488) in inode 7793826.  CLEARED.
Illegal block #2 (2685444308) in inode 7793826.  CLEARED.
Illegal block #3 (65274844) in inode 7793826.  CLEARED.
Illegal block #4 (2686558420) in inode 7793826.  CLEARED.
Illegal block #5 (67412180) in inode 7793826.  CLEARED.
Illegal block #6 (2686558329) in inode 7793826.  CLEARED.
Illegal block #7 (2686518284) in inode 7793826.  CLEARED.
Illegal block #8 (2161378328) in inode 7793826.  CLEARED.
Illegal block #9 (2698281172) in inode 7793826.  CLEARED.
Illegal block #10 (69247188) in inode 7793826.  CLEARED.
Too many illegal blocks in inode 7793826.
Clear inode<y>? yes

Inode 7793689 has illegal block(s).  Clear<y>? yes

Illegal block #0 (2164097236) in inode 7793689.  CLEARED.
Illegal block #1 (2161410180) in inode 7793689.  CLEARED.
Illegal block #2 (2161410180) in inode 7793689.  CLEARED.
Illegal block #3 (2164097266) in inode 7793689.  CLEARED.
Illegal block #4 (2161410226) in inode 7793689.  CLEARED.
Illegal block #5 (2161410180) in inode 7793689.  CLEARED.
Illegal block #6 (2156167480) in inode 7793689.  CLEARED.
Illegal block #7 (2153808084) in inode 7793689.  CLEARED.
Illegal block #8 (2156167264) in inode 7793689.  CLEARED.
Illegal block #10 (2170781949) in inode 7793689.  CLEARED.
Illegal block #11 (2153807968) in inode 7793689.  CLEARED.
Too many illegal blocks in inode 7793689.
Clear inode<y>? yes

```

---

### Post by astrotech226 on 2008-02-06
One of two ways.  Pass the "-p" option to fsck to have it automatically fix any errors it is sure it can fix.  Anything real drastic will still ask you.  Passing the "-a" option will attempt to fix everything.

$ sudo e2fsck -a -b 98304 /dev/sda4

---

### Post by astrotech226 on 2008-02-06
One of two ways. Pass the "-p" option to fsck to have it automatically fix any errors it is sure it can fix. Anything real drastic will still ask you. Passing the "-a" option will attempt to fix everything.

$ sudo e2fsck -a -b 98304 /dev/sda4

---

### Post by Fadeev on 2008-02-06
I try it:
```
ruslan@ruslan-desktop:~$ sudo e2fsck -a -b 98304 /dev/sda4
/dev/sda4: Superblock has an invalid ext3 journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

/dev/sda4 was not cleanly unmounted, check forced.
/dev/sda4: Inode 7257916 has illegal block(s).  

/dev/sda4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)

```
Not working...

---

### Post by Fadeev on 2008-02-06
sudo e2fsck -y -b 98304 /dev/sda4
Command say yes for all questions...
Right?

---

### Post by astrotech226 on 2008-02-06
Yep!  I forgot to add that part.  Add the "-y" to answer yes to all questions.

---

### Post by Fadeev on 2008-02-07
operation has been going on all night.
it is okay?

---

### Post by astrotech226 on 2008-02-07
It can take a long time, but this doesn't look good.  What led up to this?  Did you have some sort of power problem or anything?

Also, what is the status of the other partitions sda1, sda2 and sda3?  Are they OK?

---

