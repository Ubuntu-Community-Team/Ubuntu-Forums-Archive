---
title: "Using Compiz or Beryl makes window borders disappear"
date: 2008-08-06
forum: General Help
---

### Post by Ederico on 2008-08-06
Dear all,

When I try and use Compiz or Beryl on my Ubuntu the window borders (those with the minimise, restore, close buttons in the upper right corners) do not appear. Thus I have to revert to Metacity.

I don't know what setting I have to tweak or what is wrong. Hope someone can help!

Ederico.

P.S. I run Hardy Heron.

---

### Post by DJ_Peng on 2008-08-06
It sounds like the Window Borders needs to get turned on. You may need to install CompizConfig Settings Manager (also known as ccsm), then run it and go down to the Effects section and enable Window Decoration. The Command field should read ```
emerald --replace
``` (you may need to also install Emerald) This is kind of a long standing issue that I'm surprised hasn't been resolved better yet, but that should fix things for you.

---

### Post by Ederico on 2008-08-06
Ok I fixed it, thanks a lot.

I went to System and Appearance (hey, mine is in Italian, I'm translating so the terms might be different), went to effects and selected Windows Decoration. Then through Emerald I chose Compiz as window manager.

Thanks again.

---

### Post by DJ_Peng on 2008-08-06
Glad we could help. :)

---

