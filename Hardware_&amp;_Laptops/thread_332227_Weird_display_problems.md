---
title: "Weird display problems"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by valkarin on 2007-01-05
Two weeks ago, I installed the wrong nvidia binary driver.  since then, my screen will occasionally darken and the res will slowly change to 800X600 then slowly change back.  The change is smooth, but annoying.  I have fixed the driver and now have the correct one running as far as I know.  I don't get an nVidia splash screen, but direct rendering is on.  can anyone help me with this?  Suggestions, hints?

---

### Post by ingo on 2007-01-07
No splash screen but 3D support and rendering? Weird. How many frames per second do you get when you run glxgears from the shell?

Also which NVidia card are you running and which driver did you install? If you cannot remember run

> lshw

and

> nvidia-settings

and it will tell you.

---

