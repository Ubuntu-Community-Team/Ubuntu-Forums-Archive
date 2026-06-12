---
title: "Problem with undeleting files from FAT32 external hard disk"
date: 2009-07-28
forum: Hardware
---

### Post by equusaustralus on 2009-07-28
Hi, 

I've been wrestling for several days now with missing files from an external WD 500gb USB hard disk. Basically, I noticed that around half of the directories on the disk were empty, though the directories themselves were there. There was no possible way for their contents to have been accidentally deleted. 

It registered 170gb out of a total of 465 gb. I moved all of the files to another drive, so now it shows 170gb free. Gparted however shows that there is another 280gb used.

So, I suspected it was a problem with the partition tables. I used TestDisk, which found that the boot sector and backup boot sector were ok, but were not identical. Tried rebuilding the boot sector from the backup, so now they're both ok and identical. The attempt to repair the FAT came back with a message that everything was OK with it. 

Next, I tried undeleting all of the files to a separate drive. It manages around 20-30gb, then something weird happens. It starts all over again with the same files it just undeleted, and places them in a sub-directory of one of the freshly-undeleted directories... not sure if this makes sense.:confused:

Here's a part of the file readout TestDisk gives:

 1 P FAT32 LBA                0   1  1 60799 254 63  976751937 [ELEMENTS]
Directory /
                                                   Previous
drwxr-xr-x     0     0         0 11-May-2009 08:29 Tot_samiy_Munhgauzen
-rwxr-xr-x     0     0   1172283392 16-Jun-2008 21:49 Brilliantovaja ruka.avi
drwxr-xr-x     0     0         0 11-May-2009 08:28 Nuit et Brouillard - Night And Fog
-rwxr-xr-x     0     0   695441552 25-Jul-2008 10:03 Germany Year Zero (Roberto Rossellini).avi
drwxr-xr-x     0     0     32768  3-Jul-2008 03:37 _PSP_A~1
drwxr-xr-x     0     0         0  3-Jul-2008 03:37 Delirious
-rwxr-xr-x     0     0   735408128  3-Jul-2008 06:10 Jesus Camp (2006).avi
-rwxr-xr-x     0     0   734427136 24-Jul-2008 17:03 The Rules of the Game (1939).avi
-rwxr-xr-x     0     0     73839 31-May-2009 04:09 Baby Of Macon

So, should I reconcile myself with the partial data loss or is there something more I can do? I would at least like to have the use of the full hard disk. Also, if I succeed in repairing the tables, is the disk reliable for storage?

Any help would be much appreciated!

---

