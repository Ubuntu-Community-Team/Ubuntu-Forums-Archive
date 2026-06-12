---
title: "Firefox Spell Check...No suggestions?"
date: 2008-09-13
forum: General Help
---

### Post by The Pinny Parlour on 2008-09-13
Hello

I have Spell Check setup but when I right click the red underlined word, the menu give no spelling suggestions.

Any ideas how to correct this?

---

### Post by Pro-reason on 2008-09-13
> **The Pinny Parlour said:**
> Hello

I have Spell Check setup but when I right click the red underlined word, the menu give no spelling suggestions.

Any ideas how to correct this?

Is this definitely happening with all words?  Try “*computar*”.

It works for me.

What is the output of the following if you type it into a terminal?
```

dpkg -p firefox-3.0 | grep Version

```

---

### Post by The Pinny Parlour on 2008-09-13
I'm not sure what has happened.  What I did do to solve it was backup my bookmarks, and totally nuke my profile folder and started from scratch.
all works now after a little housekeeping and fine tuning to get FF how I like it.

Thank you for your help BTW   :)

---

### Post by DGambrinus on 2008-09-28
Nuking the ~/.mozilla folder worked for me too. Thanks!

---

### Post by SerafeimG on 2009-05-03
> **DGambrinus said:**
> Nuking the ~/.mozilla folder worked for me too. Thanks!

By saying nuking you mean delete??

---

