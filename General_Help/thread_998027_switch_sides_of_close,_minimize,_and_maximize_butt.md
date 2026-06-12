---
title: "switch sides of close, minimize, and maximize buttons"
date: 2008-11-30
forum: General Help
---

### Post by zuknivek on 2008-11-30
I installed mac4lin and now when i change my appearance back to what i had the close, minimize, and maximize buttons are still on the opposite sides.

To get a better understanding of what I'm asking look at attached picture.  

[IMG]http://i299.photobucket.com/albums/mm305/zuknivek/screenshot-1.jpg[/IMG]

---

### Post by Forlong on 2008-11-30
Are you using Emerald?

If not, what's the output of:
```
gconftool-2 -g /apps/metacity/general/button_layout
```

---

### Post by zuknivek on 2008-11-30
I am using emerald

---

### Post by seren6ipity on 2008-11-30
How did you uninstall Mac4ln? Did you use the uninstall shell script in the package. Because that fixes the window options.

Make sure that you have selected the correct **icon** theme.

---

### Post by Forlong on 2008-12-01
> **zuknivek said:**
> I am using emerald
Then a) try another Emerald theme or b) configure the current one in Emerald Theme Manager

If you can confirm a) works, I can tell you how to do b) (I'll have to install Emerald Theme Manager for that).

---

### Post by zuknivek on 2008-12-06
> **seren6ipity said:**
> How did you uninstall Mac4ln? Did you use the uninstall shell script in the package. Because that fixes the window options.

Make sure that you have selected the correct **icon** theme.

I didn't uninstall with the shell script. This fixed the problem. Thank you!

---

