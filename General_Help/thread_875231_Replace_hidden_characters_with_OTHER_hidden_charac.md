---
title: "Replace hidden characters with OTHER hidden characters"
date: 2008-07-30
forum: General Help
---

### Post by JohnnyXmas on 2008-07-30
Hey all,

I have a directory full of PHP files I need to convert to the Drupal standard. Part of this requires me to replace all the TAB indentation with two spaces. How can I go about doing this? A search / replace is easy enough with "visible" characters, you can even do it in gedit, but I can not find a way of doing this with hidden stuff.

Choice of editor is irrelevant, whatever works, that's what I'll use.

---

### Post by Claus7 on 2008-07-30
Hello,

awk will do. Just type :

awk '{gsub("\t","  ");print}' inputfile > outputfile
EDIT: in between "  " leave two spaces

Regards!

---

