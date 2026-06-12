---
title: "Cannot get into Display settings because of orphaned module"
date: 2008-11-02
forum: General Help
---

### Post by SkittleLinux18 on 2008-11-02
I plugged in a second monitor to my Linux computer. When I went into the *Monitor and Display Settings*, I turned on the second monitor and set it to *dual image*. Upon closing out, I was prompted to restart X. I did, but the monitor wasn't working. So I tried to get back into *Monitor and Display Settings* and was given this message:

[IMG]http://i17.photobucket.com/albums/b62/keving1/Settings-Error-Messages.jpg[/IMG]

I unplugged the monitor and restarted the whole computer. When it booted to the KDM screen, the login window was almost off the screen. I had to play with it to type in my password and login to KDE. I still get the same error message when I try to get into the settings. Everything else is working fine. How do I fix this?

---

### Post by SkittleLinux18 on 2008-11-03
By the way, this is Kubuntu 8.04 with KDE 3.x

---

### Post by SkittleLinux18 on 2008-11-05
I ransacked the Ubuntu bugs report for this, or similar, problems. I found the exact problem was reported for the "Disks and Filesystems" settings. No one in the very long thread pertaining to the bug experienced the problem with the "Monitor and Display" settings, just other settings within the System Settings Menu. There were screen shots provided in the thread and they were identical to the one I have posted. 

Furthermore, I discovered in there that this problem has persisted since the Dapper days, and is still not resolved.

The closest thing anyone found to a resolution was upgrading various packages through Adept Manager, however, no one knows which upgraded packages provided the fix. Many were saying the problem was never fixed, those few users just got lucky. I didn't read everything, but in my mind, this problem is, for the time being, unresolvable.

---

