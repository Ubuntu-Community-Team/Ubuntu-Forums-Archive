---
title: "MP3 player - read only?"
date: 2009-03-03
forum: Hardware
---

### Post by lemonbar on 2009-03-03
I have a new [8gb Memorex mp3 player]("http://www.memorex.com/products/product_details.php?FID=50100&PID=50712") - I had it working okay (using Intrepid on my pc, btw), but last time I tried to add and remove songs, my computer crashed and I lost everything on the player - even the browser.  I reset the player, and it's functional (radio works, mic works, I can change the skins, yada yada), and once the computer was running again, I tried to put music on the player (which is empty aside from the basics).  I get an error message now that says "read only" permission.  I opened the properties window to change the permissions to "read and write," restarted, and still receive the same error message.  I've looked all over for the answer but am overwhelmed by all the advice - does anyone have...

[CENTER]**[SIZE="5"]The Answer?[/SIZE]**[/CENTER]

I'm about to go crazy.

---

### Post by cariboo on 2009-03-03
You can set the mount point to world read/write eg:

```
sudo chmod -R 777 /media/<mp3_mount_point>
```

where <mp3_mount_point> = how the device is mounted in /media.

The above command must be run in an Applications-->Accessories-->Terminal.

Jim

---

### Post by lemonbar on 2009-03-04
So, I tried that, and it did this:

> chmod: changing permissions of `/media/disk': Read-only file system
chmod: changing permissions of `/media/disk/STDBSTR.DAT': Read-only file system
chmod: changing permissions of `/media/disk/STDBSTR.IDX': Read-only file system
chmod: changing permissions of `/media/disk/STDBDATA.DAT': Read-only file system
chmod: changing permissions of `/media/disk/STDBDATA.IDX': Read-only file system
chmod: changing permissions of `/media/disk/Record': Read-only file system      
chmod: changing permissions of `/media/disk/FMRecord': Read-only file system    
chmod: changing permissions of `/media/disk/TXT': Read-only file system         
chmod: changing permissions of `/media/disk/RAMLIST.DAT': Read-only file system 
chmod: changing permissions of `/media/disk/SETTINGS.DAT': Read-only file system
chmod: cannot access `/media/disk/X': Input/output error
chmod: cannot access `/media/disk/The Only Ones': Input/output error
chmod: cannot access `/media/disk/music': Input/output error
chmod: changing permissions of `/media/disk/Record': Read-only file system
chmod: changing permissions of `/media/disk/FMRecord': Read-only file system
chmod: changing permissions of `/media/disk/TXT': Read-only file system
chmod: cannot access `/media/disk/.Trash-1000': Input/output error
chmod: cannot access `/media/disk/The Ramones': Input/output error


...and then it still said "read only."  I tried changing the mount point under properties to /mp3player, and tried to drop the music on the disk.  "Read only" - but I wasn't really surprised. I unmounted the player, plugged it back in, and got "unable to mount disk."  So, I screwed up something again.  Is it broken now?  

I reset the mp3 player, and I was wondering where to go to change the mount point.  After all this I'm a little cautious about touching anything on the computer or the mp3 player:D.

---

### Post by lemonbar on 2009-03-04
I should've used the brackets maybe?

---

