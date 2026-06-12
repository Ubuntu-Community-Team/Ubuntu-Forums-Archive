---
title: "encrypted partitions checked every boot"
date: 2011-10-05
forum: Hardware
---

### Post by jcwoods on 2011-10-05
I have a laptop running 11.04 with encrypted root and swap partitions.  Only /boot is unencrypted.  Every time I boot, it runs through a file system check on the two data partitions (/ and /boot).  While this only takes a few seconds, it's gotten very annoying over the past year (since 10.10 or earlier).  Root is ext4 and boot is ext2.

My particulars (lightly edited to save space):

root@acorn:~# mount
/dev/mapper/sda3_crypt on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sda1 on /boot type ext2 (rw)

root@acorn:~# tune2fs -l /dev/sda1
tune2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          9a58fa3a-bd18-4571-81b6-99ce66e660e7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      filetype sparse_super
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              249368
Block count:              498688
Reserved block count:     24934
Free blocks:              413708
Free inodes:              249132
First block:              1
Block size:               1024
Fragment size:            1024
Blocks per group:         8192
Fragments per group:      8192
Inodes per group:         4088
Inode blocks per group:   511
Last mount time:          n/a
Last write time:          Wed Oct  5 06:25:39 2011
Mount count:              1
Maximum mount count:      30
Last checked:             Wed Oct  5 06:25:19 2011
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128


root@acorn:~# tune2fs -l /dev/mapper/sda3_crypt                                                                                                                                     
tune2fs 1.41.14 (22-Dec-2010)                                                                                                                                                       
Filesystem volume name:   <none>                                                                                                                                                    
Last mounted on:          /
Filesystem UUID:          3d74889c-b2b2-4e08-bd55-c66651f12d6c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              4677632
Block count:              18680063
Reserved block count:     934003
Free blocks:              14398500
Free inodes:              4393708
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Oct  7 22:51:57 2010
Last mount time:          Wed Oct  5 06:25:19 2011
Last write time:          Sun Sep 18 21:33:47 2011
Mount count:              12
[B]Maximum mount count:      20
Last checked:             Sun Sep 18 21:33:47 2011
Check interval:           15552000 (6 months)
Next check after:         Fri Mar 16 21:33:47 2012[/B]
Lifetime writes:          41 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1835107
Default directory hash:   half_md4
Journal backup:           inode blocks

---

