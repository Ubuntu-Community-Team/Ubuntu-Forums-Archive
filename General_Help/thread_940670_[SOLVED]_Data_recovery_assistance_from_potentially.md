---
title: "[SOLVED] Data recovery assistance from potentially dying harddrive + Live CD"
date: 2008-10-07
forum: General Help
---

### Post by ww711 on 2008-10-07
I currently have a Windows XP PC that I need to get files from - My Documents. The hard drive is potentially dying because I can hear clicking noises - sometimes it boots into Windows, sometimes never and am reluctant to try to boot into XP any more, in case this causes further damage to the hard drive.

I'm currently using a Linux Cent OS live CD to access the dying hard drive, it detects the hard drive fine as hda, when I navigate around I can see the files listed, then right click and examine the properties of the files, it says 0kbs, this occurs to some files. Is there a way to get all my files back, if at all? I've already attempted to try copying small chunks of files across rather than all at once, but still having difficulties.

Any other methods that I could try?

---

### Post by geirha on 2008-10-07
Have a look at [http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

---

### Post by jason.b.c on 2008-10-07
> **ww711 said:**
> I currently have a Windows XP PC that I need to get files from - My Documents. The hard drive is potentially dying because I can hear clicking noises - sometimes it boots into Windows, sometimes never and am reluctant to try to boot into XP any more, in case this causes further damage to the hard drive.

I'm currently using a Linux Cent OS live CD to access the dying hard drive, it detects the hard drive fine as hda, when I navigate around I can see the files listed, then right click and examine the properties of the files, it says 0kbs, this occurs to some files. Is there a way to get all my files back, if at all? I've already attempted to try copying small chunks of files across rather than all at once, but still having difficulties.

Any other methods that I could try?




ah , i feel your pain (been there , done that)


do you have a usb thumb drive...?



if so , plug it in and mount it.., then you can drag-and-drop the files you wanna rescue into that...

---

### Post by jerome1232 on 2008-10-07
If you have an external hard drive big enough I would image your drive asap. That way if it dies you still have something to work with.

The following code would image /dev/hda to /media/disk/hda.img (I use that because under Ubuntu that is the usual mount point of usb disks). I would recomend unmounting to avoid  writing to the possibly dammaged drive.

```
dd bs=512 if=/dev/hda of=/media/disk/hda.img conv=noerror,sync
```

---

### Post by ww711 on 2008-10-07
> **jerome1232 said:**
> If you have an external hard drive big enough I would image your drive asap. That way if it dies you still have something to work with.

The following code would image /dev/hda to /media/disk/hda.img (I use that because under Ubuntu that is the usual mount point of usb disks).

```
dd bs=512 if=/dev/hda of=/media/disk/hda.img conv=noerror,sync
```

Forgot to mention that I have a usb external freecom 500gig hard drive thankfully that detects and works in in the live CD.

I will attempt to image the drive and see how far I get.

---

### Post by ww711 on 2008-10-07
I followed through on imaging the dying harddrive to my external usb harddrive, it started to copy and now says 'file size limit exceeded, it's stopped at 4 gigs. since it has hit the 4 gig limit...I suspect that my external hard drive is in a FAT32 file system.... I do not particularly want to format the external harddive because it has a very large amount of data on there...any other options?

---

### Post by jerome1232 on 2008-10-07
wow, I would think those come formated as ntfs! Since you have a 4 gb limit on file size, I guess you'll just have to copy everything over. Mount that drive as read only, then start copying. I would use rsync I guess, it's great for this job.

```

# mount your drive read only
sudo mkdir /mnt/dyingdrive
sudo mount /dev/hda /mnt/dyingdrive -o ro
# make a 'backup' directory on your usb disk
mkdir /media/disk/backup
# copy your entire drive over to your backup directory
sudo rsync -av /mnt/dyingdrive /media/disk/backup
```

---

### Post by ww711 on 2008-10-07
Any reason why bash would say no to a rsync command?

I am on the root a/c of the centos live cd and feeding it the command

*rsync -av /mnt/dyingdrive/ /media/FREECOM\ HDD/dyingdrive/*


bash says rsync: command not found.
I tried a 'man rsync' too - No manual entry for rsync. I guess rsync is not a part of the live cd. Also tried a 'man scp' too - it shows the manual for secure copy.

---

### Post by jerome1232 on 2008-10-07
Is Centos a Red Hat or Debian based distro? Well at any rate you should be able to use your package manager to install rsync to the live cd environment. (I've been assuming Ubuntu this whole time, I'm not sure if that is part of it's live cd enviroment either)

---

### Post by ww711 on 2008-10-07
CentOS is redhat based, that was the only live CD I could find in the stack. I'm sure I have a Kubuntu 5.10 live cd somewhere.

---

### Post by jerome1232 on 2008-10-07
Can't you just use, what is it yum? to install rsync (Can you tell I don't get away from debian much? lol.)
Imaging was the best solution it doesn't copy files it just copies the data (you can mount that image like it was a real hard drive and run all kinds of utilities on it), Rsync is very nice since it verifies everything is copied correctly.

You can just use cp, not the best method but it'll copy your files, this HAS to be installed by default. :)
```
sudo cp -R /mnt/dyingdrive /media/disk/backup
```

---

### Post by ww711 on 2008-10-07
Managed to find a HH 8.04 live CD and now back on track...feed it the rsync command now.

---

### Post by jerome1232 on 2008-10-07
Ok well if it doesn't have rsync and you have some ram to spare, you can go ahead and sudo apt-get install rysnc then run it.

---

### Post by TeXtonyx on 2008-10-07
I just finished doing this before reading this forum now. My XP drive kept rebooting
spontaneously, so I don't know if it is the drive but I couldn't use it, like you. I booted
to Ubuntu and put in a blank dvd (cd will work too). Then under 'places' there is an
option to open the cd/dvd writing folder, which I did. Then open a terminal and type

sudo mkdir /mnt/WinXP  (and if your XP is the first partition then use)
sudo mount -t ntfs /dev/sda1 /mnt/WinXP

This works unless you haven't shut Windows down cleanly, so that it wants to
run those options which include "Start Windows Normally". So try the above first
and if no luck start XP just long enough to use Start->Shutdown (removing the lock)
Now you can use the file browser to see files on XP they are on and under /mnt/WinXP
The way I did it was to use the terminal, cd /mnt/WinXP and then cd to the folder that
you want. I made (sudo mkdir) a folder under my home, /home/textonyx/Rescued so
that I could copy all the files to /Rescued from /mnt/WinXP/transfers There, I used
sudo cp *.txt  /home/textonyx/Rescued from the command line, or you can drag and
drop from the file browser to put them in Rescued or your cd/dvd install folder.
Once I had the files in Rescued I used another file browser window to copy them
to the cd/dvd folder. Not so efficient but to show that there is more than one way.
Once the files are in the cd/dvd folder I think there is a box, make Dvd. Click on
it and it is fairly obvious. I picked a slow/low record speed. In my case I have another
Vista drive and I rebooted to Vista and read the dvd there and copied the files to
the Vista hard drive. One cd or dvd will likely hold everything in your My Documents
I didn't have to install any software for this. If you do install any software, remember
that if you reboot into the live cd, you have to reinstall that software. This is for an
emergency and takes less time than cloning the whole XP drive which can put more
stress on the drive and make it fail. It doesn't hurt to have two backups, this way
first and then to another drive if you can manage that, so you can have two backups.
Remember to use sudo, or else gksudo for the GUI.

---

### Post by ww711 on 2008-10-07
Ok, rsync has finished with some stats.

sent 44538961229 bytes received 1366200 bytes 10089552.03 bytes/sec
total size is 44529446129 speedup is 1.00
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]


Now I have an image of my hard drive on my external hdd and can access my files! Success!

Have to say that a live CD is very useful especially in these type of scenarios as well as knowing Linux and a user community willing to help.

---

### Post by jerome1232 on 2008-10-07
Great glad we could help you get your files, if you feel like this is solved go ahead and mark the thread solved so other people know that a solution can be found here, and that other's don't waste time reading the thread only to find out it's already solved

in the upper right you should have 'thread tools'; use that to mark as solved.

---

