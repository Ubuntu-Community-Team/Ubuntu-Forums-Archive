---
title: "[SOLVED] Delay"
date: 2008-08-10
forum: General Help
---

### Post by PCessna on 2008-08-10
Hey all,

Currently to run avant-window-navigator, I am have a session entry as the program name and command as avant-window-navigtor.
Works fine, But is there anyway I can delay it from starting for like 5 seconds.  

Because when gnome, x-window, metacity, and etc start, it looks like white crap for a few seconds until everything loads, so I figure a delay which I don't care how long it takes to load anyways should fix this

Thanks

---

### Post by RealPSL on 2008-08-10
Instead of starting awn directly use a script. I just put a script like the one below in my home directory and point the sessions entry to it. You can change the the script below with gedit. I do not have awn so you will need to make sure it works.

```
#!/bin/bash
#
# Purpose: Start awn after a 10 second delay


sleep 10 && /usr/bin/avant-window-navigtor
```

I would call the file something like rc.awn

---

### Post by PCessna on 2008-08-10
> **RealPSL said:**
> Instead of starting awn directly use a script. I just put a script like the one below in my home directory and point the sessions entry to it. You can change the the script below with gedit. I do not have awn so you will need to make sure it works.

```
#!/bin/bash
#
# Purpose: Start awn after a 10 second delay


sleep 10 && /usr/bin/avant-window-navigtor
```

I would call the file something like rc.awn
Thankies :D

---

### Post by PCessna on 2008-08-10
> **PCessna said:**
> Thankies :D
doesn't work.. sorry :(

---

### Post by PCessna on 2008-08-11
> **PCessna said:**
> doesn't work.. sorry :(

Good lord, another ignore session, here are some details.

In execution of his script, it flashes 10 seconds for delay and crashes,

Thanks
-PCessna

---

### Post by RealPSL on 2008-08-11
Do you mean awn crashes? Does it give any error messages? Can you run the script from the command line?

---

### Post by PCessna on 2008-08-12
> **RealPSL said:**
> Do you mean awn crashes? Does it give any error messages? Can you run the script from the command line?

No.No. I just want a script that works with Hardy 64-bit without crashing with no error messages. AWN doesn't crash.
Here:
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
10th second when launch should happen:
crash. (terminal)

AWN is as stable as hell, I think it may
just be the script.

---

### Post by PCessna on 2008-08-13
> **PCessna said:**
> No.No. I just want a script that works with Hardy 64-bit without crashing with no error messages. AWN doesn't crash.
Here:
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
Terminal cursor blink
10th second when launch should happen:
crash. (terminal)

AWN is as stable as hell, I think it may
just be the script.
bump

---

### Post by PCessna on 2008-08-13
> **PCessna said:**
> bump

:mad::mad::mad: can someone PLEASE answer!

---

### Post by PCessna on 2008-08-14
> **PCessna said:**
> :mad::mad::mad: can someone PLEASE answer!

bump, can someone please answer

---

### Post by RealPSL on 2008-08-16
I am not sure this is the source of your problem but since you have not provided an error message. The navigator was misspelled (missing second a) in the previous entries.

```
#!/bin/bash
#
# Purpose: Start awn after a 10 second delay


sleep 10 && /usr/bin/avant-window-navigator
```

---

### Post by PCessna on 2008-08-16
> **RealPSL said:**
> I am not sure this is the source of your problem but since you have not provided an error message. The navigator was misspelled (missing second a) in the previous entries.

```
#!/bin/bash
#
# Purpose: Start awn after a 10 second delay


sleep 10 && /usr/bin/avant-window-navigator
```

Ty. Fixed.

---

### Post by PCessna on 2008-11-12
> **PCessna said:**
> Ty. Fixed.

I am trying to use this again, and wine is manning all file extensions, what should it "open with" thanks.

---

### Post by geirha on 2008-11-13
> **PCessna said:**
> I am trying to use this again, and wine is manning all file extensions, what should it "open with" thanks.

Just "Open". It must be executable though, so check the permissions tab in the file's properties.

---

