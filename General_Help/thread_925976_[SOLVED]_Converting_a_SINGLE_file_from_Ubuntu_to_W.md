---
title: "[SOLVED] Converting a SINGLE file from Ubuntu to Windows"
date: 2008-09-21
forum: General Help
---

### Post by Doc Hoss on 2008-09-21
I'm dual booting Ubuntu and Windows XP (on one drive), and I have another drive that I just dump data (movies, music, backup files, etc) on.  I downloaded a file to my Linux install then copied it to  the data drive (data drive and Windows partition are formatted as NTFS, Ubuntu as ext3), but Windows can't see it when I look in the directory.  Under Ubuntu, I can see and access the file fine.  

I'd rather not have to download this file again, as it's pretty hefty and would take a while.  Plus I'd like to know how to solve this.  Any ideas?

---

### Post by HermanAB on 2008-09-21
You have to run the Windows disk check and repair utility from within Windows.  That should fix it.

I avoid these issues by running Windows in VMware on Linux.  Then I transfer files using FTP or SFTP.  That way, each OS access its own  file systems and nothing gets lost in the translation.

Cheers,

Herman

---

### Post by hardyn on 2008-09-21
or run a fat32 "arbitration" partition.

---

### Post by Doc Hoss on 2009-01-10
Problem solved.  Both your suggestions were great.  Thanks!

---

### Post by Sherlock Holmes on 2009-01-10
i know this is late, but how about fs-driver?

---

### Post by Doc Hoss on 2009-01-11
Actually, I haven't had problems with transferring a single file (or directory) to a NTFS partition and having it be recognized by Windows in quite a while...I think I may have gotten ntfs-3g set up since I first posted this?

What is fs-driver, anyway?  I'd like to know more.

---

