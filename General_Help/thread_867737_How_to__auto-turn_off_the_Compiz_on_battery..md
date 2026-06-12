---
title: "How to  auto-turn off the Compiz on battery."
date: 2008-07-23
forum: General Help
---

### Post by piter_aspire5920g on 2008-07-23
Hello!

Laptop-mode.conf has a smart option that gives us a chance to choose a different programs to turn on/off when changing power source.

For example we can make a script which will autmatically turn off Compiz and other "heavy" modules when using battery. And automatically turn it on, if we come back to AC.

But I am not fluent in scripts. Can somebody help with it?

This would be VERY useful!

---

### Post by anotherdisciple on 2008-07-23
Assuming you are using Ubuntu... it uses metacity as default window manager. The script could be as simple as...
```
#!/bin/bash
metacity --replace
```

and the script that restarts compiz...

```
#!/bin/bash
compiz --replace
```


I have never tried to make a script that does this.. however I remember that some scripts are automatically run when you go into battery mode.... perhaps you can add "metacity --replace" to that script and "compiz --replace" in the AC script.

---

### Post by piter_aspire5920g on 2008-07-23
What name should I give to those files?

---

