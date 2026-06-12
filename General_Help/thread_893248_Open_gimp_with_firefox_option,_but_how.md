---
title: "Open gimp with firefox option, but how?"
date: 2008-08-18
forum: General Help
---

### Post by Mb0742 on 2008-08-18
The new Firefox, I somehow ended up with an 'open with editor' option however I am using Ubuntu so of course there is no .exe to focus on is there anyway to do this? I have already tried hot linking it to a shortcut to no avail. Please help!

[Here](http://img201.imageshack.us/img201/5079/screenshotiy9.png)

---

### Post by mcduck on 2008-08-18
Just put the path to the program's exectuable there. For Gimp, like most of the other programs as well, the executable is in /usr/bin.

So, for gimp, I suppose the correct entry would be /usr/bin/gimp". You can check that by running "which gimp" in a terminal.

---

### Post by Mb0742 on 2008-08-18
Dam it won't start up :( Any other ideas?

---

### Post by fragos on 2008-08-18
"gimp %U"

---

### Post by Simstud on 2009-11-05
My solution: Install the firefox plugin "image assistant", which adds an "open image" option to the right click menu of an image. Problem is that the plugin opens gthumb and nothing else. So I typed: 

sudo ln -s /usr/bin/gimp /usr/bin/gthumb

Done.

WARNING: Don't do this if you have and use gthumb.

---

