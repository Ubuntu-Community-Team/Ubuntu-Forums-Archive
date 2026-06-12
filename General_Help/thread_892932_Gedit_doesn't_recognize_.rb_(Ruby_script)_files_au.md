---
title: "Gedit doesn't recognize .rb (Ruby script) files automatically"
date: 2008-08-17
forum: General Help
---

### Post by Battle O'Endor on 2008-08-17
I create new or open existing *.rb file (Ruby script).

I see (in file manager) that it has application/x-ruby MIME type.

ruby.lang is defined:

user@host:/usr/share/gtksourceview-2.0/language-specs$ cat ruby.lang | grep mime
    <property name="mimetypes">application/x-ruby;text/x-ruby</property>

But Gedit sets file language to 'None' and I need to change it manually to Scripts -> Ruby to get syntax highlighting.

With all of the others file types language is set automatically.

How to make this happen with .rb?

---

