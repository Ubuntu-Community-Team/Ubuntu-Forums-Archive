---
title: "Login Screen too large"
date: 2008-08-13
forum: General Help
---

### Post by zieglerj on 2008-08-13
The resolution for my login screen is drastically different than the resolution when I log-in. It's so large that it doesn't fit on the screen. Is there any way to fix it?

---

### Post by S.A.A on 2008-08-13
to fix it do the following:

1) Make a Backup of your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

2) Open xorg.conf

sudo nano /etc/X11/xorg.conf

3) Locate your Screen Entry

Section "Screen"

You will find multiple entries similar to:

        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768"
        EndSubSection

The First Entry in the "Modes" Line is what GDM will use, so change it to something lower/higher (Please make sure you know that your monitor and Graphic Card BOTH support this Resolution). Save the file.

Close all running applications, restart GDM (/etc/init.d/gdm restart). Another way is just to log out your ubuntu session and press Ctrl-Alt-Backspace in the login screen. Look if everything went fine.

If the specified display resolution - "1280x1024" in the case above - differs from the used virtual screen resolution, add a respective line in the Display subsection of xorg.conf:

Virtual 1280 1024 

If these changes did not help, you can always use:

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

to restore your system to the previous state.

---

### Post by sayakb on 2008-08-13
If your problem is resolved, please mark the thread as solved (Thread tools->Mark thread as solved)

---

