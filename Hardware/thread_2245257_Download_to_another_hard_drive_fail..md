---
title: "Download to another hard drive fail."
date: 2014-09-22
forum: Hardware
---

### Post by Chase_Preuninger on 2014-09-22
I currently have Ubuntu installed on a 120GB SSD.  In my computer I have a 1TB mechanicle drive which I have mounted under media/Storage (NTFS partition).  I want to use it to download my torrents to this drive instead of an SSD.  I use qBittorrent and whenever I start a download I get an "Error permission denied".  I also had this prolbem with transmission torrent client.  None of my other programs seem to have any prolbem writing to the Storage drive, I use it to save my firefox downloads.  Also I have windows installed on this machine as well and it's torrent clients have no prolbem writing to this partition.  Any ideas?

---

### Post by yancek on 2014-09-22
The "permission denied" error is pretty explicit, you need to change the permissions from within Ubuntu.  If the drive in question is accessible under /media/Storage, open a terminal in Ubuntu and run the following command: ls -ld /media/Storage
This will show the permissions as well as owner:group so someone can explain how to change.

> Also I have windows installed on this machine as well and it's torrent clients have no prolbem writing to this partition.

Not sure why you are surprised that from a windows operating system you are writing files to a windows partition with a windows filesystem and it works.  Not sure what other "programs" you are referring to?

---

