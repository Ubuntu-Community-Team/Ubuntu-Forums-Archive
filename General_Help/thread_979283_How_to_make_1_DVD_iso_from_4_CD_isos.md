---
title: "How to make 1 DVD iso from 4 CD isos?"
date: 2008-11-11
forum: General Help
---

### Post by zeiz on 2008-11-11
I really don't know where to place this question :confused:

I have very simple BSD script that makes 1 bootable DVD from 4 (or whatever) CDs where 1st is bootable. Unfortunately it doesn't work in Ubuntu (I guess Linux). I can extract all the CD's isos to a folder and then create 1 DVD but I'm not sure it's the same because it asks "insert Disk2... etc.
Is there specific Ubuntu/Linux solution to create 1 DVD from n CDs?

---

### Post by ohzopants on 2008-11-12
What utilities was your BSD script using?  There might be linux ports or analogues available.

I am curious about the solution to this, it's a very interesting question.

---

### Post by caljohnsmith on 2008-11-12
How about posting your BSD script for making a DVD, and maybe we can help you figure out what the equivalent would be in Linux.

---

### Post by zeiz on 2008-11-12
This script I used to make a DVD from 4 FreeBSD CDs: otherwise it pain in the *** to change disks repeatedly. But I played too much with that partition and finally broke OS so I don't have BSD partition now. The script worked problem free there and it refused to work under Intrepid. Here it is (edited under new beta):

#!/bin/sh

# extracting all ISOs for creating 1 DVD ISO
# set path to my ISO's
cd1="/home/ubUser/ISO/7.1-BETA2-amd64-disc1.iso"
cd2="/home/ubUser/ISO/7.1-BETA2-amd64-disc2.iso"
cd3="/home/ubUser/ISO/7.1-BETA2-amd64-disc3.iso"
cd4="/home/ubUser/ISO/7.1-BETA2-amd64-disc4.iso

# extracting all from archive
#echo "Extracting disc $cd4"
tar -xf $cd4 -C /home/ubUser/ISO/all
#echo "Extracting disc $cd3"
tar -xf $cd3 -C /home/ubUser/ISO/all
#echo "Extracting disc $cd2"
tar -xf $cd2 -C /home/ubUser/ISO/all
#echo "Extracting disc $cd1"
tar -xf $cd1 -C /home/ubUser/ISO/all

# changing INDEX
#echo "Changing INDEX"
sed -ie 's/|2/|1/g' /home/ubUser/ISO/all/packages/INDEX
sed -ie 's/|3/|1/g' /home/ubUser/ISO/all/packages/INDEX
sed -ie 's/|4/|1/g' /home/ubUser/ISO/all/packages/INDEX

rm -Rf /home/ubUser/ISO/all/rr_moved

# creating dvd-iso
mkisofs -v -J -R -no-emul-boot -b boot/cdboot -o /home/ubUser/tmp/7.1-BETA2-amd64-dvd.iso /home/ubUser/ISO/all

It's interesting that all the commands work in Linux but entire script fails. Maybe a typo?

---

### Post by caljohnsmith on 2008-11-13
How about adding the following right after the shebang:
```
#!/bin/sh
[COLOR="Blue"]set -x[/COLOR]
```
Then rerun your script in the terminal, and it should show each command as it is executed; you should be able to see which command it hangs on or returns an error. How about posting the output so we can see.

---

### Post by zeiz on 2008-11-13
First I got: ".....directory too deep... (7) 6-max.
I removed (commented out) cd4(docs) where too deep directories were found from work. The result:

ubUser@host:~$ sh /home/ubUser/ISO/cd2dvd
+ cd1=/home/ubUser/ISO/7.1-BETA2-amd64-disc1.iso
+ cd2=/home/ubUser/ISO/7.1-BETA2-amd64-disc2.iso
+ cd3=/home/ubUser/ISO/7.1-BETA2-amd64-disc3.iso
/home/ubUser/ISO/cd2dvd: 22: Syntax error: Unterminated quoted string
ubUser@host:~$

I removed quotes from lines with commands. The result:

