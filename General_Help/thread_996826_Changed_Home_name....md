---
title: "Changed Home name..."
date: 2008-11-29
forum: General Help
---

### Post by Dj Dutchman on 2008-11-29
HI, I installed Ubuntu 8.10 (x86) on a friends laptop and today I recieved an email from him saying that he has a problem. Normally I would go to him and trouble shoot but I'm presently in a different city so I was wondering if anybody could help...

Here is his email:

> Basically was sorting out  stuff on my laptop and my home directory was listed as “dario” the small d was annoying me so I went to the about me information where directory was listed as /home/dario and tried to sort it out. Didn’t get a result so I tried changing directory to /home/Dario and then  saved and that’s where the problem comes in.

So when I log in I still use username: dario and password: ******

Then the message comes up: “Your home directory is listed as: ‘/home/Dario’ but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.”

Then if you click No it just goes back to homescreen if you click Yes it goes to this message:

“User’s  $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User’s $HOME directory must be owned by user and not writable by other users.”

K then another message comes up: “Could not update ICEauthority file /.ICEauthority”

Then another message: “There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)”

And yet another one: “Cannot create the directory “home/Dario/.gnome2/share/fonts”. This is needed to allow changing the mouse pointer theme.”

And another: “There was an error starting up the screensaver: Failed to change to directory ‘/home/Dario’ (No such file or directory) Screensaver functionality will not work in this session.”

And that’s the end of the messages. After that it just goes to the desktop background with nothing else hey.

Can anybody help???

P.S. Trying to log in with 'Dario' (Capital D) doesn't work...

---

### Post by cmnorton on 2008-11-29
It looks like if he renames /home/Dario to /home/dario, and reboots, or minimally logs out and logs back in, he should be all set.

---

### Post by Dj Dutchman on 2008-11-29
So he should say yes to 'logging in with the / (root) directory as his home directory', browse to his /Dario home directory and change it to /dario.

One question, what is the path to the home directories? Sorry I'm not completely familiar with the Ubuntu file system...

---

### Post by dexter on 2008-11-29
> **Dj Dutchman said:**
> 
One question, what is the path to the home directories? Sorry I'm not completely familiar with the Ubuntu file system...

/home

---

### Post by Dj Dutchman on 2008-11-29
Thanx, that would make sense ;)

---

### Post by taurus on 2008-11-29
If I were him, I would boot the machine into recovery mode from GRUB menu and then change it back from there.

```
mv /home/Dario /home/dario
ls -la /home
shutdown -r now
```

---

### Post by cmnorton on 2008-11-29
> **Dj Dutchman said:**
> So he should say yes to 'logging in with the / (root) directory as his home directory', browse to his /Dario home directory and change it to /dario.

One question, what is the path to the home directories? Sorry I'm not completely familiar with the Ubuntu file system...

I agree with the posts that say to do this in recovery mode.

---

### Post by Dj Dutchman on 2008-11-29
Thanks everybody, I've emailed him, will let you know as soon as he gets back to me...

---

