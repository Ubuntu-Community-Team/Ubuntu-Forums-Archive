---
title: "usb external hard drive, can't delete files"
date: 2009-05-25
forum: Hardware
---

### Post by acefromspace on 2009-05-25
I have used this same drive (Western Digital 80 gig in external USB case) with other Linux (Fedora) no problems. It works fine with Ubuntu (mounts, can read files, play videos, ect) but I can't delete files. error about read only filesystem. drive is formatted vfat (msdos) I have used this drive before with Windows also (that's why it was formatted vfat) but now don't care about that. what format is best for Linux only systems? all I use this drive for is storing data files.

---

### Post by B4RR13N705 on 2009-05-25
I think that you dont have permissions. Do some "chmod" and it will work fine. :)

---

### Post by picante on 2009-05-25
I have this same problem. Because of that I haven't been backing up to my USB drive and have since lost a lot of things because apparently openoffice isn't very consistent with saving things. Odd.

But what does "chmod" mean?

---

### Post by B4RR13N705 on 2009-05-26
Chmod is for give permissions to a file or folder.
```
 $ sudo chmod a+wxr <file> 
```
+w -> Write permissions
+r -> Read Permissions
+x -> Execute Permissions

---

### Post by acefromspace on 2009-05-26
I found a sort of solution in another thread... not sure why this works, but it seems to fix the problem for now. I unmounted the drive, but left it powered on, shut down computer, started computer and now it works, including "move to trash". When I unmount drive again, I get a prompt to empty trash... works. I will try some command line also, just to get in there and really find out what's going on. folders and files on the drive show in properties as owner: (the original name I chose at install) with read and write allowed, but show group: root. finally, there is checkbox to share... would this help?

---

### Post by firstcupoffreshpressed on 2009-05-30
I found a solution to my permissions problem that may work for others.

1. mount the external drive 
2. open a terminal and type: 

                 mount

Your output should have lines that look like this:

/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on [COLOR="Red"]/media/disk-1[/COLOR] type ext3 (rw,nosuid,nodev,uhelper=hal)

3. type:

   sudo chown -R username:username /[COLOR="Red"]media/disk-1[/COLOR]

Use your username where it says user name and use what it says between "sdb1 on" and "type" after user name.  I colored it red to make it easy to see.  

Hope this is clearer than mud and helps.  I can write to my external drive now after hours of perplexification.

---

### Post by picante on 2009-06-10
That seemed to work until it got to a couple of folders which refuse to be deleted, then my terminal went BALLISTIC with just random symbols filling the entire window. It was still going like that ten minutes later so I closed the terminal, and then my computer was running horribly slow so I rebooted.

Anyway, I think I may just need to buy another drive, because with these undeletable folders here, I had the same troubles when using Windows - drove me absolutely loco.

Thanks for your help.

---

### Post by Mr Gates on 2010-05-02
I have the same problems in ubuntu 10.04 but I did not have these issues in ubuntu 9.04. However this solution does not work. a Operation not permitted entry appears in the terminal screen although I am an admin on the system

---

