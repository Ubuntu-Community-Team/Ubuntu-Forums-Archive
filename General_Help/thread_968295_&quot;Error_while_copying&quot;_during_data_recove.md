---
title: "&quot;Error while copying&quot; during data recovery using Ubuntu liveCD"
date: 2008-11-02
forum: General Help
---

### Post by krembanan on 2008-11-02
Hello,

I have search the forums for similar posts but found none.

I am using a Ubuntu liveCD for saving the data on my friend's windows laptop hard drive that recently broke down (She gets a blue screen and can't boot into Windows). 

I managed to mount her hard drive following the steps in this nice guide:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

At first, I too recieved the error message about "cannot mount drive", but the guide showed me how to "force" mount it in a folder /media/disk in Ubuntu using the following command:

```
mount -t ntfs-3g /dev/sda1 /media/disk -o force
```  

At this point, I was able to mount, open and browse the hard drive and see her files. However, when I copied the files and tried to paste them into an external USB hard drive, I recieved the following error:

"There was an error getting information about the files in the folder "[Folder name]"

Show more details

Cancel Retry Skip"

Skipping the message led to another similar message for another folder name.

"Show more details" yields

Error stating file '/media/disk/Documents and Settings/Videos/[a really long path here, nothing special]/videofinder.properties': Input/output error

 
Does anyone have an idea why the copying doesn't work? I feel that I am so close to rescuing her broken Windows data using Ubuntu.

Thanks for reading

---

### Post by cmnorton on 2008-11-05
First thing, I would try to recover your friend's system using recovery console in Windows. I've pulled data off Windows and other Linux systems, without having to force a mount. That does not mean you should not force the mount, but seeing you had to do that made me wonder if there isn't a mechanical problem with the disk or a problem with the file system.

If you really want to get data off, you can use dd, but you have to have something that is a target of the dd, either an attached USB drive or some place on the network. Then, you'd need to recover the Windows disk, and dd back, in case the recovery did not go well.

---

### Post by krembanan on 2008-11-07
OK, thanks. Maybe I will try dd.

(For other readers with similar problems: At first I didn't know what dd was, but then I searched for it and found this link which explains what it is ("data dumping").)

[http://ubuntuforums.org/archive/index.php/t-922469.html](http://ubuntuforums.org/archive/index.php/t-922469.html)

---

