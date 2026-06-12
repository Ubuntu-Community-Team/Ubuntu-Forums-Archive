---
title: "PHP compiler for Ubuntu?"
date: 2008-08-30
forum: General Help
---

### Post by CastilleV on 2008-08-30
Just wondering, but is there a PHP compiler for Ubuntu?

---

### Post by mb_webguy on 2008-08-30
Absolutely.   Check these links:
[http://www.linuxdocs.org/HOWTOs/PHP-HOWTO-9.html]("http://www.linuxdocs.org/HOWTOs/PHP-HOWTO-9.html")
[http://www.ibm.com/developerworks/opensource/library/os-php-ide/index.html]("http://www.ibm.com/developerworks/opensource/library/os-php-ide/index.html")
[http://linuxmafia.com/faq/Devtools/ides.html]("http://linuxmafia.com/faq/Devtools/ides.html")
[http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html")

---

### Post by pythonscript on 2009-07-02
For this basic php script:

```

<?
print "Hello World!\n";
?>
```the command 
```

chmod +x hello.php

```followed by:
```
php hello.php
```generated the proper output.

---

### Post by new2ubuntu on 2009-12-28
ummm... no. Non of those links are compilers... they are IDE's. And changmoding it and running it through the PHP interface is still using the php interpreter... a LOT slower then a compiled program (especially on larger scripts or scripts that manipulate a lot of data)

Google reveals this: (I did not check into it)
[http://www.phpcompiler.org/](http://www.phpcompiler.org/)

from my glance it is experimental, Linux only, and creates C code, 2. :D

for windoze here is another one:
[http://www.bambalam.se/bamcompile/](http://www.bambalam.se/bamcompile/)

I have heard these only work for the most basic of things and have not tried them... but the Linux one at least I know is a real compiler.
:guitar:

---

