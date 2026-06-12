---
title: "Sqldeveloper only runs from terminal"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by donkeyX on 2009-01-05
Hey Guys,

I am having a little trouble with sqldeveloper when using it. Basically, i have used the script to install and all seems to go well and it works ok. So for example when i run it from the terminal eg: ```
sqldeveloper &
``` it all starts up ok and i can create and use connections fine. The problem comes when i went to add the shortcut to the menu for running it. What happens then is when it opens it will not show the connection information that has been previously created, i am guessing because it is not searching for the config information in ~/.sqldeveloper which is where it gets placed??? Anyway, after having a look I am guessing that it has something to do with the script that runs sqldeveloper failing when not run from the terminal and was wondering if you guys had any suggestion for fixing this script or adding params to make it pass the correct info to the script: 
```
#!/bin/bash
cd "`dirname $0`"/sqldeveloper/bin && bash sqldeveloper $*

```

this is the script that gets run when you type in sqldeveloper from the terminal and i have no idea what it does?

thanks in advance

---

### Post by donkeyX on 2009-01-09
Well it looks like this was more of a env var issue rather than a strange script problem. What i ended up doing was creating a file called ~/.bash_vars and then sourced that in the /etc/profile script so it is run for all users. After a few restarts this seems to have fixed it up fine.

Examples of my two files are here : 

[/etc/profile]("http://www.edens-gate.com/temp/profile")
[~/.bash_vars]("http://www.edens-gate.com/temp/.bash_vars")


Cheers ME :P

---

### Post by unutbu on 2009-01-09
Thanks for sharing your solution.

---

