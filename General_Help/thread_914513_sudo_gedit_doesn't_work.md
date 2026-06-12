---
title: "sudo gedit doesn't work"
date: 2008-09-08
forum: General Help
---

### Post by allspiritseve on 2008-09-08
I can launch gedit from the command line just fine... but if I try sudo gedit, it asks for my password and then just hangs. I've searched these forums and google, but I can't find a solution. Please help!

Cory

---

### Post by SuperSonic4 on 2008-09-08
use ```
gksudo gedit
```

[COLOR="Red"]gksudo[/COLOR] is used for GUI apps as root whereas [COLOR="Red"]sudo[/COLOR] is used in terminal

---

### Post by allspiritseve on 2008-09-08
I've used sudo gedit manu times before, and it worked fine.

I tried gksudo gedit, and that didn't work either. It did give me a new command line, but no gedit.

---

### Post by iaculallad on 2008-09-08
Care to post the error/message it displayed (if any) when you issued the command: **gksudo gedit**.

What happens if you do:

```
sudo -i
gedit
```

---

### Post by allspiritseve on 2008-09-08
I let it sit for a while, and gedit opened, but isn't responding. If I try to close it, it asks me to force quit. I have not received any errors. 

I tried what you just posted. On two lines, I got nothing. On one line, I got this:

```
root@spirit-laptop:~# sudo -i gedit
/usr/bin/gedit: /usr/bin/gedit: cannot execute binary file

```

---

### Post by iaculallad on 2008-09-08
> **allspiritseve said:**
> I let it sit for a while, and gedit opened, but isn't responding. If I try to close it, it asks me to force quit. I have not received any errors. 

I tried what you just posted. On two lines, I got nothing. On one line, I got this:

```
root@spirit-laptop:~# sudo -i gedit
/usr/bin/gedit: /usr/bin/gedit: cannot execute binary file

```

That would be a two command execution:

```
sudo -i
gedit
```

One command at a time.

---

### Post by cdaringe on 2008-09-08
i assume you've already tried uninstalling/reinstalling?

---

### Post by allspiritseve on 2008-09-08
> **iaculallad said:**
> That would be a two command execution:

```
sudo -i
gedit
```

One command at a time.

No, right, I tried that. Nothing happened so I tried it on one line.

---

### Post by allspiritseve on 2008-09-08
> **cdaringe said:**
> i assume you've already tried uninstalling/reinstalling?

Yep, I tried that. Still won't work.

---

### Post by LowSky on 2008-09-08
uninstall gedit

then delete the folder /usr/lib/gedit

then reinstall

---

### Post by allspiritseve on 2008-09-08
> uninstall gedit

then delete the folder /usr/lib/gedit

then reinstall 

Nope, same problem.

**Edit: it appears to be working now. Unfortunately I don't know what I did, so I can't help anyone else with the same problem.**

---

