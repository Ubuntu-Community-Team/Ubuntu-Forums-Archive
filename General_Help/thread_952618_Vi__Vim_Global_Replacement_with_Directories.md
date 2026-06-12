---
title: "Vi / Vim Global Replacement with Directories"
date: 2008-10-19
forum: General Help
---

### Post by hfranco on 2008-10-19
I have a Vi / Vim question.

I'm trying to replace all occurrences of one string by another with

```
:%s/original/replacement
```

I would like to know how I would be able to do this with directories.

For example, if my original is backups and my replacement is new_stuff/backups

So in theory it should look like this:

```
:%s/backups/new_stuff/backups
```

But that's unsuccessful.

I'm getting a error:
E488: Trailing characters

Thanks.

---

### Post by mike2357 on 2008-10-19
A backslash often signifies in the Linux/Unix world to interpret the next character literally, i.e. without any special meaning.  Backslashes often go before * to mean the actual asterisk character.

In your example, this should work:

%s/backups/new_stuff\/backups

---