ubUser@host:~$ cd ~/ISO
ubUser@host:~/ISO$ sh cd2dvd
+ cd1=/home/ubUser/ISO/7.1-BETA2-amd64-disc1.iso
+ cd2=/home/ubUser/ISO/7.1-BETA2-amd64-disc2.iso
+ cd3=/home/ubUser/ISO/7.1-BETA2-amd64-disc3.iso
+ echo Extracting disc /home/ubUser/ISO/7.1-BETA2-amd64-disc3.iso
Extracting disc /home/ubUser/ISO/7.1-BETA2-amd64-disc3.iso
+ tar -xf /home/ubUser/ISO/7.1-BETA2-amd64-disc3.iso -C /home/ubUser/ISO/all
+ echo Extracting disc /home/ubUser/ISO/7.1-BETA2-amd64-disc2.iso
Extracting disc /home/ubUser/ISO/7.1-BETA2-amd64-disc2.iso
+ tar -xf /home/ubUser/ISO/7.1-BETA2-amd64-disc2.iso -C /home/ubUser/ISO/all
+ echo Extracting disc /home/ubUser/ISO/7.1-BETA2-amd64-disc1.iso
Extracting disc /home/ubUser/ISO/7.1-BETA2-amd64-disc1.iso
+ tar -xf /home/ubUser/ISO/7.1-BETA2-amd64-disc1.iso -C /home/ubUser/ISO/all
+ sed -ie s/|2/|1/g /home/ubUser/ISO/all/packages/INDEX
sed: can't read /home/ubUser/ISO/all/packages/INDEX: No such file or directory
+ sed -ie s/|3/|1/g /home/ubUser/ISO/all/packages/INDEX
sed: can't read /home/ubUser/ISO/all/packages/INDEX: No such file or directory
+ rm -Rf /home/ubUser/ISO/all/rr_moved
+ echo Creating DVD-iso
Creating DVD-iso
+ mkisofs -v -J -R -no-emul-boot -b boot/cdboot -o /home/ubUser/tmp/7.1-BETA2-amd64-dvd.iso /home/ubUser/ISO/all
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.8 (Linux)
Scanning /home/ubUser/ISO/all
Writing:   Initial Padblock                        Start Block 0
Done with: Initial Padblock                        Block(s)    16
Writing:   Primary Volume Descriptor               Start Block 16
Done with: Primary Volume Descriptor               Block(s)    1
Writing:   Eltorito Volume Descriptor              Start Block 17
genisoimage: Uh oh, I cant find the boot image 'boot/cdboot' !
ubUser@host:~/ISO$ 

Now what? :)

PS: all commands are "colored" now in the script except mkisofs - this one is black and not in bold. ??

PPS> gosh, it's not right place but, CALJOHNSMITH, I found your post with grub related help. My case: dual boot XP/Ubuntu. XP installed first then Ubuntu (worked fine). Then freeBSD...its loader obviously replaced grub on mbr. then I shrinked hd0,0 (XP) from 50 to 30GB and grew ubuntu partition to free space. then I did: grub>find /boot/grub/stage1...grub> hd0,5 ... grub>root (hd0,5)... grub>setup (hd0,0). Result: grub appeared and it's booting Ubuntu but not XP whatever I do with menu.lst. I assume: previous partition table is in grub config files (map, stageX, etc). How to get XP boot without reinstalling Intrepid?

---

### Post by krisik28 on 2008-11-13
Hi ,
I've the same problem like zeiz .
I changed his script , adapt to my patch and added 
```
#!/bin/sh
set -x
```
now it's looks like that :
```
#!/bin/sh
set -x

# extracting all ISOs for creating 1 DVD ISO
# set path to my ISO's
cd1="/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc1.iso"
cd2="/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc2.iso"
cd3="/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc3.iso"
cd4="/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-docs.iso"

# extracting all from archive
#echo "Extracting disc $cd4"
tar -xf $cd4 -C /home/abqate/Pulpit/freebsd
#echo "Extracting disc $cd3"
tar -xf $cd3 -C /home/abqate/Pulpit/freebsd
#echo "Extracting disc $cd2"
tar -xf $cd2 -C /home/abqate/Pulpit/freebsd
#echo "Extracting disc $cd1"
tar -xf $cd1 -C /home/abqate/Pulpit/freebsd

# changing INDEX
#echo "Changing INDEX"
sed -ie 's/|2/|1/g' /home/abqate/Pulpit/freebsd/packages/INDEX
sed -ie 's/|3/|1/g' /home/abqate/Pulpit/freebsd/packages/INDEX
sed -ie 's/|4/|1/g' /home/abqate/Pulpit/freebsd/packages/INDEX

rm -Rf /home/abqate/Pulpit/freebs/rr_moved

# creating dvd-iso
mkisofs -v -J -R -no-emul-boot -b boot/cdboot -o /home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-DVD.iso /home/abqate/Pulpit/freebsd
```
and unfortunately it doesn't work .
This I got from terminal :
```

abqate-desktop% '/home/abqate/Pulpit/freebsd/scalanie.sh' 
+ cd1=/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc1.iso
+ cd2=/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc2.iso
+ cd3=/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc3.iso
+ cd4=/home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-docs.iso
+ tar -xf /home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-docs.iso -C /home/abqate/Pulpit/freebsd
+ tar -xf /home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc3.iso -C /home/abqate/Pulpit/freebsd
+ tar -xf /home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc2.iso -C /home/abqate/Pulpit/freebsd
+ tar -xf /home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-disc1.iso -C /home/abqate/Pulpit/freebsd
+ sed -ie s/|2/|1/g /home/abqate/Pulpit/freebsd/packages/INDEX
sed: nie mo&#380;na odczyta&#263; /home/abqate/Pulpit/freebsd/packages/INDEX: No such file or directory
+ sed -ie s/|3/|1/g /home/abqate/Pulpit/freebsd/packages/INDEX
sed: nie mo&#380;na odczyta&#263; /home/abqate/Pulpit/freebsd/packages/INDEX: No such file or directory
+ sed -ie s/|4/|1/g /home/abqate/Pulpit/freebsd/packages/INDEX
sed: nie mo&#380;na odczyta&#263; /home/abqate/Pulpit/freebsd/packages/INDEX: No such file or directory
+ rm -Rf /home/abqate/Pulpit/freebs/rr_moved
+ mkisofs -v -J -R -no-emul-boot -b boot/cdboot -o /home/abqate/Pulpit/freebsd/7.0-RELEASE-i386-DVD.iso /home/abqate/Pulpit/freebsd
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.6 (Linux)
Scanning /home/abqate/Pulpit/freebsd
Using 7_0_R000.ISO;1 for  /7.0-RELEASE-i386-docs.iso (7.0-RELEASE-i386-disc3.iso)
Using 7_0_R001.ISO;1 for  /7.0-RELEASE-i386-disc3.iso (7.0-RELEASE-i386-disc1.iso)
Using 7_0_R002.ISO;1 for  /7.0-RELEASE-i386-disc1.iso (7.0-RELEASE-i386-disc2.iso)
Writing:   Initial Padblock                        Start Block 0
Done with: Initial Padblock                        Block(s)    16
Writing:   Primary Volume Descriptor               Start Block 16
Done with: Primary Volume Descriptor               Block(s)    1
Writing:   Eltorito Volume Descriptor              Start Block 17
genisoimage: Uh oh, I cant find the boot image 'boot/cdboot' !

```
What can I do to make it work ?
Regards krisik28

