---
title: "ATI express driver Resolution problem"
date: 2008-06-20
forum: Hardware
---

### Post by jpfguambe on 2008-06-20
I Installed ATI driver on Ubuntu Hardy in order to run the all wonder Compiz-Fusion and AWN.
Before the installation of the driver i was running with 1280x1024.
After the installation of the driver compiz-fusion was running wow, but my maximum resolution was 1024x768.

How can i have 1280x1024 resolution?

---

### Post by nickdbliss on 2008-06-21
Ok go to the terminal under Applications>Accessories>Terminal

and type this
#sudo gedit /etc/X11/xorg.conf

Scroll down where it says Section "Screen"
Before EndSection Insert the following:

SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection

Save, Close and restart.
Hope that ll work for you.Thanks

---

