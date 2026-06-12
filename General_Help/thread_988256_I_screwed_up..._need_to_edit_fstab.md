---
title: "I screwed up... need to edit fstab"
date: 2008-11-20
forum: General Help
---

### Post by rbw3689 on 2008-11-20
I wish I didn't have to create another help topic, but I can't find a sufficient answer anywhere and I've been searching for awhile now.

I did something to my fstab file and screwed it up completely. (I was trying to solve an issue and created another one, basically.) The GUI interface won't load now. I am trying to use nano to edit the file.

Here is what I'm doing, after it prompts me to enter my username/password:

```
sudo nano /etc/fstab
(enter password)
```

File opens, I make my changes... when I go to save it, it doesn't save, telling me it's read-only. I thought that's what "sudo" was supposed to be for...? I've used it before, obviously, but with gedit.

Any help appreciated, thanks.

---

### Post by taurus on 2008-11-20
What's the output of this command?

```
ls -la /etc/fstab
```

---

### Post by Peter09 on 2008-11-20
If you are in recovery mode then you already have admin privileges. So you do not need the sudo part of it.

If you are not in recovery mode it might be worth trying that way.

---

### Post by rbw3689 on 2008-11-20
Sorry... I bailed out and reinstalled Ubuntu. (I only installed it yesterday, so no big loss... I actually solved a couple of my other problems in the process.)

I had tried to get into recovery mode, but for some reason couldn't do it. Also, I know for a fact that root had read/write access to the file (and I did double check with the ls -la command).

Thanks for the suggestions, anyway. :) It was appreciated.

---

### Post by editrix on 2008-11-20
> **rbw3689 said:**
> I did something to my fstab file and screwed it up completely. 
Been there, done that--as have we all :-)

> **rbw3689 said:**
> Sorry... I bailed out and reinstalled Ubuntu.

Been there, done that, too. :biggrin:

---

