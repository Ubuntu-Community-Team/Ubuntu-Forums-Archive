---
title: "Copy from CD with write permission?"
date: 2008-08-14
forum: General Help
---

### Post by fridaythe14th on 2008-08-14
Any way to accomplish this?

---

### Post by logos34 on 2008-08-14
what exactly is happening?  You mean you're copying folders from a cd but they're locked with no write permission in your destination directory?  If so you can run

sudo chmod -R 777  /copied-cd-directory

---

### Post by fridaythe14th on 2008-08-14
Yes, that's what I meant. Sorry if I was unclear.

Thank you, but I was looking for a way to do it automatically in Nautilus/Gnome.

---

### Post by jerome1232 on 2008-08-14
I don't know of a way to do it autmatically but I wouldn't chmod them 777 either, I would do it this way (I can never remember what each number means so I use chmod differently) 
```
chmod -R ug+rw <files copied from cd>
```

---

### Post by fridaythe14th on 2008-08-14
Thanks! What I was looking for though was something like a setting somewhere to change the default behaviour.

Anyway I have bigger problems now since my CD-drive suddenly stopped working (will post a new thread about that though).

---

### Post by mc4man on 2008-08-14
> something like a setting somewhere to change the default behaviour.
There is no setting, maybe it will be addressed in an update sometime, maybe not.

For a file or 2 i just do a r. click, properties, permissions. For a larger number what's really easy is to make a folder in your home dir. to copy to initially. Then you can change everything in one comm. and not worry about path, filenames, caps, spaces, ect. 
For instance I created a folder in home called fix to copy files from data cd's/dvd's. Then just this 

 chmod u+rw -R fix

---

### Post by fridaythe14th on 2008-08-14
Yeah I know how to chmod, but thanks all anyway!

This behaviour makes sense since CDs are read only and has to be mounted as read only, they get it as permission and the permission is copied. However, does anyone actually want it this way?

---

