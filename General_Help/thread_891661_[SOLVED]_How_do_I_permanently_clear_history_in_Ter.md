---
title: "[SOLVED] How do I permanently clear history in Terminal?"
date: 2008-08-16
forum: General Help
---

### Post by 3pinner on 2008-08-16
I would like to clear my terminal history.
I have tried using: clear history, which it will do, but as soon as I retype history, its still there.

Any suggestions?

Thanks

---

### Post by dje on 2008-08-16
does [this]("http://gentoo-wiki.com/SECURITY_Adjusting_The_Way_Bash_History_Funtions") help?

dje

---

### Post by Dougie187 on 2008-08-16
Well, I dont know if theres a way to make sure that your history is never saved, but you can delete your .bash_history file. that should clear out your history.

---

### Post by GreenN00b on 2008-08-16
Open a terminal and execute the following command
```
rm ~/.bash_history
```

---

### Post by drs305 on 2008-08-16
The commands I use to clear terminal history are:
```
history -c && source ~/.bashrc
```

The first clears the history and the second refreshes things if you are keeping the same terminal open.

---

### Post by jakob.g on 2008-08-16
# export HISTSIZE=0
# history
# [Note that history did not display anything]

shamelessly ripped from from [http://www.thegeekstuff.com/2008/08/15-examples-to-master-linux-command-line-history/](http://www.thegeekstuff.com/2008/08/15-examples-to-master-linux-command-line-history/) 
great article by the way :)

---

