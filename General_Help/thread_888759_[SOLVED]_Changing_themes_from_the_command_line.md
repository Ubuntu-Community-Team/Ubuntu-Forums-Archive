---
title: "[SOLVED] Changing themes from the command line"
date: 2008-08-13
forum: General Help
---

### Post by Krydahl on 2008-08-13
OK, so I have 2 themes, a light one and a dark one, that I switch between depending on my mood.

To change, I have to open up appearances, select the theme, close appearances, open emerald, pick the theme, close it. It all seems a bit of a palaver. I was thinking of writing a little bash script to change them over. Trouble is, while it's pretty obvious how to do it for the emerald bit (copy files into the right directory, run emerald --replace) I can't see where the main gnome theme picks up the current theme info from.

Anyone any ideas?

---

### Post by Krydahl on 2008-08-14
OK, figured it out now. You have to use gconftool to set up the different theme elements separately if anyone's interested.

---

