---
title: "ext3 journal problems"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by Hellaxe on 2007-06-10
Hello people:

i'm having some problems with my /home partition.
From nowere it start having problems and errors and the system makes the file system "read-only".
After making the fsck to /home it's ok but sometime after it goes read-only again.

I'm kind of lost on this one because i didn't do anyting wrong to /home.

My suspition is to amule that someway did broke something in the /home and that the incomeing directory is in another partion in the same disk.

Or the new kernel 2.6.17.11 -generic that i upgraded recently (Yes still in Edgy - lack of time to upgrade).

Could someone give me a clue about this.
Thanks.

EDIT:

this is what i get from dmesg:
```
[17181882.624000] journal_bmap: journal block not found at offset 4108 on hda4
[17181882.624000] Aborting journal on device hda4.
[17181882.748000] ext3_abort called.
[17181882.748000] EXT3-fs error (device hda4): ext3_journal_start_sb: Detected aborted journal
[17181882.748000] Remounting filesystem read-only

```

---

### Post by taurus on 2007-06-10
Do you have a separate /home partition?  Can you post the output of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Hellaxe on 2007-06-10
Yes my /home partition is separated.

Here is the fdisk report:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2551    20490876    7  HPFS/NTFS
/dev/sda2            2552       27614   201318547+   c  W95 FAT32 (LBA)
/dev/sda3           27615       38913    90759217+  1c  Hidden W95 FAT32 (LBA)

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       16907   135805446    c  W95 FAT32 (LBA)
/dev/hda2   *       16908       17636     5855692+  83  Linux
/dev/hda3           17637       17758      979965   82  Linux swap / Solaris
/dev/hda4           17759       19457    13647217+  83  Linux

```

Now the fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=6a3644d4-1112-4029-a435-f52a282722d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=63b24dfc-82ed-4394-8f9a-561d03344845 /home           ext3    defaults        0       2
# /dev/hda1
UUID=3FEC-06C1  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
#UUID=06F82CC3F82CB2BB /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=457A-B9D7  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=8AF5-73B2  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=05e6e704-b455-4ba2-8d8c-4dcf9f09682a none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

now the df:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             5.5G  3.7G  1.6G  71% /
varrun               1014M  132K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
/dev/hda4              13G  5.9G  6.4G  48% /home
/dev/hda1             130G  104G   26G  81% /media/hda1
/dev/sda2             192G  119G   74G  62% /media/sda2
/dev/sda3              87G   24G   64G  27% /media/sda3

```

As you see there is no problem with space. It simple freaks out but i can't understand why.
thanks

---

### Post by taurus on 2007-06-10
What's the output of this command then?  

```
ls -la ~
```
(Don't include stuff that you don't want everybody to see.)

---

### Post by H3g3m0n on 2007-06-10
Filesharing programs can cause filesystem corruption as they are fairly intensive, Azureus is a good test of filesystems and harddrives, I've had it 3 or so.

Try a more thorough scan for badblocks:
sudo fsck -ccvvfy -C - /dev/yourpartition

Make sure that your not powering off the computer without shutting it down correctly.

If the problem still persists, try using emule on another partition/drive and see if that causes the same problems.

You might also have a dying harddrive. Try using smartmontools, it can read information that most modern harddrives log about performance errors and get them conduct self tests, all of my failing harddrives have failed the tests so its a good indication.

For instance my failing secondary harddrive:
```
`--> sudo smartctl -d ata -H /dev/sdb
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
Failed Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   139   139   140    Pre-fail  Always   FAILING_NOW 962

