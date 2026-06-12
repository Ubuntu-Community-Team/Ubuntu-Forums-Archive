---
title: "[SOLVED] Open Links in New Tabs from Applications"
date: 2008-08-07
forum: General Help
---

### Post by Literati on 2008-08-07
So, I'm trying to get it so when I'm in xchat and I click a link it opens the page in a new tab in my current firefox session. Currently is just starts a new firefox session, without even going to the link in question. In my gconf-editor the url-handler for IRC says just "firefox" how do I fix this?

Thanks! :)

---

### Post by damoxc on 2008-08-07
I think that's in the firefox preferences menu.

Edit > Preferences.

Then in the "Tabs" tab check that "open in a new tab" is selected.

---

### Post by Literati on 2008-08-07
I figured it out. I just needed to change "firefox" to "firefox %s" in gconf-editor

---

