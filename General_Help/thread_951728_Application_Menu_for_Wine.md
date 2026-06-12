---
title: "Application Menu for Wine"
date: 2008-10-18
forum: General Help
---

### Post by dstein on 2008-10-18
When I install new windows software using Wine, a corresponding launcher is usually created in ~/.local/share/applications/wine/Programs. However, this launcher is missing the *Categories* attribute and does not appear on my Application menu. Therefore I open up the launcher in a text editor and append: ```
Categories=Wine-Programs;
```
or something similar to the programs that I want to show up in my Applications menu.

Does anyone know why this is happening? Why is the *Categories* attribute not being created automatically in the launchers that are created by wine? How can I fix this?

If I remember correctly, I believe I used to have a similar problem when using Crossover.

Thanks.

---

