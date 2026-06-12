---
title: "sh command"
date: 2008-11-14
forum: General Help
---

### Post by wildrussian on 2008-11-14
Hey everybody! I have been reading this forum for a little while but this is my first post. I did a search on my question but it didn't seem to find anything so I decided to post it. Can anybody please tell me what does sh command mean and when and why to use it? Thanks so much.

---

### Post by tvtech on 2008-11-14
sh is the BSD General command interepreter shell

if you really want to learn more about it check out 

```
username@localhost:~$man sh
username@localhost:~$info sh
```

once you enter the info/ man pages you can scroll with your arrow keys, and just hit q to quit. 

this will give you a full description of the available uses and switches for the sh commond interpreter.  it's just a different type of shell like bash.

---

### Post by lswb on 2008-11-14
sh is another "shell" or command interpreter similar to bash, csh, etc. It has somewhat fewer features and options than bash, but is smaller and faster. Most linux distros use bash for the default shell, however ubuntu uses sh for non-interactive scripts in an attempt to lower execution time. bash is still the default for login and interactive shells. 

There is litte reason to run sh by itself as an interactive shell. You might use it to run a script that does not have executable permissions set or "#!/bin/sh" as its first line.

---

