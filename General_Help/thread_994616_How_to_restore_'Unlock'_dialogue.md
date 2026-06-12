---
title: "How to restore 'Unlock' dialogue"
date: 2008-11-26
forum: General Help
---

### Post by tpapastylianou on 2008-11-26
I've just installed Ubuntu 8.10 on my Asus N10 laptop using wubi.
When it was freshly installed, if I clicked on my DATA partition under 'Places', ubuntu would come up with a lovely window saying something along the lines of, you need to be authenticated to mount this volume, and had a nice unlock button to do so. 

I then installed a few apps to check exactly what is mountable and what is not (I was trying to figure out where the windows files are, turns out they're under /host), specifically pysdm and ntfs-3g. Naturally I realised later on that I didn't need to install either and uninstalled them. 

But anyway, now, when I click on the drive, it just says "not enough privileges to mount volume". Where has the nice 'unlock' dialogue gone? How can I get it back?

To be clear, my issue isn't whether I can access the drive or not, I can always sudo mount it in the console, or even gksudo into nautilus and mount it from the GUI as root. My problem is how can I bring back the lovely 'unlock' dialogue which enables a common non-root user to click on something and be given the option to authenticate.

PS. all the right boxes (i.e. access to external drives) are ticked under User Preferences in the users and groups administration menu, but it still tells me I'm not privileged enough.

---

### Post by tpapastylianou on 2008-11-26
nevermind, fixed by deleting (well, or rather # commenting out) the entries in my /etc/fstab file. I guess pysdm must have altered my fstab,

Now I can mount/unmount as normal user again :)

---

### Post by cariboo on 2008-11-26
Have you somehow removed yourself from the admin or adm groups? To see if you are still a member of the two groups in a Applications-->Accessories-->Terminal type:

```
groups
```

The output should be something like this:

```
jim@jack:~$ groups
jim adm dialout cdrom plugdev lpadmin admin sambashare
```

If you find either adm or admin missing you need to add yourself back to the missing group.

I'm not sure if you can boot into recovery mode in a wubi install, but if you can when you get to the menu select drop to a root prompt and type:

```
usermod -a -G adm admin <user_name>
```

Where user_name = your user name.

Jim

---

