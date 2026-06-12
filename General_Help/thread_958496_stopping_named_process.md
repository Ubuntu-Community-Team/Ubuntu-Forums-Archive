---
title: "stopping named process"
date: 2008-10-25
forum: General Help
---

### Post by marli2 on 2008-10-25
this is probly a really simple answer.
how do i stop a named process
>kill compiz
fails to work.
i want to add it to a game script as compiz conflicts
i can kill it through the session window but that seems long winded.

---

### Post by sdennie on 2008-10-25
You can use pkill:

```

pkill compiz

```

There is also pgrep which returns a pid:

```

kill `pgrep compiz`

```

---

