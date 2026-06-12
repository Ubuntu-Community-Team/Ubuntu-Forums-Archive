---
title: "[SOLVED] Icons that won't die!!!"
date: 2008-08-30
forum: General Help
---

### Post by the_hardy_kid on 2008-08-30
Okay, I power up my computer and get to my desktop to find that the contents of my home folder are there.

I assumed that they were shortcuts. I deleted them. Then I realized that that had just deleted the contents of my home folder.

But the icons on my desktop were still there. Crap.

Please help :(

---

### Post by iaculallad on 2008-08-30
Try doing this: Create a new user, then drop on your terminal and issue the commands below:

```
sudo cp -r /home/the_new_user_you_created/.gconf ~/.gconf
sudo chown -R your_username:your_username ~/.gconf

```

Logoff then log back in.

---

### Post by RequinB4 on 2008-08-30
Try this:

Press alt+f2 on your keyboard and enter:

```

gconf-editor

```

select apps -> nautilus -> preferences and uncheck "desktop_is_home_dir"

---

### Post by Shazaam on 2008-08-30
Look around in your trash folders....
Run this code in terminal (will open nautilus as root)...
```
gksudo nautilus
```
Once nautilus opens hit CTRL+H (unhides hidden folders). Go to File System /home/yourusername/local/share/Trash/files
See if your folders are there. If they are drag them to the desktop.
Next go to /root/local/share/Trash/files and look around. Same as above.
Be carefull running nautilus as root as anything you do MAY be permanent.

---

### Post by the_hardy_kid on 2008-08-30
Thanks Guys, but no luck.

The thing is, I have unchecked the desktop_is_home_dir thing in the registry. 
The files don't show up in the ~/Desktop folder either?

---

### Post by the_hardy_kid on 2008-08-30
No, the thread is solved.

They're gone. I unchecked the option and logged out then in again.
I was playing with the registry last night and must have checked it by accident.

Thanks Guys, High 5!

---

### Post by RequinB4 on 2008-08-30
> **the_hardy_kid said:**
> No, the thread is solved.

They're gone. I unchecked the option and logged out then in again.
I was playing with the registry last night and must have checked it by accident.

Thanks Guys, High 5!

OOPS, forgot to tell you to restart GNOME, my bad.  I'll make a mental note.

Glad you got it working!

---

### Post by iaculallad on 2008-08-30
Let's just stick on calling it "gconf-editor". Registry? It's too windoze :lolflag:

---

### Post by the_hardy_kid on 2008-08-30
Yea, because it only showed up on restart.

And agreed, "gconf-editor" sounds cooler anyway.

---

