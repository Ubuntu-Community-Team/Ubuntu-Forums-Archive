---
title: "[SOLVED] mpg123 help (very basic)"
date: 2008-11-15
forum: General Help
---

### Post by transmition on 2008-11-15
This should seem like such a simple problem, but alas, my google skills have failed me. With the program mpg123, how do I pause a song while it is playing?

---

### Post by sdennie on 2008-11-15
You could just send it the STOP and CONT signals:

```

pkill -STOP mpg123

```

Then

```

pkill -CONT mpg123

```

I once wrote an mp3 player in vim using mpg123 and this is what I used.

---

### Post by iAlta on 2008-11-15
I'm not sure you can... I looked into the manpage ('$ man mpg123') but there is no mention of any pausing capability, strange...

Try using mplayer, there you use the space-bar.

---

