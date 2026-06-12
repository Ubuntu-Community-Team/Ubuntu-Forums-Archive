---
title: "Conky in the foreground when logging on?"
date: 2008-09-18
forum: General Help
---

### Post by Melindrea on 2008-09-18
I have a problem. I've set up so that conky should start with my session. It does, however it also lies in the foreground not in the background. If I close it and reopen it, or just open it manually, that problem isn't there.

I used a .conkyrc that I found on the mega thread, with some edits to suit colouring and such better.

If anyone has a solution, I'd be a very happy camper!

//Melindrea

---

### Post by zxscooby on 2008-09-18
Are you using compiz? If so you might have to delay the start
of compiz by a second or two so it doesn't draw a window around
conky when it starts.

---

### Post by SkonesMickLoud on 2008-09-18
It sounds like you're using compiz, and compiz is drawing shadows around conky.  Simple fix:

Open your startup list and edit the Conky entry to read:

```
sleep 5 && conky
```

Restart X (Ctrl+Alt+Backspace) and re-login.  Shouldn't be an issue anymore, but if it is, increase the sleep time.

---

### Post by Melindrea on 2008-09-18
Hrm. That only led to conky not starting at all...

BUt it does sound like it's compiz that's messing things up, thanks. =)

---

### Post by SkonesMickLoud on 2008-09-18
> **Melindrea said:**
> Hrm. That only led to conky not starting at all...

BUt it does sound like it's compiz that's messing things up, thanks. =)

This used to happen to me on 7.10.  Found a workaround by creating a bash script and having that started instead of Conky.  Mine looks like this:

```

#!/bin/bash
sleep 10 &&
conky -d -c /home/skones/.conkyrc
exit

```

Just replace your conky entry with this as "sh */path/to/scriptname*.sh" after you make it executable.

Oddly enough, I don't have any need for it anymore as I don't use compiz.  Old habits die hard I guess.

---

### Post by John Baptist on 2009-07-14
I had this problem under Jaunty. The sleep trick didn't work for me, and, anyway, I think I should be able to see conky as soon as I log in. The solution that I found is to create a .gnomerc file that loads conky. This works much better than the "start up apps" control panel. (If you aren't using GNOME, this won't work, of course.)

---

