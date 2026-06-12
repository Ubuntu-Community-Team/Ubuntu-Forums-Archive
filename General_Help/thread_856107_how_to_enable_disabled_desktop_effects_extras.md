---
title: "how to enable disabled desktop effects extras?"
date: 2008-07-11
forum: General Help
---

### Post by ravindukelum on 2008-07-11
:guitar:I used extra effects on my ubuntu then I changed it "none" means no effects but now i can't enable it to "extra" effects when i'm going to enable it gives a message "desktop effects couldn't enaled" please help me to get my desktop effects back.

---

### Post by sayakb on 2008-07-11
At a terminal, do:
```
killall metacity
compiz --replace &
```

---

### Post by ravindukelum on 2008-07-11
i tried that method but it does not work

---

### Post by sayakb on 2008-07-11
Can you post the output of compiz --replace ?
Also, have you tried compiz-check? [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

---

