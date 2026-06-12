---
title: "Keep a custom command from starting when a terminal profile is opened"
date: 2008-07-15
forum: General Help
---

### Post by S3loth on 2008-07-15
How would I do this. I have it set up so I can text people with a terminal with "./txt.sh # "M" 1" I just need to replace the # and M but when I start terminal it tries to send it right away (then fails, then loops into trying and failing). Is there something I can put in there to stop it from starting right away?

---

### Post by fyo on 2008-07-16
I'm not sure I follow... It sounds like you've made a "shortcut" of some kind to your script... Is that the case?

What I would do is just have the script saved in path and then open a terminal (from the menu, but you will probably want to copy one to the quick launch) and type:

```
$ ./txt.sh 5551234 "Hello there" 1
```

The script should of course be set up to handle the args appropriately.

Anyway, nothing should "run" just by starting your terminal session.

---

