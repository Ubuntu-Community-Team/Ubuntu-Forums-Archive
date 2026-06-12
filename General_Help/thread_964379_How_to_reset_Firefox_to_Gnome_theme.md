---
title: "How to reset Firefox to Gnome theme?"
date: 2008-10-30
forum: General Help
---

### Post by Murrquan on 2008-10-30
I just installed and the un-installed a theme in Firefox, and now instead of the Gnome integration theme it's got these ugly silver buttons. How do I set it back to normal?

I did change the default icon theme to Bluecurve, but that was working perfectly in Firefox until I changed *its* theme.

---

### Post by jesuspresley on 2009-04-26
To reset all firefox preferences, try to choose another theme, and then delete the .firefox folder in your user's home folder.[I]
But beware! This also deletes your user profile in Firefox: Bookmarks, history, saved passwords etc.[/I]

I think it's here:
```
rm -rf ~/.mozilla/firefox
```
or```
rm -rf /home/<myUserName>/.mozilla/firefox
```

---

