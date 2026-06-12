---
title: "screensaver"
date: 2008-08-09
forum: General Help
---

### Post by fdny343 on 2008-08-09
just installed harvey from disc. everything at the time....perfect. chose my screensaver and set the times for it to appear. went on with no problems.
added a few applications and now when I chose screensaver I cannot make changes, my mouse freezes up and the screen goes black. right after this occurs, the tan username screen pops up. any thoughts?

---

### Post by Diabolis on 2008-08-09
> **fdny343 said:**
> right after this occurs, the tan username screen pops up. any thoughts?

You mean the log in window (GDM), right?

If that is right, what happened is that your xserver crashed. You can find the x11 server log here: **/var/log/Xorg.0.log**

---

### Post by fdny343 on 2008-08-09
sorry, but how do I get to that file/server?

---

### Post by Diabolis on 2008-08-09
Open it with any text editor, for example gedit:
```
gedit /var/log/Xorg.0.log
```

---

### Post by fdny343 on 2008-08-09
do I use that in the search engine? where is that command entered?

---

### Post by Diabolis on 2008-08-09
In a terminal: **Accesories / Terminal**

---

### Post by fdny343 on 2008-08-09
please understand I'm very new to this system. where do I find this terminal? think like your talking to a kid.

---

### Post by Diabolis on 2008-08-09
Assuming that you installed Ubuntu and that you haven't changed many of its default values.

In your upper panel, you have a menu that says applications, go to Accesories and there you'll find the terminal.

---

### Post by fdny343 on 2008-08-09
ok. I think I found it. how do I fix it? do I reset and clear?

---

### Post by fdny343 on 2008-08-09
how do I check to see if any default values have been changed?

---

### Post by Diabolis on 2008-08-09
If an error in xserver occurred, it will appear in the last lines of the file.

---

### Post by fdny343 on 2008-08-09
should I just reload ubuntu? no such faults were found.

---

### Post by Diabolis on 2008-08-09
Just to get this right, it crashes only when the screensaver show up?

---

### Post by fdny343 on 2008-08-09
well I dont know what I did, but I think I fixed it. keep you posted.

---

### Post by Diabolis on 2008-08-09
ok :confused:

If everything is fine, great. come to ask anytime, there will be always someone that will offer you a solution.

---

