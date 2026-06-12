---
title: "Don't know where to look for backup drive...."
date: 2009-05-12
forum: Hardware
---

### Post by Immolatus on 2009-05-12
I just finished formating (EXT3) an internal backup drive. It used to show up under the PLaces--> computer tab as a 500 gig media, now it's not there.
Any thoughts on how to access it??

P.S. I plan to use it just as one would a flash drive but for the fact that it is installed in the machine. :popcorn:

---

### Post by Immolatus on 2009-05-12
Update: so I put the "disk mounter" applet on the panel and it mounts the back up; however when I try to drag and drop anything in to it I get an error saying I don't have permission.

   My guess is that I need to set the permissions for the whole drive. So the question really is, how to go about it. Any thoughts????

---

### Post by sir_nasty on 2009-05-12
drop into a terminal and do something like chmod 755 DRIVEPATH (/media/disk?) of course in this instance DRIVEPATH is the path to your external hdd... if that gives you an error run: man chmod and check the syntax...

---

### Post by Immolatus on 2009-05-12
Ah!! a response! (I digress often) It seems however that I have arrived at a less than elegant solution. I have added the drive to my /etc/fstab and have created a custom launcher on the panel so I don't have to type out the command every time. The drive is called backup so I created a directory called /backupmt to mount it at. the only rub is that I have to "sudo mv" anything I want to put in to it.

By the way this is actually an internal drive that I just installed and formated ext3. Any other thoughts you might have would be greatly appreciated.

---

### Post by Immolatus on 2009-05-13
Sorry for reposting.......yeah I think maybe there is a better way than what I have done I think it involves editing the fstab again. cheers.

---

