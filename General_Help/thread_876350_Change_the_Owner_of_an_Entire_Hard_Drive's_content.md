---
title: "Change the Owner of an Entire Hard Drive's contents."
date: 2008-07-31
forum: General Help
---

### Post by SSVegito888 on 2008-07-31
I am using Ubuntu 8.04 Hardy.

I am trying to change the owner of an entire hard drive's contents.

Here is a little info you might need:

Drive's name is disk

the path is /media/disk

formated as NTFS.

external usb drive


I have tried using gksudo nautilus  and navigated to directory /media  and right-clicked on the folder disk.  Next I went to the permissions tab and tried to change the owner there.  Every time I change it to my username, it immediately changes back to root.

Also, I have tried using chown to change the owner but it didn't work,  I was probably using chown improperly because I am new to Linux.


PLEASE HELP ME!!!


Thanks,

SSVegito888

---

### Post by bodhi.zazen on 2008-07-31
You have to set ownership and permissions at the time of mounting, you need to add a fwe options to /etc/fstab :

Try these options : ```
auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137
```If you would like more permissive options, dmask=000, fmask=111

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by cmnorton on 2008-07-31
I believe this has to do with how the drive is mounted. Look here.

[https://wiki.ubuntu.com/WriteSupportForNTFS](https://wiki.ubuntu.com/WriteSupportForNTFS)

---

### Post by coffeecat on 2008-07-31
> **SSVegito888 said:**
> formated as NTFS.

external usb drive


I have tried using gksudo nautilus  and navigated to directory /media  and right-clicked on the folder disk.  Next I went to the permissions tab and tried to change the owner there.  Every time I change it to my username, it immediately changes back to root.

You are plugging in an NTFS-formatted external USB disc and it is being automounted? Have I got that right? Are you having permission problems, or problems reading/writing/copying/modifying, or whatever? If not, don't worry that all the files seemed to be owned by root. NTFS is a Microsoft filesystem that doesn't support Unix/Linux permissions. When a NTFS-formatted drive is automounted by Ubuntu (or all the other distros I've tried it in) the files are marked as being owned by root, but you should still be able to work with them as an ordinary user.

If you are having permission problems, post back with details of exactly what is happening and someone will be sure to be able to help you. The command chown (and chmod) only works on Linux filesystems, which is why you were having no luck. I'm sure you were using chown properly, just on the wrong filesystem. :wink:

---

