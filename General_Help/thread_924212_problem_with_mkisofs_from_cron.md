---
title: "problem with mkisofs from cron"
date: 2008-09-19
forum: General Help
---

### Post by gtr@frii.com on 2008-09-19
I have a script for backup to cd on an 8.04 server.  I have several windows systems sharing files off of samba and I backup this data with rsync daily from cron.  I have a script that I want to use to backup to cd once per week.  I can successfully execute the script from the CLI but it always fails from cron.  No errors show up in /var/log/syslog and the iso file always fails when the size reaches about 140MBytes. (I do not have access to the system at the moment, but I believe the actual ls -l shows the iso file is 153600000.  In the following script I've tried it numerous times from either /tmp or /exports/stage with the same results.  The tar file is about 250MBytes in size.  It always works from CLI and always fails from cron.What is going on here?

#!/bin/bash
mkisofs /tmp/shareback.tar.gz > /exports/stage/shareback.iso
cdrecord speed=8 -tao -silent -eject -data /exports/stage/shareback.iso
#mkisofs /tmp/shareback.tar.gz > /tmp/shareback.iso
#cdrecord speed=8 -tao -silent -eject -data /tmp/shareback.iso
#rm /tmp/shareback.*
#rm /exports/stage/shareback*

Further info.  I've been trying various steps.  Obviously, I should have been using the -o option.  In any case, in testing I used the following script which works fine from the CLI and fails silently from cron.  If I run it from the CLI and do an ls -l the iso file is there with correct time.  From cron, nothing happens, as viewed from ls -l output.  So,  . it appears that mkisofs and/or genisoimage are bailing due to some error in cron.

I'm still stumped.  Here's the latest incantation of the script.

#! /bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
rm -f /root/work/backup.iso
/usr/bin/genisoimage -o /root/work/backup.iso /root/work/foo.tar.gz

---

### Post by TatuSalin on 2008-09-20
Hello. Maybe you should redirect your iso file different way.

Your current script is 
#! /bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
rm -f /root/work/backup.iso
/usr/bin/genisoimage -o /root/work/backup.iso /root/work/foo.tar.gz

Maybe you should do like this?

#! /bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
rm -f /root/work/backup.iso
/usr/bin/genisoimage -o /root/work/backup.iso > /root/work/foo.tar.gz

You may also 

read more from man-pages.:guitar:

---

### Post by gtr@frii.com on 2008-09-20
I'm more confused now.  The compressed tar file was the source for the iso to be built.  Again, this shell script works just fine from the command line, but nothing happens when I run it form cron.

Since I don't have access to the 8.04 servere at the moment i"ve been working on my laptop with 8.04 ubuntu desktop. Clearly something is failing in the cron environment and I can't figure out what it is.  I've tried calling backup.sh from a wrapper bash shell in cron - it failed also.  Then I just started from a simple test case as detailed below using a slightly different version of backup.sh, plus some generated garbage files to make the iso from.

Here's backup.sh
#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

rm -f /root/work/test/BACKUP.ISO
genisoimage -input-charset UTF8 -o /root/work/test/BACKUP.ISO /root/work/test/ 

Here's what I did to build garbage
root@glen-laptop:~/work/test# cat build-garbage
root@glen-laptop:~/work/test# dd if=/boot/vmlinuz-2.6.24-19-generic of=garbage1 count=20000
3752+1 records in
3752+1 records out
1921464 bytes (1.9 MB) copied, 0.0648449 s, 29.6 MB/s
root@glen-laptop:~/work/test# cp garbage1 garbage2
root@glen-laptop:~/work/test# cp garbage1 garbage3
root@glen-laptop:~/work/test# ls -l garbage*
total 5652
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage1
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage2
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage3

root@glen-laptop:~/work/test# 

Here's what I got when I ran from the command line
root@glen-laptop:~/work/test# cat runfromCLI
root@glen-laptop:~/work/test# ./backup.sh 
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
2995 extents written (5 MB)
root@glen-laptop:~/work/test# ls -l
total 11672
-rw-r--r-- 1 root root 6133760 2008-09-20 17:52 BACKUP.ISO
-rwxr-xr-x 1 root root     192 2008-09-20 17:29 backup.sh
-rw-r--r-- 1 root root     513 2008-09-20 17:34 build-garbage
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage1
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage2
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage3
-rw-r--r-- 1 root root     842 2008-09-20 17:49 mount-garbage
-rw-r--r-- 1 root root       4 2008-09-20 17:52 runfromCLI
root@glen-laptop:~/work/test# 

Here's the result of mounting the iso
root@glen-laptop:~/work/test# cat mount-garbage
root@glen-laptop:~/work# modprobe loop
root@glen-laptop:~/work# cd test
root@glen-laptop:~/work/test# ls
BACKUP.ISO  backup.sh  build-garbage  garbage1	garbage2  garbage3
root@glen-laptop:~/work/test# mkdir /media/isoimage
root@glen-laptop:~/work/test# mount BACKUP.ISO /media/isoimage/ -t iso9660 -o loop
root@glen-laptop:~/work/test# ls /media/isoimage
backup.sh  build_ga  garba000  garbage1  garbage2
root@glen-laptop:~/work/test# ls -l /media/isoimage
total 5632
-r-xr-xr-x 1 root root     192 2008-09-20 17:29 backup.sh
-r-xr-xr-x 1 root root     513 2008-09-20 17:34 build_ga
-r-xr-xr-x 1 root root 1921464 2008-09-20 17:15 garbage1
-r-xr-xr-x 1 root root 1921464 2008-09-20 17:15 garbage2
-r-xr-xr-x 1 root root 1921464 2008-09-20 17:15 garbage3
-r-xr-xr-x 1 root root     895 2008-09-20 17:46 mount_ga
root@glen-laptop:~/work/test# 

Here's the run from crontab stuff
root@glen-laptop:~/work/test# cat runfromCRON

root@glen-laptop:~/work/test# date
Sat Sep 20 17:54:08 MDT 2008
root@glen-laptop:~/work/test# crontab -l
# m h  dom mon dow   command
00,05,10,15,20,25,30,35,40,45,50,55 * * * * 6 /root/work/test/backup.sh
03,08,13,18,23,28,33,38,43,48,53,58 * * * * 6 /root/back_wrapper.sh

root@glen-laptop:~/work/test# tail /var/log/syslog
Sep 20 18:03:01 glen-laptop /USR/SBIN/CRON[13247]: (root) CMD (6 /root/back_wrapper.sh)
Sep 20 18:05:01 glen-laptop /USR/SBIN/CRON[13312]: (root) CMD (6 /root/work/test/backup.sh)
Sep 20 18:05:06 glen-laptop dhclient: DHCPREQUEST of <null address> on wlan0 to 192.168.2.1 port 67
Sep 20 18:05:06 glen-laptop dhclient: DHCPACK of 192.168.2.108 from 192.168.2.1
Sep 20 18:05:06 glen-laptop dhclient: bound to 192.168.2.108 -- renewal in 236 seconds.
Sep 20 18:08:01 glen-laptop /USR/SBIN/CRON[13419]: (root) CMD (6 /root/back_wrapper.sh)
Sep 20 18:09:01 glen-laptop dhclient: DHCPREQUEST of <null address> on wlan0 to 192.168.2.1 port 67
Sep 20 18:09:02 glen-laptop dhclient: DHCPACK of 192.168.2.108 from 192.168.2.1
Sep 20 18:09:02 glen-laptop dhclient: bound to 192.168.2.108 -- renewal in 264 seconds.
Sep 20 18:10:01 glen-laptop /USR/SBIN/CRON[13493]: (root) CMD (6 /root/work/test/backup.sh)
root@glen-laptop:~/work/test# ls -l
total 11676
-rw-r--r-- 1 root root 6133760 2008-09-20 17:52 BACKUP.ISO
-rwxr-xr-x 1 root root     192 2008-09-20 17:29 backup.sh
-rw-r--r-- 1 root root     513 2008-09-20 17:34 build-garbage
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage1
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage2
-rw-r--r-- 1 root root 1921464 2008-09-20 17:15 garbage3
-rw-r--r-- 1 root root     842 2008-09-20 17:49 mount-garbage
-rw-r--r-- 1 root root     763 2008-09-20 17:53 runfromCLI
-rw-r--r-- 1 root root    1847 2008-09-20 17:58 runfromCRON
root@glen-laptop:~/work/test# 


So, .... what is going on and what do I need to do to get this to run from crontab?

---

### Post by spibou on 2008-09-20
[QUOTE=gtr@frii.com]and the iso file always fails when the size reaches about 140MBytes.[/quote]
What do you mean fails?

[QUOTE=gtr@frii.com]I've tried calling backup.sh from a wrapper bash shell in cron - it failed also.[/quote]
Modify the wrapper script so that it looks like this:
```

#........ your own code
echo Wrapper script started
touch $HOME/wrapper-script-started
backup.sh > errorfile 2>&1
echo Wrapper script finished
touch $HOME/wrapper-script-finished

```

Use a full path for errorfile and make sure that the files $HOME/wrapper-script-started and $HOME/wrapper-script-finished do not exist before doing your tests. Report the results.

---

### Post by unutbu on 2008-09-20
[email]gtr@frii.com[/email], remove one of the * from each of the crontab lines.
```

00,05,10,15,20,25,30,35,40,45,50,55 * * * * 6 /root/work/test/backup.sh
03,08,13,18,23,28,33,38,43,48,53,58 * * * * 6 /root/back_wrapper.sh
```

should be
```

00,05,10,15,20,25,30,35,40,45,50,55 * * * 6 /root/work/test/backup.sh
03,08,13,18,23,28,33,38,43,48,53,58 * * * 6 /root/back_wrapper.sh
```

The /var/log/syslog shows that the command being run is 

"6 /root/work/test/backup.sh"

when it should have been 

"/root/work/test/backup.sh"

---

### Post by gtr@frii.com on 2008-09-21
Thanks.  Darn - couldn't see the forrest for the trees.  Corrected the cron entry and it worked just fine.  Feeling foolish, but with a working backup from cron now thanks again.

Well, I thought it worked.  The command does run fine from crontab, but it builds messed up ISOs.  Burning the resulting iso usually succeeds, but then attempting to read from them results in an i/o read/write error.  This has been repeated on 3 systems, so it is not a specific hardware problem.
Testing things further I used scripts to build an iso in /tmp/backup with files copied into /tmp/backup utilizing either genisoimage or  mkisofs. The resulting ISO from the CLI was slightly bigger than the source, which made sense (~240M grew to~242M).  The script cleaned out /tmp/backup prior to copying source into it and running mkisofs.  When run from cron the scripts produced much smaller ISOs (~240M source became ~150M ISO).  I've tried calling mkisofs and/or genisoimage with nice -n -5 and get the same reults - 240M source to 242M ISO from CLI  and 240M source to 150M ISO from CRON.

Is there some magic parameters required when running from cron?, or is this a bug in genisoimage?

I have attached more details of the probelm I am having in the attached file

---

### Post by unutbu on 2008-09-22
Perhaps try changing your script to
```

genisoimage -input-charset UTF8 -o /root/work/test/BACKUP.ISO /root/work/test/ 1>&2 2>/root/work/genisoimage.out
```

This will send STDOUT and STDERR to /root/work/genisoimage.out. Then perhaps post it to see if we can spot the problem.

---

### Post by spibou on 2008-09-22
This will only redirect stderr, it should be **... 2> /root/work/genisoimage.out 1>&2**

---

### Post by gtr@frii.com on 2008-09-22
Thanks to both for the help - redirecting output fixed the problem when run from cron.  I changed the script to redirect 
2 > /root/work/genisoimage.out 1>&2

After that the script ran fine from both the CLI and from cron as shown in the attached file.  Just as an aside - is this something everyone learns through the school of hard knocks (and of course great help from the lists) or is there a readable reference for learning it an easier way.

---

### Post by spibou on 2008-09-22
Learn what? If you mean shell scripting there's a ton of books.

---

### Post by gtr@frii.com on 2008-09-24
Not shell scripting, per se.  My problem was with an outfile parameter for genisoimage.  My assumption was that the -o option opened a file other than standard out so it would be safe from crontab's redirection of  standard out to mail, or whatever.  Obviously (?) that assumption was wrong and crontab was interleaving standard out and standard error with the outfile data.
What I was asking was for was documentation / books that covered the handling of open file descriptors by cron.  In any case, thanks again for your help.  I now have a working interim backup (until the tape drive gets replaced) utilizing CDRs.

---

### Post by spibou on 2008-09-24
> **gtr@frii.com said:**
> Not shell scripting, per se.  My problem was with an outfile parameter for genisoimage.  My assumption was that the -o option opened a file other than standard out so it would be safe from crontab's redirection of  standard out to mail, or whatever.  Obviously (?) that assumption was wrong and crontab was interleaving standard out and standard error with the outfile data.
I've never used genisoimage but I just had a look at the man page and it looks as if your assumption is correct. I don't know why things didn't work out. I would recommend doing some experiments with **genisoimage -o file dir** where dir is some small directory and comparing the output of genisoimage when you run it from the command line and when you run it from crontab.

> What I was asking was for was documentation / books that covered the handling of open file descriptors by cron.
It is unlikely that such thing exists, you'd have to read the source. cron isn't meant to be doing anything fancy with file descriptors so I doubt that this is the source of your problems.

---

