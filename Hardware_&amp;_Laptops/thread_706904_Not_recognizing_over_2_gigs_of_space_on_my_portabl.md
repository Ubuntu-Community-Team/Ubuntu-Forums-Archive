---
title: "Not recognizing over 2 gigs of space on my portable music player"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by DocForbin on 2008-02-24
My laptop running Ubuntu 7.10 shows 67.9 MB of free space on my iAudio 7, and won't let me transfer anything larger than that. But if I look at the directories individually, there should be over 2 gigs available. When I go into information on the device is says there is 2294 MB of free space. Not sure when this started as I usually have 2-3 GB open. There have been a couple of unsafe removals here and there.

I empty the trash if need be every time I unmount, and am not seeing any hidden files or anything. The 'du' command shows the correct free space too.

sudo du -sh 
5.4G    I AUDIO7/

[IMG]http://img338.imageshack.us/img338/9198/screenshotyh4.png[/IMG]

Any ideas?

---

### Post by marpstar on 2008-02-24
I've had the same problem with my iPod.

I followed the instructions in this thread and got it working great again:

[http://ubuntuforums.org/showthread.php?t=390299&highlight=ipod+free+space]("http://ubuntuforums.org/showthread.php?t=390299&highlight=ipod+free+space")

---

### Post by DocForbin on 2008-02-24
Thanks for the link marpstar. I ran dosfsck on the drive and the correct free space is showing now :)

---

### Post by soxs on 2008-03-02
Well, my guess was that ~2gigs are in your .Trash* folder on the portable device. Simply use <STRG><H> to show all hidden fiels and delete the Trash folders on your music player (maybe this requires super user previliges &#8594; console &#8594; cd /media/yourdevice && sudo rm -Rvf ./Trash* which will remove all Trash folders like .trash .Trash and its content(s)).

---

### Post by DocForbin on 2008-03-02
naw, the trash was empty as mentioned in my OP. dosfsck fixed the issue. thanks though

---

