---
title: "Mounting hard drives on Dell to save data"
date: 2008-10-29
forum: Hardware
---

### Post by PopnPaul on 2008-10-29
My boss owned her computers. The logon process has failed in windows so I'm going to try to log on to live ubuntu (latest version) and mount the hard drive. Then grab an external hard drive and back up all that data. I need to do this tomorrow so email me at [email]boguslavskiy@gmail.com[/email] if you want, or just reply here. Anyway so the plan is:

Log on to Ubuntu Live CD
Mount the hard drive
Plug in external hard drive
Backup the data
Win

How would I go about mounting the hard drive? I never really used ubuntu all that much because the P35 chipset is not compatible with the current linux kernel. Also will ubuntu instantly recoginize the external hard drive? 

Thanks a lot in advance.

---

### Post by logos34 on 2008-10-30
Has she tried to boot into failsafe mode (press F8 at startup)?  Worth a shot...if successful maybe doing error checking will fix the problem).

To mount the partition from the ubuntu live cd just click on it in nautilus file browser (left pane).  Or  from the terminal:

sudo mkdir /media/windows

sudo mount -t ntfs /dev/sda? /media/windows -o force

---

