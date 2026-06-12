---
title: "[SOLVED] Logitech Camera Support"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by drusepth on 2008-01-18
I've been looking for help for this for a few days now, and all the help I've read on both the forums and on google are outdated.

I've tried easycam, but it errors out all the way through.  If you want the exact errors, say so and I'll copy and paste them, but I didn't think it'd be necessary in the original post because there are hundreds of them.

Also, I've been to
[http://ubuntuforums.org/showpost.php?p=760303&postcount=85](http://ubuntuforums.org/showpost.php?p=760303&postcount=85)
but couldn't really decipher what it is he was saying.

My lsusb:
```
drusepth@drusepth-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:08f5 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
drusepth@drusepth-laptop:~$ 

```

Bus 002 Device 004: ID 046d:08f5 Logitech, Inc. 
Is the camera.

I'm running Ubuntu 7.10.  Any help is appreciated.  If you need more information, just ask.

---

### Post by linuxwizard on 2008-01-18
This is the driver you need > [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/) >  info from here > [http://www.quickcamteam.net/software/linux/drivers/quickcam-messenger-communicate-driver](http://www.quickcamteam.net/software/linux/drivers/quickcam-messenger-communicate-driver)

---

### Post by drusepth on 2008-01-19
Thanks linuxwizard, it didn't work last night, so I did some research on it.  I restarted my computer though, and then it worked perfectly!

---

### Post by linuxwizard on 2008-01-19
You're Welcome drusepth That's great you got the driver installed and setup. And yes you would have had to restart your computer. Please mark thread as SOLVED.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

