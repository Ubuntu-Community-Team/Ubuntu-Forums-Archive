---
title: "[SOLVED] Move titlebar buttons to the right? (close / minimize / maximize)"
date: 2008-10-07
forum: General Help
---

### Post by NHansen on 2008-10-07
Hello. Not sure if this can be done, but I've searched through desktop appearances and emerald, and unless I overlooked something, I can't seem to find a way to move the 3 buttons (close/min/maximize) all the way to the right (I am using the Ubuntu Studio theme)
Sorry if this is a n00bish question, I just can't seem to find it for the life of me!
Thank you :]

---

### Post by Soupcan on 2008-10-07
Go to the Emerald Theme Manager. Click on the theme you want to edit, then the "Edit Themes" tab at the top. Then click the Titlebar tab. The "Title-bar Object Layout" box is what you are looking for.

---

### Post by NHansen on 2008-10-07
It's not an emerald theme, though.. Changing that stuff seems to do nothing to the Ubuntu Studio theme.

---

### Post by NHansen on 2008-10-07
aha! I had to run gconf-editor, go to apps>metacity>general and change the button_layout value.
Yay!

---

