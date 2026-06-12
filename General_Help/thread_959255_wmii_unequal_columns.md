---
title: "wmii unequal columns"
date: 2008-10-26
forum: General Help
---

### Post by kcode on 2008-10-26
im using wmii. as soon as it starts, i press mod+return to get the terminal, again to get second, and then mod+shift+l to create 2 columns. But they are unequal.What can be done to get equal columns.

thanks

---

### Post by chengt on 2008-10-31
In your ~/.wmii-3.5/wmiirc
locate the lines that say

```

# Column Rules
wmiir write /colrules <<!
/.*/ -> 58+42
!

```

Change it to

```

# Column Rules
wmiir write /colrules <<!
/.*/ -> 50+50
!

```

---

### Post by kcode on 2008-11-01
> **chengt said:**
> In your ~/.wmii-3.5/wmiirc
locate the lines that say

```

# Column Rules
wmiir write /colrules <<!
/.*/ -> 58+42
!

```

Change it to

```

# Column Rules
wmiir write /colrules <<!
/.*/ -> 50+50
!

```

thanks it worked!

PS: what language is this ?

---

### Post by chengt on 2008-11-28
Actually I have no idea. wmiir is a wrapper to ixpc which just writes to a file system.
what it writes is then interpreted by wmiiwm which is written in c.
So I guess in a round about way it's c

:KS

[crap that was unnecessary but I wanted to play with the smilies]

---