.-(~)------------------------------------------------------------------------------------------------------------------(hegemon@ender)-
`--> sudo smartctl -d ata /dev/sdb -l selftest
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%       770         4294705152
# 2  Conveyance offline  Completed: unknown failure    90%       628         4294705152
# 3  Extended offline    Completed: unknown failure    90%       626         4294705152
# 4  Short offline       Completed: unknown failure    90%       505         4294705152
# 5  Extended offline    Completed: unknown failure    90%      1023         4294705152
# 6  Short offline       Completed: unknown failure    90%      1023         4294705152
# 7  Short offline       Completed: unknown failure    90%      1023         4294705152

.-(~)------------------------------------------------------------------------------------------------------------------(hegemon@ender)-
`--> 
```

My working primary:
```
.-(~)------------------------------------------------------------------------------------------------------------------(hegemon@ender)-
`--> sudo smartctl -d ata /dev/sda -l selftest
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     22138         -
# 2  Short offline       Completed without error       00%     18901         -

.-(~)------------------------------------------------------------------------------------------------------------------(hegemon@ender)-
`--> sudo smartctl -d ata -H /dev/sda         
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
.-(~)--------------------------------------------------------
```

I think it would be great if Ubuntu did SMART testing automatically in the background by default, and alerted the user when it starts to fail.

---

### Post by Hellaxe on 2007-06-10
@ taurus:

I don't see that relevant but here it is:
```
0 -rw-r--r--  1 root root         0 2007-03-19 10:54 1
     4 drwx------  2 axe  axe       4096 2007-03-27 17:14 amsn_received
     4 -rw-r--r--  1 axe  axe        227 2006-09-13 10:03 automatix.log
   312 -rw-r--r--  1 axe  axe     313317 2007-04-17 11:54 axe_lena.JPG
     4 -rw-r--r--  1 axe  axe        231 2006-12-24 15:29 axeprimeiro.k3b
     4 drwxr-xr-x  8 axe  axe       4096 2006-12-20 19:06 Backup
    24 -rwxrwxrwx  1 axe  axe      22585 2006-10-10 09:08 contactos.CSV
  1696 -rw-rw-r--  1 axe  axe    1731549 2007-04-29 22:32 cpcdi_toshiba.jpeg
     4 drwxr-xr-x  2 axe  axe       4096 2006-12-21 22:26 Desktop
     4 drwxr-xr-x 14 axe  axe       4096 2007-03-21 10:04 Docs
     8 drwxr-xr-x  4 axe  axe       8192 2007-06-07 16:55 downloads
     4 drwxr-xr-x  2 axe  axe       4096 2006-12-25 12:22 dvdrip-data
     0 lrwxrwxrwx  1 axe  axe         26 2006-09-12 12:51 Examples -> /usr/share/example-content
     0 lrwxrwxrwx  1 axe  axe         35 2007-03-19 10:54 googleearth -> /home/axe/google-earth//googleearth
     4 drwxr-xr-x  9 axe  axe       4096 2007-03-19 13:50 google-earth
 21132 -rwxr-xr-x  1 axe  axe   21607408 2007-03-15 13:44 GoogleEarthLinux.bin
     4 drwxr-xr-x  5 axe  axe       4096 2006-11-06 11:21 icons_themes
     4 drwxr-----  2 axe  axe       4096 2006-09-12 15:09 Incoming
    36 -rw-r--r--  1 axe  axe      33686 2006-08-05 20:29 jriddell.key
     0 -rw-rw----  1 axe  axe          0 2006-12-21 23:40 lixo1.txt
     4 -rwxr-xr-x  1 axe  axe        101 2006-09-14 15:39 mouse
  1016 -rw-r--r--  1 axe  axe    1032776 2007-02-26 18:39 Movie.wm
     4 drwxr-xr-x  2 axe  axe       4096 2007-01-28 14:22 Musica
     4 drwx------  2 axe  axe       4096 2006-11-06 10:21 MyDownloads
     4 drwxr-xr-x  2 axe  axe       4096 2007-04-24 11:38 OUTROS
     0 -rw-r--r--  1 axe  axe          0 2006-10-29 19:16 out.txt
    16 -rw-r--r--  1 axe  axe      12877 2007-05-26 12:39 parabens_1.jpg
    20 -rw-r--r--  1 axe  axe      16576 2007-05-26 12:43 parabens.jpg
     4 drwx------  2 axe  axe       4096 2007-06-06 11:25 PDF
     8 -rw-r--r--  1 axe  axe       6106 2007-06-06 12:33 PES_dicas.txt
     4 drwxr-xr-x  2 axe  axe       4096 2006-12-10 15:26 Podcasts
     4 -rw-r--r--  1 axe  axe       1787 2006-08-05 20:36 quinn1.key
     4 -rw-r--r--  1 axe  axe       1690 2006-08-05 20:37 quinn2.key
   276 -rw-r--r--  1 axe  axe     277240 2007-04-14 16:04 sapo_erro.png
     4 -rw-r--r--  1 axe  axe        810 2006-10-03 10:38 sign1.html
     4 drwxr-xr-x 16 axe  axe       4096 2007-04-23 11:54 Software
     4 drwxr-xr-x 11 axe  axe       4096 2007-03-27 13:01 Temp
     4 drwxr-xr-x  7 axe  axe       4096 2007-01-28 17:49 Trabalho
     4 -rw-r--r--  1 axe  axe       1704 2006-09-28 22:04 tseliot.asc
     4 -rw-r--r--  1 axe  axe       1704 2006-09-28 22:04 tseliot.asc.1
  8244 -rwxrwx---  1 axe  axe    8425801 2007-05-23 14:48 Unlock Nokia 3510,3510I,6100,6200,6310,6310I,6510,6590,7210,7650,8310,8390 Remove Simlock By Code.zip
     4 drwxr-xr-x  2 root root      4096 2006-10-24 08:28 virtualmachines
     4 drwxrwxrwt  2 axe  axe       4096 2007-06-04 14:17 vmware
     4 -rw-r--r--  1 axe  axe       2328 2006-12-25 12:32 XUTOS_E_PONTAPES.log
560284 -rw-r--r--  1 axe  axe  573165501 2007-06-10 11:37 ziZf4W8L

```

@h3g3nom

Now i'm not running amule but i've thinked in changed that directory to the other hard drive.
i'll try later the smartmonttools
i don't have it installed

---

### Post by Hellaxe on 2007-06-11
hello everyone, help me out on this one.

---

### Post by Hellaxe on 2007-06-12
Yesterday i've made the options that **h3g3nom** gave and it discovered 4 logical block errors.
I think it fixed all of them because i was away from the computer and i saw that info on the report.

The strange thing is that i start the system it corrects the error and them 15 minutes or so the problems started from nowhere.
 
I tested with even with no programs opened and the result is the same.

---

