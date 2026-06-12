---
title: "Dropped my laptop...What's the easiest way to recover my hard drive"
date: 2008-11-06
forum: Hardware
---

### Post by NoPoChris on 2008-11-06
A few days ago I dropped my laptop (Dell Inspiron 1520) from about 1 1/2 feet onto a hard floor while it was running. Now when I try to boot I get as far as the Ubuntu bootsplash and then a bunch of text and numbers (which basically is the same as [this]("http://ubuntuforums.org/showthread.php?t=937872")).

I checked to make sure that the hard drive and ram didn't just get knocked loose. I can access the filesystem using the Ubuntu live cd, and right now I'm backing it up to a .tgz archive based on [this howto]("http://ubuntuforums.org/showthread.php?t=35087"). This process is taking a very long time (which I expected) and I get an error every once in a while that says:
```
tar: /whateverfile/: Cannot stat: no such file or directory
```

My plan is to try to re-install Ubuntu and just replace / with the backup I'm making. Is this the best way to do this? Will the backup work even though I get these errors? Do I need to buy a new hard drive? Could the motherboard be damaged?

---

### Post by lazius on 2008-11-06
I think in your case i could get an usb Hard drive and backup all my files and then reinstall ubuntu to see if everything goes fine. 

If it gives your some errors on copying the files maybe you don't have some permissions for certain files to copy them. Just give them the permisson with chmod or via properties windows on a root terminal (Nautilus)

Maybe just the boot sector of the disc is damaged (could be physicaly or logical).
If it's physical maybe you couldn't reinstall Ubuntu again and you will need a new hard drive. 
Well this is just my opinion hope it give you more hints.
Good luck with your issue.

---

### Post by raf_kig on 2008-11-06
I wouldn't suggest doing this. [edit: i was refering to copying over everything to / ]
Do a plain install and copy over all important config files one by one.

You can seach for packages that you had installed in your backup of /var/lib/dpkg/status.

Then restore your home directory, best way to do this would be doing it file by file again and check the config files for corruption.

If you have backups of your personal data in $HOME use those instead of the rescued ones.

Regards

raf

---

### Post by NoPoChris on 2008-11-07
Great, thanks for the info guys!

I ended up having to back up most of my files one by one anyway because the backup file was apparently too large. That's no big deal though, I just made a back up archive of each folder in my home dir and most of the files in the / dir.

Is there anything that I should avoid copying over, or are there any folders that it would be pointless to try to replace? I just want to know so that maybe I could save some time.

---

### Post by RJARRRPCGP on 2008-11-08
If you try to reinstall, do you see any dreaded "Buffer I/O error" error message? If you do, you probably have a bad HDD or bad HDD connection.

---

### Post by NoPoChris on 2008-11-08
The reinstall went smoothly, I didn't get any errors or anything and I can now boot up, yay.

I am trying to extract the backups of some of the stuff from the old / dir (I'm using gui - right click, "Extract Here") but I get this error:
```
tar: whatever/whatever: Cannot change owndership to uid 0, gid 0: Operation not permitted
```

I assume that this is because I didn't correctly change the permissions for the files when I made the backup. Now, I'm not exactly proficient with Tar or chmod. So is there a way to change permissions now?

[edit: I figured out how to do the extraction using sudo tar -xzvf /whatever.tar.gz, I'm just have to learn what the parts of the command mean.

I'll try to break it down:
sudo = super user do, tar = Tar, the archiver/extractor ,-x = extract?, z = has something to do with the .gz, it tells it to ungzip, right?, v = lists the files being extracted, f = not sure, and then the file to be extracted, I can also add where to extract to

right?]

---

