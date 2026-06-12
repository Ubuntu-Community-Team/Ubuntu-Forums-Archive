---
title: "One solution for &quot;Desktop effects could not be enabled&quot;"
date: 2008-10-26
forum: General Help
---

### Post by Toci on 2008-10-26
Days ago I found some command that promised to enable "real transparencies" (gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true), I applied it and a while later when I tried to switch Visual Effects from none to normal I got an error saying  "Desktop effects could not be enabled".

 So I opened a Terminal and typed the same command again except this time with "false" instead of "true"


gconftool-2 -s --type bool /apps/metacity/general/compositing_manager false


 Everything works again. Perhaps it can also work for others.

---

### Post by hictio on 2008-10-26
Thanks, I'll keep it around, last week I have a similar problem... turned off the Desktop Effects and afterwards [the refused to start](http://oesediez.blogspot.com/2008/10/vanishing-plugin.html).

---

