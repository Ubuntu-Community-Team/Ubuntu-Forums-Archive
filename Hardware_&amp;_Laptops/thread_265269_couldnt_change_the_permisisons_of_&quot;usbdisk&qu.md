---
title: "couldnt change the permisisons of &quot;usbdisk&quot; because it is on a read only disk"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by Trekos on 2006-09-25
I dont know how to get around this.
I got this 2GB usb stick 2 days ago, unpacked it, tried it at work, made a couple of copy/deletes on my system there (running Ubuntu 6.06), took it at home, attached it on the usb port, read all the data fine, but when the time came to store modified data back into the stick I get the message above.
Tried to change permisisons through Nautilus, it won't let me. So I decided to go root.
I open a terminal, run sudo -s, opened Nautilus, tried to change the permissions, it simply wont let me !
The same message pops up : 
"The permissions could not be changed".
Couldn't change the permissions of "usbdisk" because it is on a read-only disk.

The file owner and the file group on the stick is "...me"

I am no Linux newbie, I have been using the great power of Tux for the last 1 1/2 year, and never before had to get down and get "dirty" messing with system files. Everything used to work fine for me... until now.

So... HELP !
Any ideas ?

---

### Post by talpone on 2006-09-30
The same happens to me.
My 80 GB usb disk worked fine for months and now after few r/w operations goes read-only.
The only changes from before to now is the online Ubuntu update I did last week.
Maybe ... ?

---

### Post by talpone on 2006-10-01
Problem fixed.
Take a look [http://www.ubuntuforums.org/showthread.php?t=267893&highlight=fstab+mount](http://www.ubuntuforums.org/showthread.php?t=267893&highlight=fstab+mount)
Maybe something has been changed in this component in the last update.
Bye

---

### Post by crazymurphey on 2006-10-04
I had the same thing happen to me with a USB flash drive just now, and all I wound up doing is eject it (I had been just unplugging it like you do in Windows, as I am a brand-new convert), unplug it and plug it back in and now I can write all I want.  Maybe this will help people who visit this thread in the future.  Thank goodness for Ubuntu forums!

---

### Post by jeecol on 2006-12-13
Hi, 

I had the same problem.  I copied some files into a 2.5" HD from my laptop (Kubuntu 6.10) in office and connected the HD to my desktop (Ubuntu 6.10) at home. 

1. The first moment, the files were read-only (yes, I could see the lock on the file icon). Then I used File Browser, root to changed the read-only into read and write. 

2. Around 30 min editing, the usbdisk became read-only again. I used File Browser, Root, but this time I failed.

3. I disconnected USB cord, and then the power cord for 2.5" HD.

4. I turned the power on and reconnected it to my desktop; this time, it was not read-only (I continued to edit it)

5. This is not a smart solution, but works.

----------
jeecol = one dollar, in my first language.

---

