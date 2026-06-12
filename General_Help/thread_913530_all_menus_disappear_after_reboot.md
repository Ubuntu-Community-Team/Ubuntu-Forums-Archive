---
title: "all menus disappear after reboot"
date: 2008-09-07
forum: General Help
---

### Post by yskhatib on 2008-09-07
i just restarted ubuntu (8.04) normally and after logging in I find no top nor bottom menu!! the desktop files appear but there is nothing else i can do.

this has happened before and i had to reinstall ubuntu. i cannot go through this again. is there a way to fix it, please???

---

### Post by stoneage on 2008-09-07
If restarting doesn't help, try entering 'gnome-panel' in a terminal.

Or Try 'Press Alt+F2 and input command gconf-editor to open Configuration Editor, go to app > panel > general and open toplevel_id_list , then you should be able to add a panel there - "top_panel_screen0" or "bottom_panel_screen0"'

Hope this helps.

---

### Post by yskhatib on 2008-09-07
thanks for your quick reply.

Alt+F2 doesn't work. Ctrl+Alt+F1 works, but it tells me that:
"The program 'gnome-panel' is currently not installed."
Wierd. Tried installing it using apt-get as suggested but it failed to fetch some archives. :confused:

Tried gconf-editor, but it says "cannot open display".

Any other ideas?

---

### Post by Predator106 on 2008-09-07
What exactly did you change? Did you install/uninstall packages? Or did you literally just install, boot up, login and then reboot and nothing else significant..

What is the error that apt-get?

Just some little helper questions, hopefully it will help someone (if not me) fix your problem.

---

### Post by stoneage on 2008-09-07
Not really, sounds like it may be more complicated than a missing panel.

Did you look in Synaptic to see if it is installed there? (Enter 'synaptic' in a terminal)
And maybe look at sources.lst to see if sources are enabled. 
Puzzling...          ....you are using Ubuntu, not Kubuntu ?

---

### Post by yskhatib on 2008-09-07
thanks for your replies.

ok, i think i did it.

the reason apt-get didnt fetch the libraries was that the (global gnome) proxy settings were not exported (i assume), so after exporting it manually apt-get worked.

i looked around the forums like a maniac, tried half a dozen of things and i think what worked was:
 - removing compiz completely
 - resintalling gnome-panel
 - rebooting

i get a couple of errors after logging in now, but at least the panels appear!!


thanks a lot guys! :)

---

### Post by yskhatib on 2008-09-07
> **stoneage said:**
> ....you are using Ubuntu, not Kubuntu ?
Yep. Ubuntu.

---

### Post by stoneage on 2008-09-07
Glad to hear it, but I wonder how it got uninstalled in the first place.

---

### Post by Predator106 on 2008-09-08
You get a couple of errors before logging in? What are they, if you don't mind me asking.

---

### Post by yskhatib on 2008-09-11
> **Predator106 said:**
> You get a couple of errors before logging in? What are they, if you don't mind me asking.

The errors were after logging in. They occured the first time I logged in with the panels appearing, but now they don't appear on reboot. Sorry, I forgot what they were. I think they were related to a missing configuration file, and I just pressed 'Ignore'.

---

