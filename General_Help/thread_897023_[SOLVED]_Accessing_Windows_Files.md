---
title: "[SOLVED] Accessing Windows Files"
date: 2008-08-21
forum: General Help
---

### Post by fparedesg on 2008-08-21
I just installed Ubuntu Gutsy Gibbon, I then updated to Hardy Heron. I have Windows XD SP3 on my other partition. When I go to ```
/media/*Windows Partition*/Documents and Settings/*user*/My Documents
``` I can access all of my Windows documents, however, when I drag that folder to the top Ubuntu bar/panel to create a shortcut, I cannot access the folder, I get an error message that says: ```
Could not show 'file:///media/Preload/Documents%20and%20Settings/user/My%20Documents'

The location or file could not be found.
``` If I manually go to that directory, close the window, and then try opening the shortcut, it works, however, I have to do that every time I restart/power off. Is there a way to make that shortcut work without having to manually open the folder before? I really need this, because I am constantly accessing the files I have in my Windows partition because of school. Thank you!!

---

### Post by bonfire89 on 2008-08-21
I'm not a linux pro so take my advice with that in mind, I'm just bored waiting for one of my questions to be answered.

I suspect that perhaps the partition isn't mounting until you 'manually click on it'

So, perhaps, if you set up your fstab file to automatically mount the partition at something like /mnt/myWindowsPartition then create your shortcut to that.

Here is a link on setting up linux to automatically mount a drive/partition

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing%20Ubuntu%27s%20filesystem%20table](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing%20Ubuntu%27s%20filesystem%20table)


essentially, doing this will be something like

running the command 

sudo fstab -l

in your command line to get a list of the partitions

then adding a line like

/dev/sda1   /mnt/windowsPartition    ntfs      defaults 0    0


the "dev/sda1" bit is from the sudo fstab -l command
"/mnt/windowsPartition" is your choice
"ntfs" being the file system .... this might actually supossed to be "ntfs-3g"

after editing the file you'll need to run

sudo mount -a  

to remount everything in the fstab file, your you can just restart.


hope it at least helps a tad.

---

### Post by fparedesg on 2008-08-21
Thank you! Setting the drive to automatically mount when booting works great. Thanks!

---

