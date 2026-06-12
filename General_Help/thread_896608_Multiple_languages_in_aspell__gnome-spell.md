---
title: "Multiple languages in aspell / gnome-spell"
date: 2008-08-21
forum: General Help
---

### Post by g474h4d on 2008-08-21
**Problem:**
Gnome applications with spell-checking capability (like Pidgin or Tomboy) check with the language of your session. Unfortunately it is quite common for me to have "mixed" text which contains both English and German simultaneously. That's why I want aspell to allow both languages. This has to be possible somehow because Evolution can do just that and Evolution uses aspell underneath.

**Unsuccessful attempts:**
My attempts do configure aspell to do it outside of Evolution have failed. I tried it with a config file (~/.aspell.conf) which was interpreted (I could switch from English to German and vice versa) but specifying more langs failed. Using the extra-dicts option fails with an error when the extra dictionary is of another language than the "master" dictionary. Creating a custom multi file doesn't work either - I suppose it is the same reason (it seems all added dictionaries must be of the same language).

---

