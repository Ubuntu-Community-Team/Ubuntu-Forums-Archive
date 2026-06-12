---
title: "Ubuntu 13.10 on Dell Inspiron 1300 Dark Screen hard to read"
date: 2014-02-10
forum: Hardware
---

### Post by Cohaniuc_Boris on 2014-02-10
[COLOR=#000000]Hi[/COLOR]

[COLOR=#000000]I'm using a Dell Inspiron 1300 laptop . I've installed Ubuntu 13.10 on it and it works good. [/COLOR]

[COLOR=#000000]The problem I'm having is that the screen is dark and really hard to read .....
[/COLOR]i have tried [COLOR=#000000]system settings -- brightness and lock, and nothing...
[/COLOR]Could anybody tell me what to do thanks a lot
Regards
[COLOR=#000000]Boris[/COLOR]

---

### Post by ajgreeny on 2014-02-10
If there is no way to change backlighting on the screen you could try changing the overall gamma with the use of command ```
xgamma -gamma 1.5
```The figure shown of 1.5 can be set between 0 and 2, with 1 being the default you have at the current time.  Try different figures to see if you get something appropriate for your screen, then you can write a script to do this each session start.

---

### Post by Cohaniuc_Boris on 2014-02-11
thank u very much

---

