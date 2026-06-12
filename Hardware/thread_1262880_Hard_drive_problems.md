---
title: "Hard drive problems"
date: 2009-09-10
forum: Hardware
---

### Post by martinrandau on 2009-09-10
Something has happened to my hard drive and I am unable to sort this myself using gparted's check file system function. It aborts after a few seconds with the following message (sorry for this being in html format but that is the format of the file that gparted gives me):

```
<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Transitional//EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd'>
<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='en-US' lang='en-US'>
<head>
<meta http-equiv='Content-Type' content='text/html;charset=utf-8' />
<title>GParted Details</title>
</head>
<body>
<p>GParted 0.4.3</p>
<p>Libparted 1.8.8</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Check and repair file system (fat32) on /dev/sdb1</b>&nbsp;&nbsp;00:00:11&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
calibrate /dev/sdb1&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sdb1<br />start: 63<br />end: 1953520064<br />size: 1953520002 (931.51 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
check file system on /dev/sdb1 for errors and (if possible) fix them&nbsp;&nbsp;00:00:06&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<b><i>dosfsck -a -w -v /dev/sdb1</i></b>
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>dosfsck 3.0.1 (23 Nov 2008)<br />dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN<br />Checking we can access the last sector of the filesystem<br />There are differences between boot sector and its backup.<br />Differences: (offset:original/backup)<br />  65:03/00, 67:9f/a4, 68:96/0d, 69:62/07, 70:5a/69<br />  Not automatically fixing this.<br />Boot sector contents:<br />System ID &quot;MSWIN4.1&quot;<br />Media byte 0xf8 (hard disk)<br />       512 bytes per logical sector<br />     32768 bytes per cluster<br />        38 reserved sectors<br />First FAT starts at byte 19456 (sector 38)<br />         2 FATs, 32 bit entries<br /> 122065408 bytes per FAT (= 238409 sectors)<br />Root directory start at cluster 2 (arbitrary size)<br />Data area starts at byte 244150272 (sector 476856)<br />  30516299 data clusters (999958085632 bytes)<br />63 sectors/track, 255 heads<br />        63 hidden sectors<br />1953519992 sectors total<br /></i>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
<i>Got 61436928 bytes instead of 122065204 at 19456<br /></i>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
grow file system to fill the partition&nbsp;&nbsp;00:00:05&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
using libparted
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
libparted messages&nbsp;&nbsp;&nbsp;&nbsp;( INFO )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>Input/output error during read on /dev/sdb</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
<p>========================================</p>
</body>
</html>
```

All kinds of help appreciated! :guitar:

---

### Post by tgalati4 on 2009-09-10
Boot a live CD, open a terminal.

Post the output of:

sudo fdisk -l

sudo fsck /dev/sdb1

---

### Post by martinrandau on 2009-09-11
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   82  Linux swap / Solaris
/dev/sda2             244       14593   115266375    5  Extended
/dev/sda5             244        1459     9767488+  83  Linux
/dev/sda6            1460       12295    87032137   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
```

```
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:03/00, 67:9f/a4, 68:96/0d, 69:62/07, 70:5a/69
1) Copy original to backup
2) Copy backup to original
3) No action
?
```

---

### Post by martinrandau on 2009-09-14
Any idea of what to make of this?

```
sudo fdisk /dev/sdb1

The number of cylinders for this disk is set to 121600.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Partition 3 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 3.
Partition 4 does not end on cylinder boundary.
Warning: partition 2 overlaps partition 4.
Warning: partition 3 overlaps partition 4.
Total allocated sectors 2464353615 greater than the maximum 1953520002

Command (m for help): 
```

---

