---
title: "Can I turn off Compiz over the commando line?"
date: 2008-09-05
forum: General Help
---

### Post by Archmage on 2008-09-05
Is it possible to turn of the desktop-effects via the commando line? Since when they turned on, I can't reach my menu anymore nor does the terminal window work.

---

### Post by overdrank on 2008-09-05
> **Archmage said:**
> Is it possible to turn of the desktop-effects via the commando line? Since when they turned on, I can't reach my menu anymore nor does the terminal window work.

Hi and have you tried ctrl, alt, F1 then the command ```
metacity --replace
```

---

### Post by sayakb on 2008-09-05
Just a little modification (since tty1 doesn't have X running). Either press Alt+f2 or goto Applications->Accessories->Terminal, and type in 
```
metacity --replace &
```

---

