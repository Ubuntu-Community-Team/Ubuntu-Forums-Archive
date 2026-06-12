---
title: "Suhosin and DragonFly CMS 9.2"
date: 2008-11-07
forum: General Help
---

### Post by DaleHUtch on 2008-11-07
Greetings,

Since I upgraded to Ubuntu 8.10 and recently installed the DragonFly CMS 9.2 I have had a problem. The guys over at the DragonFly site say it is a problem with Suhosin. This is what they say...

One such conflict is the default setting for the maximum number of variables that may be registered. The indicative symptom is the block manager not saving any changes made in the JavaScript area (add, delete, order changes).

Two settings have to be changed in php.ini from their default size of 200 (example values used here):

Code::

suhosin.post.max_vars = "4096"
suhosin.request.max_vars = "4096"

Well I placed the above code in my PHP.INI and restarted the server. The problem still exists and I can not confirm if the new code is working or not. There is no indication in my phpinfo.php response.

Any suggestions???

Thanks!

---

### Post by DaleHUtch on 2008-11-08
Anyone????

---

