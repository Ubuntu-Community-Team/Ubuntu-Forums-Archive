---
title: "Title bar dissapear when windows is maximized"
date: 2008-08-12
forum: General Help
---

### Post by link- on 2008-08-12
I recently installed Emerald Theme Manager to customize the window border, 
to make it look a little clear with the true glass engine. Now it looks the way I wanted but theres is a problem, when the windows is maximized the tittle bar gets completely clear, unable to see the bar and the buttons on the top right of the bar.

-link

---

### Post by S.A.A on 2008-08-13
edit your /etc/X11/xorg.conf, and add these two lines to "screen" section:
        
        Option          "AddARGBVisuals" "true"
        Option          "AddARGBGLXVisuals" "true"

---

### Post by onecuwldood on 2008-09-17
I'm not sure if this helped link- or not, but I'm having the same problem and it did not fix mine... Still searching for a fix for this.

Any other ideas?

---

### Post by onecuwldood on 2008-09-17
link-,

I may have just found a solution to mine, maybe it will help...

Open "Emerald Theme Manager" from the Compiz Fusion icon.
In the "Emerald Settings' tab I unchecked "Use Decoration Cropping" and my title bar came back.
I still have the above changes to /etc/X11/xorg.conf that S.A.A suggested. I've not tried to go back and take those changes out yet.

---

### Post by egyptianbman on 2011-08-18
The unchecking of "Use Decoration Cropping" did the work for me, thanks!

---

