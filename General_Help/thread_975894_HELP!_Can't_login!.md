---
title: "HELP! Can't login!"
date: 2008-11-08
forum: General Help
---

### Post by ECas123 on 2008-11-08
Alright so my videos were flickering alot and I found a post ( [http://ubuntuforums.org/showpost.php?p=4510147&postcount=7](http://ubuntuforums.org/showpost.php?p=4510147&postcount=7) ) and was following it along. I got to 

4. Change to a virtual terminal with: Ctrl+Alt+F1-6 and issue the following commands to restart gdm:
Code:
```
sudo /etc/init.d/gdm stop
```

But I forgot to hit Ctrl+Alt+F1-6 and just typed it into the regular terminal. My computer just started showing me black and white text now I don't know what to do. I'm using the livd CD desktop and I really need some help to get back into my regular desktop urgently. Please, anyone?

---

### Post by cyfur01 on 2008-11-08
You should still be able to drop to a virtual terminal (Ctrl+Alt+F1). From here, execute: ```
/etc/init.d/gdm start
```
This should launch you back into an X session, though all your previous windows will be closed.

Alternatively, since you're running an live-session, you can restart your computer and re-start the live session.

---

### Post by Iowan on 2008-11-08
That black/white text *might* be a terminal - what does it say?  A regular terminal will require a login.

---

### Post by cyfur01 on 2008-11-12
I tried this out on a virtual machine...

> **Iowan said:**
> That black/white text *might* be a terminal - what does it say?
I gave this a try and it's a printout from shutting down the gdm session. It doesn't result in an interactive terminal, more of just a log (very similar to Ctrl+Alt+F8 ). However, Ubuntu is still smart enough to allow you to switch to the other virtual terminals.

> **Iowan said:**
>  A regular terminal will require a login.
Normally, yes. During a live session, no (It will automatically be logged in as ubuntu@ubuntu).

---

