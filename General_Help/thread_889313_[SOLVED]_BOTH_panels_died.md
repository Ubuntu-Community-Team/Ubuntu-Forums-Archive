---
title: "[SOLVED] BOTH panels died"
date: 2008-08-14
forum: General Help
---

### Post by pikabuntu on 2008-08-14
This was really strange... When I logged in, **both** of my panels were missing :(
How can I get them back ??

---

### Post by fooman on 2008-08-14
try pressing the alt-f2 keys and see if a run dialog box pops up.  if it does type this into it:

```
gnome-panel &
```

---

### Post by wilbbe01 on 2008-08-14
If I were you my Obsessive Compulsive computer cleaning would kick in and I would probably figure out how to fix it then do a restore.....but.....maybe try creating a new user and logging in as that new user.  I think that would be the easiest in my opinion.   See if it works, if it does then maybe copy over the clean settings from your new users home directory, or just use the new user and copy your desired files over to them.

---

### Post by pikabuntu on 2008-08-14
so much weird stuff is happening. 
Now, I cant access the terminal and alt f2 will not respond

---

### Post by fooman on 2008-08-14
heres another thing you could try, press ctrl-alt-f1
that will drop you into a command line session.  when you get there log in, then type:

```
sudo apt-get install nautilus-open-terminal
```

after it installs, reboot the computer and when you get back to the desktop you should be able to right click on the screen and choose "open terminal"

when the terminal opens, type:

```
gnome-panel &
```

---

### Post by pikabuntu on 2008-08-14
> **fooman said:**
> heres another thing you could try, press ctrl-alt-f1
that will drop you into a command line session.  when you get there log in, then type:

```
sudo apt-get install nautilus-open-terminal
```after it installs, reboot the computer and when you get back to the desktop you should be able to right click on the screen and choose "open terminal"

when the terminal opens, type:

```
gnome-panel &
```

zach@zach-desktop:~$ gnome-panel &
[1] 10932
zach@zach-desktop:~$ A panel is already running.


](*,)

---

### Post by fooman on 2008-08-14
open terminal and try 

```
killall gnome-panel
```

then 

```
gnome-panel &
```

see if that works.

---

### Post by pikabuntu on 2008-08-14
what ended up working was 
sudo gnome-panel
:)

thanks for the help everyone!

---

### Post by pikabuntu on 2008-08-14
> **fooman said:**
> try pressing the alt-f2 keys and see if a run dialog box pops up.  if it does type this into it:

```
gnome-panel &
```
I saw somewhere that apparently, alt f2 only works when you have panels running

---

### Post by wilbbe01 on 2008-08-14
Do you need to type the gnome-panel after every log in?  Also for those of you with the ctrl+alt+Fkey comments; I think the alt+Fkey is when you are not in X.  When in X the alt+Fkey must be reserved or something, so you need the ctrl to get out.  Once out of 7 or whatever your gui is running on the alt+Fkey will work fine.  I'm not sure on that, but that is what I have gathered.

---

