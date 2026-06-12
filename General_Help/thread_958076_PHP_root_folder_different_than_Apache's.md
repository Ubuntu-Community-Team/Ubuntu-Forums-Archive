---
title: "PHP root folder different than Apache's ?"
date: 2008-10-25
forum: General Help
---

### Post by Cha0tik on 2008-10-25
I am building a Ubuntu machine from the command line only.
I installed Apache2 and PHP5 and all appropriate modules.

I put my PHP app directly in the Apache root folder (/var/www) so I have a bunch of PHP files in that folder. When calling them with firefox, it keeps prompting me to open or save the files. I though I had an issue with the modules or something and I wasted a bunch of time trying to figure that out until I tried to create a new folder within the root (/var/www/app) and moved everything in there and guess what... it works ?!?! Obviously PHP is interacting well with Apache

Problem is, I want my files in the root... any idea why it isn't working in the root folder ?

Thanks !

Chaotik

---

### Post by scragar on 2008-10-25
It could be your cache thinking you want to download the files again, although I doubt it, try adding a query string to the file name, or use shift+click reload to clear the cache for that page, see if it works then.

---

### Post by Cha0tik on 2008-10-25
no luck there either..

---

