---
title: "Working with the enemy"
date: 2008-06-12
forum: Hardware
---

### Post by Sou Portugues on 2008-06-12
So, I accidently deleted the partition on my girlfriends computer. Bad right. I did manage to catch it before it started erasing files. I have installed a fresh copy of windows xp (this is the "working with the enemy" part) home on it, and was going to simply delete all the files under the ntfs partition,and replace them with the files I saved. I mean all the files, so the partition is clean, then replace evrything from my external drive where I backed it up.

The only problem is when I try to acess the laptops hard drive with this live cd, I get the old acess denied bit. here's what it says:

error: device /dev/sda1 is not removable

error: could not execute pmount

How do I work around this, cause she isn't ready to escape the dark side yet (I'm working on her, slowly but surely)?

---

### Post by justin whitaker on 2008-06-12
Switch to root, then try to mount it.

---

### Post by linux6994 on 2008-06-12
You can burn a gparted livecd and use it to correct all types of partitions including ntfs. It can be found here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Suggestion for helping her convert from the MS world, let her use Ubuntu as often as she can. She will never switch unless she feels comfortable using it. There is a learning curve. Explain that she cut her teeth on MS, now its time to grow up and really chew on a stable, virus-free OS.

Good Luck.

---

### Post by Sou Portugues on 2008-06-12
> **justin whitaker said:**
> Switch to root, then try to mount it.

ubuntu@ubuntu:~$ pmount /dev/sda1
Error: device /dev/sda1 is not removable
ubuntu@ubuntu:~$ mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

Can I edit the fstab while in the live cd? Is there a simpler way to do this, like make the cd see the drive as removable?

---

### Post by justin whitaker on 2008-06-12
> **Sou Portugues said:**
> ubuntu@ubuntu:~$ pmount /dev/sda1
Error: device /dev/sda1 is not removable
ubuntu@ubuntu:~$ mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

Can I edit the fstab while in the live cd? Is there a simpler way to do this, like make the cd see the drive as removable?

Did you look in this thread?

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Sometimes when using the LiveCD, I noticed that the drive was mounted as a normal partition, not as an external drive. 

You could try using a normal mount command, and see if that is the case.

The other option is to use the pmount -hal command in that thread, to force mounting an unclean drive.

---

### Post by Sou Portugues on 2008-06-12
> **linux6994 said:**
> You can burn a gparted livecd and use it to correct all types of partitions including ntfs. It can be found here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Suggestion for helping her convert from the MS world, let her use Ubuntu as often as she can. She will never switch unless she feels comfortable using it. There is a learning curve. Explain that she cut her teeth on MS, now its time to grow up and really chew on a stable, virus-free OS.

Good Luck.

I have the gparted cd, but once I reformat, how do I acess the drive, I dont have a second computer to do it from, this is all from the laptop? I am running the live cd of ubuntu (what pops up when you go to install it) so I dont have acess to things like the mtab and fstab files, or apparently, the laptop hard drive. I am unable to install the ntfs-3g util, because it doesn't seem to work with a live cd.

---

### Post by justin whitaker on 2008-06-12
> **Sou Portugues said:**
> I have the gparted cd, but once I reformat, how do I acess the drive, I dont have a second computer to do it from, this is all from the laptop? I am running the live cd of ubuntu (what pops up when you go to install it) so I dont have acess to things like the mtab and fstab files, or apparently, the laptop hard drive. I am unable to install the ntfs-3g util, because it doesn't seem to work with a live cd.

ntfs3g should be on the live cd.

---

### Post by Sou Portugues on 2008-06-12
> **justin whitaker said:**
> ntfs3g should be on the live cd.

I don't think it is, this is a live cd from a year plus ago. Is there another way to do this without the ntfs-3g? Seems like I should be able to chown the fstab or something and do it there....

---

### Post by justin whitaker on 2008-06-12
> **Sou Portugues said:**
> I don't think it is, this is a live cd from a year plus ago. Is there another way to do this without the ntfs-3g? Seems like I should be able to chown the fstab or something and do it there....

Oh, I thought you had the latest live CD. The problem is: you have this drive formatted NTFS. You have an external drive, also formatted NTFS. The problem is, chown or fstab won't make any difference, because you do not have the appropriate file system driver to view the drive. 

You should be able to apt-get install ntfs3g with the LiveCD-it will install the software virtually so you can use it for that session. The caveat is: it all depends on how much RAM you have. 

In this case, what I would do is: boot into XP, or your Linux Machine, and get the latest live CD.

---

### Post by Sou Portugues on 2008-06-12
> **justin whitaker said:**
> Oh, I thought you had the latest live CD. The problem is: you have this drive formatted NTFS. You have an external drive, also formatted NTFS. The problem is, chown or fstab won't make any difference, because you do not have the appropriate file system driver to view the drive. 

You should be able to apt-get install ntfs3g with the LiveCD-it will install the software virtually so you can use it for that session. The caveat is: it all depends on how much RAM you have. 

In this case, what I would do is: boot into XP, or your Linux Machine, and get the latest live CD.

This is exactly the problem. However, here is the catch, I can't get the windows to connect to the internet, or burn cds. And since its a live cd and I only have 1 drive, I cant burn the cd from here, AND this is my only linux machine (the live cd). I already tried to load ntfs-3g for the session, and was unable to sucessfully do so. Caught in a catch 22 if you will...

---

