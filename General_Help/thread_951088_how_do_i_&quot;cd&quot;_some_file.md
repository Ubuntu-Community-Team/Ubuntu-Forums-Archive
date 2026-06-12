---
title: "how do i &quot;cd&quot; some file?"
date: 2008-10-17
forum: General Help
---

### Post by reinaldistic on 2008-10-17
a theme is asking me to do it "in the instructions" and it tells me to fist cd the folder where a script is at, yet when i type  sudo cd home/myusername/desktop/nameoffolderdesktopwherefileisat it says cd command was not found
im sure im doing it wrong, i just guessed the code

---

### Post by jerome1232 on 2008-10-17
Why are you using sudo? You shouldn't need that.

Instead of typing home/usernamehere/folder you should use either:

```
cd ~/Desktop/folder
# or
cd /home/usernamehere/Desktop/folder
# note the / before home it's important, otherwise it looks in your present home directory for a 'home' folder.
```
If you need to use cd as root (very few instances where this is required) then get a root shell (sudo -i) then cd in.

---

### Post by Fixman on 2008-10-17
> **reinaldistic said:**
> a theme is asking me to do it "in the instructions" and it tells me to fist cd the folder where a script is at, yet when i type  sudo cd home/myusername/desktop/nameoffolderdesktopwherefileisat it says cd command was not found
im sure im doing it wrong, i just guessed the code

Its Desktop, not desktop (case sensivity)

EDIT: And /home, not home

ANOTHER EDIT: Did you remember to decompress the file before CD'ing to it?

Anywyay, the best way to install themes is to go to system->preferences->appareance, pressing in "install" and selecting the file (compressed, not the folder).

---

