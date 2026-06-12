---
title: "how to perform a hexdump using dd from start point to end point"
date: 2012-04-07
forum: Hardware
---

### Post by jao_madn on 2012-04-07
hi, 

I would like to ask or is it possible to dump a hex using dd from starting point to end point just like the "xxd -s 512 -l 512 <bin file>"

I know the redirect hexdump -C but i can't figure it out the combination options of dd.

Hope someone can share their knowledge..

Thanks in advance

---

### Post by oldfred on 2012-04-07
Be very careful:

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

---

