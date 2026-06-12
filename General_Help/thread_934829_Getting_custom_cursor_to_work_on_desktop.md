---
title: "Getting custom cursor to work on desktop"
date: 2008-10-01
forum: General Help
---

### Post by JustAnotherVagueAnon on 2008-10-01
I have installed some custom cursor themes which work, but when I am at the desktop it just shows the same white cursor I had previously. Inside of applications it shows the new cursor, but how can I make it apply to everything?

---

### Post by kestal on 2008-10-01
are you using Emerald?

If this is not the case, can you provide a bit more info? What did you do last? has it always been like this? Did you change the option in Compiz general settings to your current mouse theme?

If thats the case, I had this problem once. You have to uninstall emerald, apply your cursor, then install it again. (Thats what I ended up doing). What you can try first is to switch to compiz --replace in the terminal, switch cursor, then close up your terminal.

---

### Post by JustAnotherVagueAnon on 2008-10-01
Ah, ok thanks. You gave me an idea. I modified my emerald startup script to sleep for 5 first and now my cursors will stick. Thanks!

---

