---
title: "Can't get external hard drive to read"
date: 2014-04-28
forum: Hardware
---

### Post by lollylopmr2 on 2014-04-28
The hard drive is formated for mac, however it was removed incorrectly and will not register as plugged in for Windows or Mac. It will show up in linux. however I cannot get it to mount, I get the following error

Unable to access “Time Machine”

Error mounting /dev/sde3 at /media/meg/Time Machine: Command-line `mount -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sde3" "/media/meg/Time Machine"' exited with non-zero exit status 32: mount: /dev/sde3 already mounted or /media/meg/Time Machine busy

I need help as soon as possible. I am doing this for a friend (it contains her entire collage portfolio, and she is a graphic designer and animator) who is trying to graduate

---

### Post by ajgreeny on 2014-04-28
To mount a mac drive you will need to install **hfsplus** package from software repositories. You may also need **hfsprogs** and **hfsutils**, but I have never needed to use any of these so I'm not sure which are essential

---

### Post by lollylopmr2 on 2014-04-28
thank you that lets me at least mount the drive.
however i am still getting an error

This location could not be displayed.

Sorry, could not display all the contents of &#8220;Time Machine&#8221;: Error when getting information for file '/media/meg/Time Machine/.DS_Store': Input/output error

---

### Post by ajgreeny on 2014-04-29
Can you see them if you use nautilus as root with command **gksudo nautilus** and then navigate to the drive?  Mac filesystems use permissions rather like Linux as far as I'm aware so you may be blocked as a normal user, but be able to view and copy them as root.

Otherwise I'm afraid I have no idea where to go; I've never used a mac nor had to look at a mac drive.

---

