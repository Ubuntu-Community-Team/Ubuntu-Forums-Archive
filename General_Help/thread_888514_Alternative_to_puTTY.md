---
title: "Alternative to puTTY?"
date: 2008-08-13
forum: General Help
---

### Post by G1ZmO65 on 2008-08-13
Is there an alternative to puTTY SSH client that runs on Ubuntu desktop that has copy/paste features?

puTTY runs great on my windows box and I can copy/paste code but I can't see how to copy/paste on the version on my ubuntu desktop.

I'm sure i'm just missing something silly but can't see it. lol

Ta

---

### Post by Nepherte on 2008-08-13
Just use the ssh command in the terminal? More information:
```
man ssh
```

---

### Post by jwaiwit on 2008-08-13
> **Nepherte said:**
> Just use the ssh command in the terminal? More information:
```
man ssh
```

use ssh is work great.

ssh host -lusername

copy & paste are available.

---

### Post by mcduck on 2008-08-13
To copy/paste with a terminal either use shift-ctr-c and shift-ctrl-v, or the unix style copypaste (highlight the text you wish to coopy & middle-click to paste).

..or if you want, the copy & paste functions are also available in the right-clik menu.

---

### Post by G1ZmO65 on 2008-08-13
Ok CTRL right-click gives me the menu which has the option COPY ALL

However it's not copying to the clipboard (or whatever the ubuntu equivalent is) When I try to paste in another application (gedit for example) there's nothing to paste.

Tried shift-ctr-c and shift-ctrl-v but get the same result (nothing to paste)

---

### Post by mcduck on 2008-08-13
Do you stil have the temriinal open when you try to paste? Because there really isn't any clipboard, you need to have both source & destination apps open to copypaste, if you close the terminal you can't paste any more..

---

### Post by G1ZmO65 on 2008-08-13
Yes both apps are open side by side

how to I make sure I have the latest version of puTTY?

If I click the ABOUT I get "PUTTY UNIDENTIFIED BUILD Nov 25 2007"

---

### Post by Nepherte on 2008-08-13
What about this: select the text you want to copy, right click and choose copy. Afterwards you right click on the place where you want the text to be pasted and you choose paste. This is how I've done it multiple times.

---

### Post by G1ZmO65 on 2008-08-13
I can select the text but right click does not do anything.

CTRL right-click brings up a menu with the COPY ALL option but selecting this then right clicking in gedit doesnt give me anything to paste.

It's frustrating as copy/paste works on my windows machine in putty fine and on the ubuntu machine in gedit it works fine but just not in putty on the ubuntu machine. Weird!

---

