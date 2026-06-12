---
title: "[SOLVED] Can't Add files"
date: 2008-07-23
forum: General Help
---

### Post by jkyahoo101 on 2008-07-23
I want to add sound files to /usr/share/sounds but it won't let me add them. It just gives a permission denied error. I also can't browse to the appropriate file. When I do it doesn't play at all. They are the right file format and I know that the files work. How do I fix the permission denied thing?

---

### Post by the_real_fourthdimension on 2008-07-23
> **jkyahoo101 said:**
> I want to add sound files to /usr/share/sounds but it won't let me add them. It just gives a permission denied error. I also can't browse to the appropriate file. When I do it doesn't play at all. They are the right file format and I know that the files work. How do I fix the permission denied thing?

For the permission denied, run "gksudo nautilus" in your terminal.  Then drag and drop like normal.

---

### Post by tuxxy on 2008-07-23
To copy the files into usr/sounds by drag & drop you need to open nautilus in sudo mode

```
gksudo naultius
```

Now try and drag/copy them in, for your permissions try and right click on the folder and edit them from here if still now luck.

---

### Post by jkyahoo101 on 2008-07-23
It still says permission denied. I can't edit the permissions because it says I am not the owner.

---

### Post by tuxxy on 2008-07-23
Try to change ownership of the file at terminal first;

```
chown -r user file/dir
```

Now run the sudo nautilus;

```
gksudo nautilus
```

---

### Post by jkyahoo101 on 2008-07-23
I am not too sure on how to use that command. could you maybe give an example?

---

### Post by tuxxy on 2008-07-23
open terminal

```
chown -R jkyahoo101 /home/jkyahoo101/Desktop/sounds
```

This is an example for changing ownership of the directory called sounds on the desktop, for a file just add the filename and extension to the end.

---

### Post by jkyahoo101 on 2008-07-23
Thanks a lot that worked.

Well it kinda worked. The file was placed in the right spot but the sound won't play.

Just to be clear I want to change the login screen ready sound. Instead of the existing 2 beats I want it to play my custom sound. It is in a wav format.

---

