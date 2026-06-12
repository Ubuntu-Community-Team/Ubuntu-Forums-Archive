---
title: "[SOLVED] Help! Brother HL-1030 refuse to print"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by Toshick on 2007-11-04
Hello All! I'm using Gutsy amd64 version. I've tried already all ways, found on this forum, but all that i can get - when i send something to print, my data led blink one time and thats all. Nothing prints. I've tried reinstall cups from Brother website, with --force-all options... lpr... everytime the same. Under Windows priter prints as it should. Maybe somebody has same problem? Or May somebody share with experience installing HL1030 on amd64 ubuntu?

Thank you.

---

### Post by scachi on 2007-11-04
I have the same problem with a Brother HL-1430.
I can't find any problems in my logs, so I don't know what can be wrong.
From windows and from mac osx everythign works fine, so it isn't the rpinter itself.

Kind regards.

Ingo

//edit

I have solved my problem.

Cups with gutenprint itself wasn't working for me.
I just downloaded the ppd file for my printer from cups and installed the printer using this file.
Then it complained about missing foomatic-rip.
After installing the foomatic package everything is working fine now.

---

### Post by Toshick on 2007-11-04
Thanks! I've did almost the same. But I've used ppd file from Brother website.

---

