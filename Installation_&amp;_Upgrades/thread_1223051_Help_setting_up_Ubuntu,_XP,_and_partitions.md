---
title: "Help setting up Ubuntu, XP, and partitions"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2009-07-25
I have been using Ubuntu LiveCD for a while, and I am planning on a dual boot system. I have some questions about what I can and cannot do.

Here is my current system:

Dell XPS 410 with Intel Core 2 Duo 6600 processor, 4GB Memory, 250 GB WD hard drive as C:, 500GB WD hard drive as D:, Sony AW-Q160S DVD writer, TSSTcorp (Samsung) SH-S203B DVD writer, HP9800 Deskjet, HP 3570c Scanjet, Nikon Coolscan V ED, Creative SB Audigy audio card, an IEEE 1394 (Firewire ) card, along with system board USB ports, NVidia GeForce 7300 LE video, and audio.

My hard drives are formatted NTFS and are configured as:

Disk C: XP system files, Programs, Profiles, and some backup files from the D: drive.

Disk D: All my data (including MY Documents folder)

WD USB external hard drive (500GB) containing a complete copy of my D: drive.

Seagate USB external hard drive (500 GB) containing a backup of my C: drive.

I actively use Quicken, MySQL, Nikon Scan, Gimp, Audacity, OpenOffice, Firefox, Thunderbird, and Sunbird.  My activities consist of a lot of digital photography workflow, document  creation, music recording, and internet related activities.

I would like to install Ubuntu on my C: drive in a 100 GB partition, and I would like to make the D: drive my data drive for Ubuntu and XP.

Here are my questions.

(1) It is my understanding that Linux stores user data in /home/(username).  If this is true, can I make my entire D: drive a folder under /home/(username) that will be mounted automatically whenever I boot the PC?

(2) Will other software be loaded to /home/(username) without my knowledge (such as when I use Synaptic to install software)?

(3) Can I have my MySQL databases on the D: drive but running under Linux?

(4) If I later wish to change my D: drive to ext3/4, can I repartition the drive as such and copy my data from the WD USB drive without issues?

(5) Are there issues that I am totally ignoring out of ignorance?

---

### Post by jerrrys on 2009-07-25
#5  [https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

and good reading

[http://www.ubuntupocketguide.com/download_main.html]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by oldfred on 2009-07-25
I can offer my experience on some of your questions. 
1. Yes - I currently use 3 hard drives and mount FAT32 & NTFS directories as part of bootup in /etc/fstab. I originally shared a FAT32 partition to allow firefox and thunderbird to use the same directory in Windows & Ubuntu.  I used FAT 2-3 years ago as the NTFS driver was not yet reliable for writing It is now). I like having windows on one hard drive and Ubuntu on the other just in case. The third is new and I just loaded Ubuntu64 and a new data directory to store all the shared data. Windows will not read the Ext partitions (their is some software to do this but there are some questions on how good it is yet. 
2. Synaptic does not normally install software in your user directory. You can install software you download in your user directory but you do not (should not normally) have to.  Hidden configuration files per user are installed in your user directory. Some recommend separate partitions for /home but I like the recommendation of keeping home for the config files and having a separate partition for /data.
3. Do not know about mysql.
4. Copying data from one drive to another is easy. The ext partition will not work for windows.
5.I am only using windows (now about 10% of time) for Quicken. GnuCash or KmyMoney seem to be ok if all you want is a checkbook. They are not the same as Quicken and are not quite as easy to use. Have you tested everything under the liveCD? Most issues can be resolved once installed

Others can chime in on mysql and other issues. As you install and have questions we are here to help you. Most of the common questions are already answered in various threads. Welcome to Ubuntu.

---

