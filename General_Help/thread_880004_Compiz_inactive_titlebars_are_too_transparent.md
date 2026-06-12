---
title: "Compiz inactive titlebars are too transparent"
date: 2008-08-04
forum: General Help
---

### Post by NTolerance on 2008-08-04
I can't seem to find the correct setting in the Compiz config settings manager for this.  Anyone got any ideas?  Thanks.

---

### Post by NTolerance on 2008-08-06
bump

---

### Post by NTolerance on 2008-08-08
bump

---

### Post by DaymItzJack on 2008-08-10
You need to look at emerald settings, not compiz settings.

System -> Preferences -> Emerald Theme Manager

Go to the "Edit Themes" tab, just click on the part that says "select engine" and then close out of the combo box for options to appear and find the inactive opacity settings on the right-ish side and change it to what you want. I'd suggest to save the custom theme you just made so you won't have to do this every time you reboot (.. not sure if it doesn't do it for you, I do it for myself though)

---

### Post by NTolerance on 2008-08-10
I don't have Emerald installed right now.  I suppose I need to install it if I want this level of control.  Do I have to use an Emerald theme or can I keep my current Metacity theme?  Thanks for your help.

---

### Post by SnoFox on 2010-01-09
Bump.

I'm not using Emerald with Compiz, but instead using gtk-window-decorator and Compiz. Inactive titlebars are way too transparent, does anyone know where I should look to fix this? Or even turn off that transparency? I'd rather have it off than it's current setting.

Thanks.

---

### Post by collinp on 2010-01-09
I'm surprised I even remember how to do this.

Open gconf-editor, like so (terminal command):
```
gconf-editor
```

Navigate to apps/gwd, I believe you will want to change the "metacity_theme_opacity" to a decimal number, 1 being no transparency and 0 being invisible.

There's also a few good guides on doing this, search for "Metacity Window Decoration Transparency".

---

### Post by SnoFox on 2010-01-09
Hellow++;

Thanks so much. :)

---

