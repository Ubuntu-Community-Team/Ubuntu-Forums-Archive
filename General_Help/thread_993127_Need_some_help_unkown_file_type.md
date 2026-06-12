---
title: "Need some help unkown file type"
date: 2008-11-25
forum: General Help
---

### Post by theplastikjesus on 2008-11-25
I'm new to linux, i got ubuntu up and running with no problem what so ever. I'm trying to open a picture i took of my desktop at work on windows and it says unkown file type. Is there something i can download in windows to show this file to a friend of mine?

---

### Post by lifestream on 2008-11-25
What file type is it? What is the extension? .png .gif .jpg .psd
Or... does it not have any extension ?

---

### Post by theplastikjesus on 2008-11-25
It has no extension, I used Print Screen in linux to snap a shot of desktop then emailed it to myself to show my friend at work. Now i cant open it in windows, at work.

---

### Post by toallpointswest on 2008-11-25
Try 
```

file <filename>

```

and see what it says.

---

### Post by solitaire on 2008-11-25
Rename it to: ```
<filename>.PNG
```
Then Windows should open it. (Windows is stupid like this! If it does not see a file extension, it turns into a quivering wreck and says it is an unknown file type.)

---

### Post by theplastikjesus on 2008-11-25
> **solitaire said:**
> Rename it to: ```
<filename>.PNG
```
Then Windows should open it. (Windows is stupid like this! If it does not see a file extension, it turns into a quivering wreck and says it is an unknown file type.)
Thank you, that worked. I love Ubuntu, flawless install here!

---

### Post by ajgreeny on 2008-11-25
Yes, strange isn't it that windows can't work out what file type it is trying to work with, yet by default it does not show the file extensions of registered, associated files if I remember correctly.  Not as clever as Linux, where you can put any file extension on a saved file and it's still recognised as what it really is, not what you have suggested it may be simply from the three end letters.

---

