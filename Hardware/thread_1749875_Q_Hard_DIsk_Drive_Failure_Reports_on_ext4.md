---
title: "Q: Hard DIsk Drive Failure Reports on ext4"
date: 2011-05-05
forum: Hardware
---

### Post by GuiGuy on 2011-05-05
**[COLOR="Red"]Warning: Long...[/COLOR]**

A question for hard disk experts if we have any around here;

I have 2T Western Digital HDD I bought new about 6 months ago. I bought three from the same batch. The HDD was formatted as ext4 

About two weeks ago SMART reported the disk as being close to failure. In Linux there were problems mounting the disk. The DiskManager constantly threw up dialogs warning of impending doom  and that I should back up and replace the device.

I have replaced the faulty HDD and yesterday was wondering what do with. Take it back under its warranty, play with it etc etc.?

Anyway, last night I plugged it into an eSATA docking station on my Win7 notebook. SMART reported the HDD as OK. Windows Disk Manager also reported it as healthy, but unknown file format (ext4). I reformatted it to NTFS and all seemed well.

I  plugged the eSATA dock into the Linux box where the HDD had originally been installed. No problems. DIskManager reported the NTFS format and indicated the HDD as Healthy. 

I then reformatted the drive to ext4. Initially there were no problems until I rebooted. The HDD was reported as subject to imminent hardware failure. I plugged the eSATA dock into another ubuntu based PC and got the same warnings. 

Back to the Windows7 notebook and repeated the above exercise. 

**It is demonstrable that when formatted as NTFS both Linux and Windows 7 PCs report the HDD as healthy. When formatted to ext4, linux PCs give warnings of imminent hardware failure. WIn7 indicates the drive is healthy. **

I'm obviously going to treat the HDD as suspect, but was wondering if anyone can shed light on the contradictory results, particularly why Linux would regard the HDD as faulty when formatted as ext4 and healthy when formatted as NTFS.

Cheers.

---

