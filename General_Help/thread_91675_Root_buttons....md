---
title: "Root buttons..."
date: 2005-11-17
forum: General Help
---

### Post by gts on 2005-11-17
In kde it is very easy to assign a root script to a button: in every voice of the application menu there is a "exec as other user" (or something like this) option, where you can write "root". Then you can add a button everywhere you want in the panels of the desktop. When you press the button, you put the password in a window and finally the script is executed. 

I can't find any way to do this in gnome... 

Can anyone help me?

---

### Post by RAOF on 2005-11-17
You can put "gksudo" before the script to run, and it'll graphically ask for a password before running the script.

So, rather than having a button running "foo.sh", you'd have a button running "gksudo foo.sh"

---

### Post by soulestream on 2005-11-17
you can use gksudo and just enter the password or

use gksudo and edit your sudoers file and add that app to not ask for a password

soule

---

### Post by gts on 2005-11-17
I've tried to create a new button with these commands:

gksudo /home/gts/Custom components/scripts/wlan.sh

gksudo '/home/gts/Custom components/scripts/wlan.sh'

gksudo "/home/gts/Custom components/scripts/wlan.sh"

but no one of these works...

any other suggest?

thanks anyway

---

### Post by RAOF on 2005-11-17
By "none of these works", I presume you mean that they all error out, saying they can't find the script?

You could try
```

gksudo /home/gts/Custom\ components/scripts/wlan.sh

```
Notice the backslash.  Spaces in filenames aren't easy to work with :)

---

### Post by gts on 2005-11-17
Thank you RAOF, I've done the work in a more drastic way :D 

gksudo /home/gts/Custom/scripts/wlan.sh

I've changed the name of the guilty directory...

---

