---
title: "[SOLVED] Main Toolbar Gone"
date: 2008-07-31
forum: General Help
---

### Post by ingeva on 2008-07-31
I must have done something stupid! :)

The main menu bar (the one that shows the navigation buttons) suddenly disappeared and I can't find a way to restore it!

I have tried every menu there is and all kinds of help without result.
I've used Ubuntu for less than a week so I need a lot of handholding! :)

---

### Post by iaculallad on 2008-07-31
Right-click on the top menu bar and select "Add to Panel", navigate to "Utilities" section and select "Menu Bar", click on the Add button.

---

### Post by ingeva on 2008-07-31
> **iaculallad said:**
> Right-click on the top menu bar and select "Add to Panel", navigate to "Utilities" section and select "Menu Bar", click on the Add button.

I wrote the tag "Nautilus" but forgot to mention it in the message text. Sorry!

There's no "Add to Panel" in the Nautilus top menu.

If you mean the launcher panel there's an "Add to Panel" but no "Utilities" section.

---

### Post by iaculallad on 2008-07-31
Ok. Press Alt+F2 and input "gnome-terminal" (that's w/o quote) and press enter. That will pop out your terminal and try to issue the following commands below to restore the defaults:

```
sudo gnome-session-remove gnome-panel
sudo gconftool-2 --recursive-unset /apps/panel
sudo gnome-panel &
```

---

### Post by ingeva on 2008-07-31
> **iaculallad said:**
> Ok. Press Alt+F2 and input "gnome-terminal" (that's w/o quote) and press enter. That will pop out your terminal and try to issue the following commands below to restore the defaults:


As far as I can understand this will affect the Gnome panel.
I don't want to touch that since I have installed a lot of applications in it.

However, I want the tools menu back in my Nautilus!
All I see now it the File, Edit, View etc. menues.

Before I try something drastic like the above, will it repair my Nautilus (Yes, I have removed and re-installed it which didn't do any good) or will it just reset the Panel?

A screen shot of my Nautilus, with the tools menu missing, is uploaded as an attachment.

---

### Post by silkstone on 2008-07-31
I don't have a tools menu in Nautilus, but I have other things which you don't. Have you tried clicking View and then making sure everything you want to see is selected. Or View > Reset View to Defaults.

---

### Post by ingeva on 2008-07-31
> **ingeva said:**
> However, I want the tools menu back in my Nautilus!
All I see now it the File, Edit, View etc. menues.

FOUND IT!

There's something called Spatial mode, and I evidently got switched to that while working with preferences.

I had a really hard time figuring out how this had happened, and looking for "Main toolbar" certainly didn't help much.

However, I came to read about spatial mode and browser mode, and finally I also found out how to switch between them. This information was very well hidden! :)

So, what I did was (In Nautilus):
Edit, Preference, Behaviour, then set/unset "Always open in Browser window".

Need I comment that I like it much better this way? :)

---

