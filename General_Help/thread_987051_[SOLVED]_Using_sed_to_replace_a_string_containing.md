---
title: "[SOLVED] Using sed to replace a string containing \"
date: 2008-11-19
forum: General Help
---

### Post by porchrat on 2008-11-19
Is it possible to replace a string using sed if that string conatins the character \ ?

I mean the \ character has meaning for sed but is there a way for it to pass that as part of the string and not a special character?

To further clarify:

```
sed 's/\,/\/g'
```


Is basically what I want to do, but it throws this:

```
sed: -e expression #1, char 8: unterminated `s' command

```

I mean OK fair enough I knew that the above command wasn't going to work, but how do I get something like that to work?

---

### Post by porchrat on 2008-11-19
It seems like their should be a simple solution, but I don't know what it is and can't find it online.

---

### Post by ilrudie on 2008-11-19
Have you tried:
sed 's/\\,/\\/g'

I'm not exactly sure what you are trying to do but this replaces all \, with \

---

### Post by rampageoberon on 2008-11-19
> **porchrat said:**
> sed 's/\,/\/g'

For future use, some characters need escaping which is what ilrudie has done in his reply.

Check out [http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm) and the Perl Regular expressions page - [http://www.perl.com/doc/manual/html/pod/perlre.html](http://www.perl.com/doc/manual/html/pod/perlre.html) is quite useful for this.

Hope that helps

---

### Post by porchrat on 2008-11-19
Big thanks to both of you.  That sorted it out and those links are helpful, I'm always willing to learn :)

---

