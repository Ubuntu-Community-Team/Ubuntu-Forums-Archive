---
title: "[SOLVED] Restore Compiz settings after disabling it"
date: 2008-07-13
forum: General Help
---

### Post by jonlemur on 2008-07-13
I have Compiz working beautifully on my computer, with a lot of settings set to the way I like them.  But sometimes I have turn off Compiz to get other things to work properly.  I can turn it off by going to System->Preferences->Appearance and turn off the Visual Effects.  But if I do that, when I want to turn the effects back on, I lose all of my settings.  I think Gutsy had a Custom option in the Visual Effects dialog, which would allow you to turn off Compiz, and turn it back on with the same settings as you had previously.  What's the best way to do something like that now in Hardy?

---

### Post by damis648 on 2008-07-13
Turning it off:

Press Alt+F2. In the dialog box type:
```
metacity --replace
```

Turning it on:

Press Alt+F2. In the dialog box type:
```
compiz --replace
```

Good luck!

---

### Post by jonlemur on 2008-07-13
That does it, thanks.

---

### Post by damis648 on 2008-07-13
> **jonlemur said:**
> That does it, thanks.

Welcome. :popcorn:

---

