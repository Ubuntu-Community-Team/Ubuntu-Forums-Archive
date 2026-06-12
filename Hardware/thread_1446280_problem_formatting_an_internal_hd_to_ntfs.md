---
title: "problem formatting an internal hd to ntfs"
date: 2010-04-03
forum: Hardware
---

### Post by pirlo89 on 2010-04-03
hi,

i have an internal hd 500 gb. and i also have partitioned it into about 197 gb of type fat32 (to use as a shared partition between windows 7 and ubuntu 9.10). but when i try to format it using gparted an error occurs .

```
<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Transitional//EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd'>
<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='en-US' lang='en-US'>
<head>
<meta http-equiv='Content-Type' content='text/html;charset=utf-8' />
<title>GParted Details</title>
</head>
<body>
<p>GParted 0.4.5</p>
<p>Libparted 1.8.8.1.159-1e0e</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Format /dev/sda5 as ntfs</b>&nbsp;&nbsp;00:00:02&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
calibrate /dev/sda5&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda5<br />start: 143572905<br />end: 557600084<br />size: 414027180 (197.42 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
set partition type on /dev/sda5&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>new partition type: ntfs</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
create new ntfs file system&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<b><i>mkntfs -Q -v -L &quot;&quot; /dev/sda5</i></b>
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>The device doesn&apos;t exist; did you specify it correctly?<br /></i>
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
libparted messages&nbsp;&nbsp;&nbsp;&nbsp;( INFO )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy.  This means Linux won&apos;t know about any changes you made to /dev/sda5 until you reboot -- so you shouldn&apos;t mount it or use it in any way before rebooting.</i>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
<i>The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy).  This means Linux won&apos;t know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/sda.</i>
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
```this is the error html file. Does anyone have a solution ?

---

### Post by efflandt on 2010-04-03
The error sounds like you are trying to format a mounted partition.  Make sure that it is NOT mounted.  Are you trying to partition it as FAT32 (like you said) or as ntfs (per the error)?

It might be best to partition ntfs from Windows (to make sure it is compatible).

If you are trying to resize any partitions you are actually using, do that by booting from CD or USB instead.

---

### Post by pirlo89 on 2010-04-04
Thanks, i formatted from within windows to ntfs. I couldn't do that before because windows did not recognize the partition. But for some reason after the error windows recognized it as fat32.

Anyway, problem solved. Thanks for your help ;).

---

