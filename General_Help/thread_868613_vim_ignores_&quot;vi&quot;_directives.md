---
title: "vim ignores &quot;vi:&quot; directives"
date: 2008-07-24
forum: General Help
---

### Post by Stilor on 2008-07-24
I must be missing something obvious here. Just migrated from Fedora to Kubuntu 8.04.1, almost everything is up an running. One question I can't find an answer to:

How do I make vim honor the vi: directives in the edited files? In Fedora, it worked out-of-the-box; I can't find any commented-out option for this in /etc/vim/vimrc. Example of such directive:

<<< start a.c >>>
/* vi: set sw=4 : */
....
<<< end a.c >>>

When this file is opened, it sets the syntax width to 4 in Fedora, but doesn't work in Ubuntu...

---

### Post by sdennie on 2008-07-24
The option is "set modeline" so:

```

echo "set modeline" >> ~/.vimrc

```

---

### Post by Stilor on 2008-07-24
Thanks a lot! Indeed, something obvious, shame on me... :)

---

### Post by sdennie on 2008-07-24
> **Stilor said:**
> Thanks a lot! Indeed, something obvious, shame on me... :)

Not *that* obvious.  It took me 10 minutes to remember they are called modelines.  ;)

---

