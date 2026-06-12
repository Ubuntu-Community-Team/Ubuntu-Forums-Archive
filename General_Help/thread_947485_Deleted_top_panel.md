---
title: "Deleted top panel"
date: 2008-10-14
forum: General Help
---

### Post by nyborjare on 2008-10-14
Need help.
I have by accident deleted the top panel....:confused:

Please help me get the thing back. 
Cannot use my Ubuntu as of now....

Any support in this matter is appreciated

Regards
Michael

---

### Post by polki@mac.com on 2008-10-14
Just right click another panel and "Add panel". Place it on top and keep adding what you want to the new top panel.

---

### Post by geirha on 2008-10-14
You can reset the panels to the way they look for a freshly created user by typing this in a terminal:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

### Post by nyborjare on 2008-10-14
> **geirha said:**
> You can reset the panels to the way they look for a freshly created user by typing this in a terminal:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

How can I start a Terminal on a blank desctop???

Sorry I am new to all this
Michael

---

### Post by Sam on 2008-10-14
Alt-F2, type "gnome-terminal" then click "Run", then type what geirha said.

---

### Post by nyborjare on 2008-10-14
> **Sam said:**
> Alt-F2, type "gnome-terminal" then click "Run", then type what geirha said.

Sam

Thank you will give it a try and report.
Michael

---

### Post by nyborjare on 2008-10-14
> **nyborjare said:**
> Sam

Thank you will give it a try and report.
Michael

OK all set...:)
Thank you all för your support in this.
I am a happy Ubuntu user again  :)

Michael

---

### Post by Sam on 2008-10-14
> **nyborjare said:**
> OK all set...:)
Thank you all för your support in this.
I am a happy Ubuntu user again  :)

Michael

You're welcome! Enjoy ;)

---

### Post by naknak987 on 2008-10-19
When I type that in I get this in my face.

gnome-panel: no process killed

---

### Post by geirha on 2008-10-19
> **naknak987 said:**
> When I type that in I get this in my face.

gnome-panel: no process killed

Sounds like you might have uninstalled the gnome-panel somehow? If you have, try getting gnome back to normal with ```
sudo aptitude install ubuntu-desktop
``` If the panel just haven't started already, running ```
gnome-panel
``` in the terminal should show the panels again.

---

### Post by HornedOne on 2008-10-19
> **geirha said:**
> Sounds like you might have uninstalled the gnome-panel somehow? If you have, try getting gnome back to normal with ```
sudo aptitude install ubuntu-desktop
``` If the panel just haven't started already, running ```
gnome-panel
``` in the terminal should show the panels again.

I had the same problem as the OP....I managed to delete that part of the panel, and using that line did the trick.  Thanks guys :D

---

