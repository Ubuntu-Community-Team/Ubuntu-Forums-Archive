---
title: "Support for Unicode (utf8/utf32) in Ubuntu"
date: 2008-08-15
forum: General Help
---

### Post by LinuxRocks713 on 2008-08-15
Hi:

Does anyone know how to display unicode in the shell (Bash)? Every time I 'cat' something with accents the following appears:
[quote=Bash]
&#65533;&#65533;
[/quote]

Does anyone know a fix/workaround/solution for this?

---

### Post by LinuxRocks713 on 2008-08-18
Bump

---

### Post by LinuxRocks713 on 2008-08-20
bump

---

### Post by simosx on 2008-08-30
The default encoding in Ubuntu is UTF-8. Type "locale" at the terminal to verify.

Unless you made invasive configuration changes, you can can Unicode text and it should work out of the box.

If you have text files with encoding other than UTF-8, you would need to convert. The gedit text editor can do this for you, as well as the iconv command line program. For example,

iconv -f iso-8859-1 -t utf-8 < inputfile.txt > outputfile.utf8.txt

---

### Post by ModelM on 2008-08-30
It might be a terminal problem. The package rxvt-unicode is a terminal designed for display of these characters, you might want to give it a try.

---

