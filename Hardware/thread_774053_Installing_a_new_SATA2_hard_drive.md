---
title: "Installing a new SATA2 hard drive"
date: 2008-04-29
forum: Hardware
---

### Post by couzin2000 on 2008-04-29
I just bought a new Seagate 500Gb (7200.11) SATA2 HD. I have a working machine that has 2 similar HDs (7200.10) and a Pioneer DVD-RW (SATA2). I have Ubuntu Gutsy installed with latest updates.

I went in, turned off the power, connected the drive properly, turned on the machine. After a few minutes of looking around, I finally found the info telling me to install Gnome Partintion Editor (gparted), so I installed it from Add/Remove. Works fine. Gparted scans the pc, finds the new drive, so I manage to partition it as ext3 and create a "disklabel" (whatever that is).

Once the whole 3 minutes of formatting was done, I CTRL_ALT_Backspaced. Relogging in did not bring up the drive, so I rebooted altogether. From then on, I could see the drive in Places > Computer, labeled "disk".

I want to know - the other drives can be seen in /media, under sda1 and sdb1, but the new one is labeled 'disk' - shouldn't it be 'sdc1' as I saw in gparted? how do I change that?

Also, how do I change the name of the drive - one is an NTFS drive and is called 'sdb1', but on the desktop is named "STUFF". Can I do that as well? Where or how do I find the tools to do this?

(note: I included a screenshot so you can see most of what's been done already.)

---

### Post by couzin2000 on 2008-06-04
Had to learn the hard way... by trial and error.

I managed to find the way to change the label of the drive. First off, since the drive is linked to a mount point, the mount point is a folder and has a name. So once you've partitioned/formatted the drive, open a terminal and do this:
```
sudo mkdir /the/folder/where/you/want/to/access/the/drive/from
```
Then:
```
sudo chmod 777 -R /the/folder/you/just/typed
```

[FONT="Courier New"]mkdir[/FONT] is to create the directory that will serve as a mount point, or the folder you will access that will act as a portal to your drive. [FONT="Courier New"]chmod 777 -R[/FONT] changes access rights to give everyone who logs in access to the folder itself (777 is universal r/w) and the [FONT="Courier New"]-R[/FONT] is to make this command recursive throughout subfolders inside the folder/mount point.

Then, you can change your drive's name to something cool:
```
sudo e2label /dev/the_drive_identifier newlabel
```
In my case, this command becomes [FONT="Courier New"]sudo e2label /dev/sdb1 Videos[/FONT].

The name of the drive is therefore changed. You MUST reboot for the changes to take effect - logging out does not work properly (at least not for me). [COLOR="Red"]Quick note: [FONT="Courier New"]e2label[/FONT] only works on EXT2 and EXT3 partitions. For other partition types, see this document:_[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")_.[/COLOR]

Hope this can help you install a drive!

---

