---
title: "[SOLVED] using sed to add to end of line"
date: 2008-11-20
forum: General Help
---

### Post by porchrat on 2008-11-20
Is it possible to add a character to the end of a line containing a certain string?

If so how can I do it?

basically the line contains "foo" somewhere in the middle and I need to add a '"' to the end of that line.

I doubt sed on its own can do this, but I'm fairly certain bash can do it.

---

### Post by porchrat on 2008-11-20
Nevermind I solved it using the squishy thing between my ears (no not my nose)!

Turns out the sed command readily provides this neat little feature so that you don't even need to invoke other bash commands.  Check it out:

```
sed -i '/string_you're_interested_in/s|$|"|g' filename
```

Amazing.  sed is so versatile.  For those that are a little confused I used the pipes because I had other things this script needed to do that involved slashes, and having all those slashes around was starting to look a little crazy.

---

