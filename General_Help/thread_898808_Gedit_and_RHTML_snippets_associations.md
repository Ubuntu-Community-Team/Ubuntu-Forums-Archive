---
title: "Gedit and RHTML snippets associations"
date: 2008-08-23
forum: General Help
---

### Post by matias.quaglia on 2008-08-23
Hi,

I'm kinda newbie on Ubuntu.

I am using Hardy, and so far so good.

I followed [this tutorial]("http://blog.nationcode.com/articles/2007/05/30/emular-textmate-en-gnu-linux") in order to work with Rails using Gedit 2 as editor.

Everything worked perfectly but when I open an embedded ruby file (rhtml, html.erb) the associated snippets to that files are the HTML one. :(

I have on my snippets list the RHTML ones, but they don't work at all.

I suspect that it's a mime type problem, and i tried updating the mime database after adding the html.erb rhtml rjs extensions as the tutorial points, but still isn't working.

Could anyone give me a tip, please?

Thanks in advance!

MQ

---

### Post by Rich78 on 2008-08-23
Sorry I'm not sure what the issue is?

Can you not just open terminal and type: sudo gedit myrubyfile.rhtml

Edit and then save?

---

### Post by matias.quaglia on 2008-08-23
Oh, my fault!

To clarify:

Of course I can edit using Gedit, it works perfect.

Te issue is that when I open an embedded ruby file, the snippets plugin associates the HTML snippets to that file, instead of the RHTML ones. :(

I can figure out how to make the RHTML snippets be active when editing the html.erb type of files.

It works perfect when I edit .rjs, but not with .rhtml

Do you have any idea?

Thanks!

---

