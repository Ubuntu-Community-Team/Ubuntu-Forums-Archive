---
title: "[SOLVED] Saving Terminal Commands"
date: 2008-11-15
forum: General Help
---

### Post by jakenbake42 on 2008-11-15
So I know this is common knowledge, but I've googled all  over and failed
What I want to do is I have a text file containing a command that I want to run. I want to be able to have a file of somesort that I can just double click to run that command
and if possible, for the terminal to not appear when it is ran
is this possible?
thanks in advance

---

### Post by rampageoberon on 2008-11-15
Sounds like what you want is to create shell scripts. Have a look at [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) and [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial) for more info.

In short a bash script would look like this

```
#!/bin/bash

your command 1 here
your command 2 here
```

Now you have to give execute permissions to the file and then run it.

---

### Post by jakenbake42 on 2008-11-17
I appreciate this very much but I'm still having trouble figuring this out [I know it's bad]
So do I just put the command in for commmand 1?
thanks again

---

### Post by jakenbake42 on 2008-11-17
Ah I figured it out using the make a new launcher command
thanks so much for all the help!

---

### Post by thestig_992 on 2008-11-17
shell script is slightly different to a launcher. A shell script uses bash, a programming langauge, and is able to do much more than just a single command like a launcher. An example of some of my scripts are: 
Torrents autoatically download when its between certain times (i have peak and off peak internet)
Wallpaper randomly changes every hour

---

