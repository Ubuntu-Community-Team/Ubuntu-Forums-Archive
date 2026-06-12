---
title: "Firefox is not rendering Tahoma font."
date: 2008-09-28
forum: General Help
---

### Post by AN@S on 2008-09-28
Hi all, 

I have a problem viewing Tahoma font in Firefox, Tahoma is heavily used in Arabic-language websites so the ugly font I get instead of tahoma does hurt my eyes :(

I have Microsoft fonts installed, is this the cause of the problem?

Regards

---

### Post by jualin on 2008-09-28
Just copy the font files from Windows to Ubuntu. In Ubuntu the files need to be copied to your .fonts directory located on your root folder (must press CTRL+H to see the .fonts folder since it's hidden).

---

### Post by fragos on 2008-09-28
The Tahoma font isn't part of the msttcorefonts package. You'll need to copy tahoma.ttf from windows to ~/.fonts in the Ubuntu partition. Then reboot or run "sudo fc-cache -fv". Which fonts are used to render a web page is normaly specified in the sites CSS as something like "font-family: "DejaVuSansCondensed", "Arial", sans-serif;". The browser starts at the beginning of the list and goes left to right until it finds that font on the browsers machine. Your only option is to have a specified font installed.

---

