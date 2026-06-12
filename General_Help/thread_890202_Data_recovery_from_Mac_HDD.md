---
title: "Data recovery from Mac HDD"
date: 2008-08-14
forum: General Help
---

### Post by Astronomerob on 2008-08-14
Hello everyone,

My mac laptop died on me a while back and I have since salvaged the hard-drive from the computer, put it in an external hard-drive case that connects to the computer through a USB cable. I had no probable recovering the majority of the files, but there are a few files that I cannot access (of course they are the ones I most need to recover).

When I double click on the desktop file under my user name in the Mac HDD I receive a message:
'
The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "Desktop".
'

Under the properties tab it says that the contents are unreadable. Under the permissions tab it says the owner is 502.

I'd appreciate any ideas on how to access, bypass (hack, or whatever there may be) to get around this.

Thank you.

---

### Post by gobbles414 on 2008-08-14
> **Astronomerob said:**
> Hello everyone,

My mac laptop died on me a while back and I have since salvaged the hard-drive from the computer, put it in an external hard-drive case that connects to the computer through a USB cable. I had no probable recovering the majority of the files, but there are a few files that I cannot access (of course they are the ones I most need to recover).

When I double click on the desktop file under my user name in the Mac HDD I receive a message:
'
The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "Desktop".
'

Under the properties tab it says that the contents are unreadable. Under the permissions tab it says the owner is 502.

I'd appreciate any ideas on how to access, bypass (hack, or whatever there may be) to get around this.

Thank you. I had the exact same problem when I tried to recover data from my Fiancee's dead iBook. The following procedure worked for me:

1. Open a terminal window in Ubuntu by going *Applications => Accesories => Terminal*.

2. Enter *sudo chmod 777 -R /media/NAME_OF_THE_MAC_HARD_DRIVE* (no period). Obviously, replace NAME_OF_THE_MAC_HARD_DRIVE with the Mac hard drive's real name. :)

3. Enter *sudo chown YOUR_USER_NAME -R /media/NAME_OF_THE_MAC_HARD_DRIVE*. Obviously, replace YOUR_USER_NAME with the name of your Ubuntu user account.

4. Enter sudo chgrp *YOUR_USER_NAME -R /media/NAME_OF_THE_MAC_HARD_DRIVE*.

5. Unmount the Mac hard drive, and disconnect it's cable from your computer.

6. Restart your computer, and then log into Ubuntu.

7. Reconnect the Mac hard drive, and it should automatically mount.

8. You should now be able to access all files/folders on the Mac hard drive! :guitar:

Let me know if this solution works for you. By the way, this procedure can also useful when you can't access a hard drive which has been newly formatted in a partition editor like GParted in Ubuntu.

---

### Post by Astronomerob on 2008-08-15
Thanks for your response, but I am encountering a problem when trying your solution. I think the problem is in the name of the hard-drive (or how I am putting in the name). This is what the terminal ended up showing:

:~$ sudo chmod 777 -R /media/Rob's Computer
> sudo chown robert -R /media/Rob's Computer
chmod: cannot access `/media/Robs Computer\nsudo chown robert -R /media/Robs': No such file or directory
chmod: cannot access `Computer': No such file or directory


Any suggestions?

Thanks again.

---

### Post by Astronomerob on 2008-08-15
Also, adding a forward slash \ does not seem to change anything:

Rob's\ Computer

doesn't change anything.

---

### Post by coffeecat on 2008-08-15
It might be easier to copy all the files you can't access as root, and **then**, once they're on your Linux filesystem, chown them to your ownership. That way, you don't have to unmount and remount the MacOS-formatted drive.

Try this:

```
sudo cp -a /path/to/folder/on/drive/* /path/to/destination/folder/
```The -a flag will preserve the permissions (which is a minor nuisance) but will also preserve the timestamps. Now:

```
sudo chown *yourusername*: /path/to/destination/folder/*
```Don't forget the colon after yourusername.

The reason for all this fiddling is that your Linux UID is different from the UID of the files you can't access on the Mac formatted drive. Both Linux and MacOS use Unix permissions. In Linux, the first created user is given the UID 1000. On my Mac Mini my UID is 501, and I had exactly the same problem as you copying files from a hfs+ (Mac filesystem) fornatted drive. And did (more or less) the above to get round it.

**Edit:** Just noticed this in your first post:

> Under the permissions tab it says the owner is 502.502 is the UID (user identity number). The files must have been owned by the second created user on that MAC, but just follow what I describe above and you should be OK.

**ALSO - 2nd edit:** :wink: Seeing as you're having problems with the space in the path (and I guess the ' is also causing problems) why not open a nautilus browser as root to copy the files across to your Linux machine? Then you can chown them to your ownership in the terminal (second step above) once they're in your Linux filesystem. For a root nautilus:

