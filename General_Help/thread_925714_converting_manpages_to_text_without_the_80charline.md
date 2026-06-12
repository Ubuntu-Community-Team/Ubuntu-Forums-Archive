---
title: "converting manpages to text without the 80char/line limit"
date: 2008-09-20
forum: General Help
---

### Post by yacwroy on 2008-09-20
Unfortunately, many programs still use man pages instead of text or html files, meaning you have to convert them or you're forced to view them with man.

Using "man g++ | cat -b > g++.man.txt" creates a text copy of the g++ manpage, but unfortunately man somehow figures it's in an 80col/line terminal or something, so the resulting text file is awfully squished.

Is there any way I can tell man that I'm using a 10000000000000000000000000000000000000000000000000000 character terminal so that it doesn't add unspecified line breaks? That way my app can use word wrap.

Thanks.

---

### Post by Pro-reason on 2008-09-21
```

export MANWIDTH=1000

man g++ | cat -b | gzip > g++.man.gz

zless g++.man.gz

```

---

### Post by ghostdog74 on 2008-09-21
i see no use case for converting to text as man pages are all text. Instead i would think its worthwhile for you to convert to html instead. Unless you want try writing yourself, otherwise, people have already done it. See [here](http://www.squarebox.co.uk/users/rolf/download/manServer.shtml)  aand [here](http://www.math.utah.edu/~beebe/support/myman2html/man2html.awk) for example

---

