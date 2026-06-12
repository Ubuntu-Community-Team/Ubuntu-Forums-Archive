---
title: "cannot backup to external disk with rsync, create hard links of add w permissions"
date: 2010-01-12
forum: Hardware
---

### Post by tevang on 2010-01-12
Dear Ubuntu users,

I want to backup my Documents directory and instead of copying everything to my external disk I tried to use this command line to create an incremental backup with rsync on my external disk:

$cd /media/My\ Passport
$rsync -a --delete --link-dest=../BackUp08.2009_Ubuntu/ /home/thomas2/Documents/  BackUp01.2010_Ubuntu/


but I get the following output:


rsync: chgrp "/media/My Passport/BackUp01.2010_Ubuntu/." failed: Operation not permitted (1)
rsync: chgrp "/media/My Passport/BackUp01.2010_Ubuntu/Cealign-0.8-RBS.zip" failed: Operation not permitted (1)
rsync: chgrp "/media/My Passport/BackUp01.2010_Ubuntu/Cytoscape_2_6_3_unix.sh" failed: Operation not permitted (1)
rsync: chgrp "/media/My Passport/BackUp01.2010_Ubuntu/Dendroscope_unix_2_3.sh" failed: Operation not permitted (1)
rsync: chgrp "/media/My Passport/BackUp01.2010_Ubuntu/NAMD_CVS_Linux-x86_64-CUDA.tar.gz" failed: Operation not permitted (1)
rsync: chgrp "/media/My Passport/BackUp01.2010_Ubuntu/PfMDR1_AAA1.fasta" failed: Operation not permitted (1)
......


Moreover when I try to create hard links from an older backup in my external disk with the following command line:

cp -al BackUp08.2009_Ubuntu/Reduce/reduce.3.13.080428.linuxi386 BackUp01.2010_Ubuntu/
cp: cannot create link `BackUp01.2010_Ubuntu/reduce.3.13.080428.linuxi386': Operation not permitted

I also tried to use sudo, even login as root with "sudo su" but didn't make any difference. The permissions of my external disk are the following and cannot add write privileges:

drwxr-xr-x 22 thomas2 root 32768 2010-01-13 04:18 My Passport

Is this normal? Any advice would be greatly appreciated.

---

