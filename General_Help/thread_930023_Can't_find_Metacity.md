---
title: "Can't find Metacity"
date: 2008-09-25
forum: General Help
---

### Post by tommygunner on 2008-09-25
I am trying to figure out how to do control alt delete to map to the system monitor and the I'm told to click on "metacity" under

Applications/System Tools

I don't see any such thing. I typed metacity into Synaptic but nothing came up. I typed metacity into the terminal and nothing came up.

Where can I find this application?

---

### Post by tommygunner on 2008-09-25
Ok, I think I found it by typing "gconf-editor" but I'm still not sure why it is referred to as "metacity."

---

### Post by anotherdisciple on 2008-09-25
Click on (System > Preferences > Keyboard Shortcuts)


Change the system monitor shortcut to ctrl+Alt+delete


Also, like you said... in gconf-editor under (Apps > Metacity > global keybindings) you can change it.

---

