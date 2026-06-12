---
title: "[SOLVED] launcher help"
date: 2008-11-14
forum: General Help
---

### Post by Stargazer989 on 2008-11-14
hey guys, I'm trying to find out if mIRC 6.21 has any bugs while running under wine. so when i click my launcher for it, i need a terminal to start up and run the wine command so i can figure out things.

i've tried gnome-terminal && wine /path/to/mirc/
as well as xterm && wine /path/to/mirc/
i've also used  wine /path/to/mirc/ ; xterm
got nothing.

any ideas ?

---

### Post by doas777 on 2008-11-14
is there a drop down list at the top of your create launcher window with the lable "Type: Application" ? if so, pull it down, and select "Application in Terminal".

good luck,
frank

---

### Post by Stargazer989 on 2008-11-15
it never occurred to me to see what the drop-menu does. TY! though the terminal closes when the program closes as well, any remedies ? (like a logging system or something)

---

### Post by doas777 on 2008-11-15
> **Stargazer989 said:**
> it never occurred to me to see what the drop-menu does. TY! though the terminal closes when the program closes as well, any remedies ? (like a logging system or something)

well one simple step is to redirect output to a file. you could change your launcher command to end with ```
 command > ~/outputfilename.txt
```.

---

