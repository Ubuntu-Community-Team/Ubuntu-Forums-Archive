---
title: "Installing BIN files?"
date: 2008-08-04
forum: General Help
---

### Post by jras20 on 2008-08-04
What command do I need to do to install BIN files?  This is the only thing I am stuck on now on Ubuntu.  I just need to know what code to type in.  Everything else I got it pretty well down.
Thanks!

---

### Post by munkyeetr on 2008-08-04
```
sh filename.bin
```

---

### Post by jras20 on 2008-08-04
> **munkyeetr said:**
> ```
sh filename.bin
```
Thanks

---

### Post by oldos2er on 2008-08-04
> **jras20 said:**
> What command do I need to do to install BIN files?  This is the only thing I am stuck on now on Ubuntu.  I just need to know what code to type in.  Everything else I got it pretty well down.
Thanks!

 First make it executable: chmod a+x filename.bin
 Then run it: ./filename.bin

---

### Post by Ataris on 2008-08-04
Yeah, I think sh is supposed to be used for .run files, but I suppose it would work for .bin files too.

---

### Post by loboc on 2008-08-04
> **jras20 said:**
> What command do I need to do to install BIN files?  This is the only thing I am stuck on now on Ubuntu.  I just need to know what code to type in.  Everything else I got it pretty well down.
Thanks!

Once you chmod it to mae it executable you can copy the executable to 
/usr/local/bin 

```
sudo cp foo.bin /usr/local/bin
```

and then it will be on all users paths, 

If its just for you you can create a directory for your scripts in your home folder

```
 mkdir ~/bin
``` 

then 

```
 gedit ~/.bash_profile 
```

and copy paste this text into it  

```

PATH=$PATH:~/bin
export PATH

```

if you want an ASCII TUX to read you your fortune everytime you login at one of the TTY (CTRL+F1 - F5) do this 

```
 sudo apt-get install fortune cowsay
```

and add this to the last line of .bash_profile
```

fortune | cowsay -f tux.cow

```

If you want your fortune every time you open a gnome terminal open a terminal and click

EDIT>PROFILES
Choose the Default Profile
Click the Edit Button 

Select the Title and Command Tab 

Click the "Run command as a login shell"
so gnome terminal will read the bash_profile and execute it faithfully

---