```
gksudo nautilus
```But be careful when you have a root nautilus open. You have full adminstrative privileges with it.

---

### Post by Astronomerob on 2008-08-15
Great, I'll give that a go as soon as I can. But before I do, I have a question. When I am writing in the path to the folder on the Mac HDD should I drag and drop the file to the terminal (which results in a long and confusing file path [or directory]) or should I use the /media/..... directory? (If I haven't made sense I apologize, I'm not too terribly familiar with this)

Thanks.

---

### Post by coffeecat on 2008-08-15
> **Astronomerob said:**
> Great, I'll give that a go as soon as I can. But before I do, I have a question. When I am writing in the path to the folder on the Mac HDD should I drag and drop the file to the terminal (which results in a long and confusing file path [or directory]) or should I use the /media/..... directory? (If I haven't made sense I apologize, I'm not too terribly familiar with this)

If you've automounted the Mac disc, the path will always start with /media, because that's where the system creates the mountpoint. The mountpoint you're getting is /media/Rob's Computer. I guess that's because 'Rob's Computer' is the partition label - probably what you created when the Macbook was alive and well. The problem with 'Rob's Computer' is that you've got a space and a ', both of which need to be escaped with the \ symbol. A bit of a fiddle, particularly when you have to do something like /media/Rob\'s\ Computer/folder/subfolder/subsubfolder/filename. That's why I suggested opening a root nautilus. All you have to do then is to navigate to where your files are on the Mac HDD, and drag and drop them over. If you get an error, open a second root nautilus, navigate that to your destination folder, and drag and drop from the first nautilus window to the second. The files will be copied, but they will still have to be chown'd.

Actually, since I posted I had a further idea. I've never tried it, but it should work. Have you got an external USB drive formatted with a Microsoft filesystem - either fat32 or NTFS? Or another partition on your internal drive, also FAT32 or NTFS. If you drag and drop your Mac files (with root nautilus) onto a Miscrosoft filesystem, the files conveniently lose their ownerships, because MS filesystems don't support Unix permissions.

You should then be able to copy them into your home folder in the ordinary way. If you do that it might be wise first to unmount the USB drive and log out and in again and remount the USB drive, because when you do 'gksudo nautilus' you get a root-owned desktop. There's a way of preventing that with an option, but I can't remember it offhand.

---

### Post by gobbles414 on 2008-08-15
> **Astronomerob said:**
> Thanks for your response, but I am encountering a problem when trying your solution. I think the problem is in the name of the hard-drive (or how I am putting in the name). This is what the terminal ended up showing:

:~$ sudo chmod 777 -R /media/Rob's Computer
> sudo chown robert -R /media/Rob's Computer
chmod: cannot access `/media/Robs Computer\nsudo chown robert -R /media/Robs': No such file or directory
chmod: cannot access `Computer': No such file or directory


Any suggestions?

Thanks again. Are you sure that the name of the Mac hard drive is really *Rob's Computer*? Unplug all printers, scanners, memory card readers, and USB flash drives from your computer... Then restart. Once you've logged back into Ubuntu, go *Places => Computer*. In the computer window, go into *filesystem => media*. There should be some folders here. Each of your CD-ROM drives probably has a folder here. But there should also be a folder which represents your Mac hard drive. What is it called?

---

### Post by Astronomerob on 2008-08-15
Awesome! Got it!

I ended up using a combinations of ideas. Here's what happened:

I tried starting a nautilus window, but couldn't figure out how to navigate to the HDD without leaving root. So I tried copying the files from the MacOS HDD to another external HDD using NTFS. Here's what it ended up looking like:

sudo cp -a /media/Rob\'s\ Computer/users /media/External\ HDD

And that worked flawlessly (even if it did take a rather long time to copy). Note that the apostrophe also had to have a \.

So thank you all very much for your help.

---

### Post by thankershow on 2013-01-11
> **Astronomerob said:**
> Hello everyone,

My mac laptop died on me a while back and I have since salvaged the hard-drive from the computer, put it in an external hard-drive case that connects to the computer through a USB cable. I had no probable recovering the majority of the files, but there are a few files that I cannot access (of course they are the ones I most need [data recovery]("http://www.transfer-iphone-recovery.com/")).

When I double click on the desktop file under my user name in the Mac HDD I receive a message:
'
The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "Desktop".
'

Under the properties tab it says that the contents are unreadable. Under the permissions tab it says the owner is 502.

I'd appreciate any ideas on how to access, bypass (hack, or whatever there may be) to get around this.

Thank you.
Using the Blue button does not require the CDs.   This assumes you  sttill have a valid recovery partition on your hard drive.  It's the same as using the CDs however, in that the visible drive partition is reformatted and the system is re-loaded as it arrived from the factory.

---

