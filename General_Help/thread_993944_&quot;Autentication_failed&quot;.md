---
title: "&quot;Autentication failed&quot;"
date: 2008-11-26
forum: General Help
---

### Post by freestyleren on 2008-11-26
So i've the following line by mistake, and now i can't login or anything:
> @include common-pamkeyring
How can i delete this line when i can't login? I'm relatively new to ubuntu. 

It's a dualboot with Win XP and when i try to boot XP it loads the desktop background and thats it.

All help apreciated.

---

### Post by Peter09 on 2008-11-26
Can you not remove this line from recovery mode?

It is unclear if you cannot log into windows or Ubuntu?

---

### Post by freestyleren on 2008-11-26
I can't log into ubuntu. I thought i could fix it from xp but that doesn't work either. Might not be the same problem though.

---

### Post by Peter09 on 2008-11-26
Can you get into recovery mode?

---

### Post by freestyleren on 2008-11-26
Yes.

---

### Post by Peter09 on 2008-11-26
So - then go to the file you entered the command in an edit it - is that possible?

---

### Post by freestyleren on 2008-11-26
When i write > gedit /etc/pam.d/gdmin the root, it says "Gtk-warning can't open display"

---

### Post by Peter09 on 2008-11-26
thats because your have no GUI running in recovery mode.

You can try

```
startx
```

that may give you a GUI.

if not then you need a text based editor, I use vi but thats not very nice if you have never used it before. However you could try nano which is a bit more friendly.

```
nano <file name>
```

---

### Post by dburnett77 on 2008-11-26
> **freestyleren said:**
> So i've the following line by mistake, and now i can't login or anything:

How can i delete this line when i can't login? I'm relatively new to ubuntu. 

It's a dualboot with Win XP and when i try to boot XP it loads the desktop background and thats it.

All help apreciated.

It's typically those of the BlueTooth access at these levels.  With many heads turned.  Lern't to expect it, as those brazenly challenging their dumbfoundedness are caught in the act.  Typical, for those sooo "special

---

### Post by freestyleren on 2008-11-26
> **Peter09 said:**
> thats because your have no GUI running in recovery mode.

You can try

```
startx
```

that may give you a GUI.

if not then you need a text based editor, I use vi but thats not very nice if you have never used it before. However you could try nano which is a bit more friendly.

```
nano <file name>
```
How do i save and exit the file in nano?

EDIT: I't worked. Thankyou very much for your patience, i really apreciate it.

---

### Post by Peter09 on 2008-11-26
<CNTRL><C> to save and <CNTRL><X> to exit

---

### Post by freestyleren on 2008-11-26
I't worked. Thankyou very much for your patience, i really apreciate it.

---

### Post by Peter09 on 2008-11-26
Thats OK - Glad to Help.

Best Mark the thread as solved.

---

