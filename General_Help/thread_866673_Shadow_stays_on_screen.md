---
title: "Shadow stays on screen"
date: 2008-07-22
forum: General Help
---

### Post by whalogreg on 2008-07-22
I'm running into a problem with the shadow from any system windows that pop up on my screen... the shadow seems to stay on the screen once the window is closed, no matter what I've tried, the only way I've gotten this to clear up is after a reboot... any help..

---

### Post by ajmorris on 2008-07-22
hi there,
i notice you are running compiz. What happens if you try a different version of compiz, downgrade/upgrade your current version. Also, what paramaters, if any do you use to start compiz. and what output do you get if you start compiz through a terminal? 

AJ

---

### Post by iaculallad on 2008-07-22
Press the Alt+F2 combo and input **gconf-editor**, Navigate to apps->gksu, and uncheck (if checked) the value for **force-grab** (This fades the screen when gksudo and gksu are invoked for an application that needed authentication).

---

