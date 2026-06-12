---
title: "unsure how to FIX OPENOFFICE COLOR"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by shadowlands on 2009-11-02
I am not sure how to read the following so that I can enter it in to the terminal correctly.  Can someone assist me or give me a link to better directions.  

OPENOFFICE COLOR FIX
Karmic sets the OpenOffice colors to KDE or Gnome colors. This is especially a problem will color-coded spreadsheets, because the background colors set in the spreadsheet no longer show. If you DON'T want OpenOffice to use your desktop colors, this script will make that change. You may need to run this script again if OO or your desktop is updated.

Code:

#!/bin/bash
# openoffice color fix
# [http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8](http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8)
test=`grep "export OOO_FORCE_DESKTOP=none" /usr/lib/openoffice/program/soffice`
if [ "$test" = "" ]; then
	sudo sed -i -n '1h;1!H;${;g;s/#!\/bin\/sh\x0A/#!\/bin\/sh\x0Aexport OOO_FORCE_DESKTOP=none\x0A/;p;}' /usr/lib/openoffice/program/soffice;
fi

---

### Post by x22 on 2009-11-23
that's a bash script...

if you highlight the code with the left mouse
button, and then paste it into an editor such
as vi or emacs, with the middle button, and then
save it as an executable "name" you should be able
to run it from any terminal

---

### Post by Hagar Delest on 2010-02-06
See that one (especially the end), it even brings back the default gray shading: [[Solved] OOO_FORCE_DESKTOP for dark themes]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=27216").

---

