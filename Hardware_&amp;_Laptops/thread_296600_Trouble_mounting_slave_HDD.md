---
title: "Trouble mounting slave HDD"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by Ian Adkins on 2006-11-09
Hi there.  I just installed Ubuntu this summer, and it's great.  There are only a few things I have yet to figure out, and I was hoping someone might be able help me with one of them.

I have a slave drive that has a lot of media and backup files on it.  Though it shows up in the File Browser, I am unable to access it:

Unable to mount the selected volume
error: device /dev/hdb1 is not removable
error: could not execute pmount

It's formatted FAT32, and all the jumpers and cables are correct and secure.  I thought I read somewhere that the problem might be that I need to create an Ubuntu file directory for the disk, but (a) I don't know how to do this, and (b) I'm afraid of losing my data.

I'd really appreciate some guidance.  Keep in mind, though, I am a total novice with a very shaky grasp of terminals and directory structures and all that jazz.

---

### Post by BLTicklemonster on 2006-11-09
If you are using Edgy, then do this:

Get pysdm from synaptic, then go to system, administration, and then go to storage device manager, and you can mount from there.

If you are in dapper, then go to the link in my sig that says, automatically mount partitions.

---

### Post by catlett on 2006-11-09
Just copy and paste what I write below. This will not tamper with your data. I am going to put this in a folder called slave for the examples below but you can use whatever label you want.
First make a directory called slave in the media folder
```
sudo mkdir /media/slave
```
Next you need to add an entry to the file that tells the computer what drives to mount on startup
```
sudo gedit /etc/fstab
```
ONE THING TO CHECK. MAKE SURE /dev/hdb1 IS NOT ALREADY LISTED. IF IT IS, PODST THE OUTPUT OF /etc/fstab BEFORE YOU GO FURTHER.

After the files opens, enter this line at the bottom.
```
/dev/hdb1 /media/slave vfat iocharset=utf8,umask=000 0 0
```
Save the file and close it. Reboot your copmputer. If you have volume icons viewable in your settings there will be an icon of a hard drive called slave on the desktop. If not, go to the top panel and enter into Places>Computer>Filesystem>Media in media you will see the slave folder. Open it and your files will be there. If you get any errors, post them amd we'll see if we cvan figure them out but this should work.

---

### Post by Ian Adkins on 2006-11-09
Holy crap, thanks!  That worked like a charm.  I have full access to my data now. :-D

---

