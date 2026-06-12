---
title: "Apache &quot;falls asleep&quot;??"
date: 2005-11-13
forum: General Help
---

### Post by Zerlinna on 2005-11-13
Hey there,

I've just installed  apache2, php5 and mysql4 and it generally works fine - except that apache2 seems to "fall asleep" after some minutes. This is only the case if I'm doing nothing on my server and I can easily fix it with
> sudo apache2 -k stop
sudo apache2 -k start
Just that two minutes later I have to do the same again!
 Is there any time-out function or something like that? How can I keep it from "falling asleep"?

Thx, Zerlinna

---

### Post by Corvillus on 2005-11-13
If you're just referring to apache2 having sleep status in a process listing, it, as well as any applications that aren't immediately doing something, are supposed to do that. As long as it's still serving up pages, it's working fine. Try going to [http://localhost/](http://localhost/) to make sure it's working though.

---

