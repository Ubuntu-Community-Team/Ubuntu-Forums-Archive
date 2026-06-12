---
title: "access denied usb harddrive"
date: 2008-10-26
forum: Hardware
---

### Post by benjaminjames on 2008-10-26
torrent paused: disk write error, open failed: '/media/My Book/media/Music/xxxxxxxx. Read-only file system
OK so i have been using a usb western digital hard disk to store any downloads etc i use it in both windows and ubuntu (mostly ubuntu tho) and since i bought it 6 months ago it has been fine but i am now getting the message posted above whenever i try to save a download on it. i thought an update in hardy may have broken it so i switched to intrepid rc but still the same problem. I went into windows and made sure that it was set to share with all users i then right clicked it in ubuntu and went to permissions and was told "the permissions of "my book" could not be determined". if i check the permissions on the individual folder inside the hdd that i am trying to write to i see that as owner of the file i have create and delete folder access but file access is blank and when i change it to read and write and then exit when i go back into permissions it has reverted to blank.
sorry for the long post but does anyone know how to remedy this. thanks all
btw i forgot to mention that if i try to share the folder in ubuntu i get the message could not change the permission of "media" folder

---

### Post by scliburn on 2008-10-26
hmmm. very coincidental, however I am experiencing the same problem. It's read only, and I can't format it, or change permissions. I have gparted and it doesn't give me the option to delete any partition, nor format any part of the drive. I've mounted this on an Ubuntu server and the same issue applies. Very strange.

Anyone familiar with a quick resolv. for this?

---

### Post by roman.lange on 2008-10-27
Very interesting, I have been experiencing exactly the same problem! The USD drive gets mounted as soon as I plug it in, it gets displayed on the desktop, but it is read-only. I tried gksudo nautilus to change the permissions but failed as I do not have the permission to change the permissions... :)

I have been using this drive for several months without problems. The problem just started a few days ago. I cannot save any file to it anymore.

Does anyone know of a possible solution?

Edit: as I was still able to copy files from the drive but not to the drive, I decided to backup the files. I then tried a few other solutions but the situation just got worse. So I decided to change the file system to /ext3 which I did using GParted (back up your files beforehand, otherwise they will get lost!). Afterwards I still had to use the terminal, type "gksudo nautilus" and change the permission on the drive. I know, not an elegant solution, but at least I can use the drive again...

@Scliburn: using GParted, I first had to unmount the drive. Have a look at this [http://www.mattcutts.com/blog/format-external-drive-for-linux/]("http://www.mattcutts.com/blog/format-external-drive-for-linux/")

---

### Post by benjaminjames on 2008-10-27
nice to know im not alone but we definatley need a solution ive been tinkering around for hours and NOTHING this is a major problem for me as my ubuntu partion is tiny so i cant really save anything on it. grrr anyways as before any help is much appreciated thanks all

---

### Post by benjaminjames on 2008-10-28
bump

---

### Post by benjaminjames on 2008-10-29
looks like we are alone, im seriously considering formatting my harddrive as i want to get rid of my vista partion anyway but it could happen again anyway so i still really need an answer so c'mon ubuntu guru's surely u can suggest something :(. thanks all

---

