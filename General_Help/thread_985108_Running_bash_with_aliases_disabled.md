---
title: "Running bash with aliases disabled"
date: 2008-11-17
forum: General Help
---

### Post by filburt1 on 2008-11-17
I use Bash as my shell. Is it possible to disable aliases completely, or otherwise configure bash such that the "alias" command has no effect?

I don't mean just remove existing aliases, but actually disable the functionality to define aliases in the first place.

Thanks.

---

### Post by geirha on 2008-11-17
```
shopt -u expand_aliases
```

It will still allow you to define aliases, but the aliases will no longer be used.

---