---

### Post by caljohnsmith on 2008-11-13
Well besides sed not finding those INDEX files, it looks like the main reason the script doesn't work is:> 
genisoimage: Uh oh, I cant find the boot image 'boot/cdboot'
The original command is:
```
mkisofs -v -J -R -no-emul-boot [COLOR="Blue"]-b boot/cdboot[/COLOR] -o /home/ubUser/tmp/7.1-BETA2-amd64-dvd.iso /home/ubUser/ISO/all
```
And according to the mkisofs help screen:
> -b FILE, -eltorito-boot FILE
Set El Torito boot image name
So the "boot/cdboot" is supposed to be an El Torito boot image (El Torito boot files specifically have to do with booting CDs/DVDs). So I'm not sure where the original script was getting those files, but maybe that will lead you to find a solution.

---

### Post by zeiz on 2008-11-13
Instead of ](*,) I did all with hands :oops: (unzip, merge etc, but "sed" - in terminal) and installed fbsd-7.1-beta2 without docs. Success. But the script doesn't work there too :shock:
The script was of Russian origin and possibly worked not on native fbsd that I'm trying to adopt (KDE4.1 already OK!) but on Russian TrueBDS ([www.truebsd.org](www.truebsd.org)) based on fbsd:KS.

I've sent this before I receive info about El Torito. So thanks again, calijohnsmith! But how did you get the output you quoted?

---

### Post by zeiz on 2008-11-18
Not the end of the story yet! 
I decided to come back to i386 (no benefits for x64 only troubles) but now I needed dvd-iso again and I decided to try the script again and I edited it:
1. removed -b boot/cdboot - no success.
2. changed the above to -b boot.catalog -no success.
3. changed no-emul-boot to eltorito-boot - no success.

Every time I saw lots of errors and what I actually realized that tar doesn't extract files from cd-isos. I don't know why but it's the easiest to extract the isos with Arch and put them in my folder "all" starting from #3 and finishing with #1 tapping "yes" to merge and replacing. I did that and executed the script (edited to origin) again without any hope (very last time!) But o, mirracle! It worked and I was given a)very long output without any "uh, oh" at the end and b)the iso! It's installing right now after successful boot.
I have no idea what happened but may be it will be usefull for somebody.
As well as this: [http://odin.himinbi.org/xp_cds/eltorito_extraction.html](http://odin.himinbi.org/xp_cds/eltorito_extraction.html)

PS. I cannot see how to attach a file so just the end of very long output:
...........................................
 98.67% done, estimate finish Tue Nov 18 22:41:09 2008
 99.33% done, estimate finish Tue Nov 18 22:41:09 2008
Total translation table size: 2048
Total rockridge attributes bytes: 253761
Total directory bytes: 487424
Path table size(bytes): 1078
Done with: The File(s)                             Block(s)    759567
Writing:   Ending Padblock                         Start Block 759983
Done with: Ending Padblock                         Block(s)    150
Max brk space used 1ce000
760133 extents written (1484 MB)
ubUser@host:~/Desktop$

---

