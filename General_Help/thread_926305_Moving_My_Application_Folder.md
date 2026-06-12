---
title: "Moving My Application Folder"
date: 2008-09-21
forum: General Help
---

### Post by LeonBlade on 2008-09-21
Hello everyone,

I currently have the application [Songbird] on my desktop.
However, I want it in the folder with all the other automatically installed apps where it should be.

Can someone tell me where to move it and how to place it on the applications bar.

Thanks,
--LeonBlade

P.S. Sorry if this topic is already some place else.

---

### Post by Monotoko on 2008-09-21
the place for applications is /etc if its not with ubuntu

and to put something on your taskbar, just drag the item up there :P

---

### Post by cariboo on 2008-09-21
The previous poster is off by a little bit, /etc is for configuration files. Programs that are not in the repositories should be installed in either /usr/local or /opt. Remember you will have to change the ownership and permissions if you move the folder to one of the above mentioned directories.

Jim

---

### Post by LeonBlade on 2008-09-23
Thank you both.

I have the /otc/ directory, but not the /local/ directory.
The /otc/ directory is totally empty...
Any ideas on where I can find all of my programs so I know where to place them?  

And permissions?  Is that just the ```
chown 777
```

---

### Post by mc4man on 2008-09-23
If your using **hardy** you could also just install the songbird .deb here and it will be treated like any other installed app.

[http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird)

---

