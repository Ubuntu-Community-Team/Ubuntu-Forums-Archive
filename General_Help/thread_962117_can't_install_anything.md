---
title: "can't install anything"
date: 2008-10-28
forum: General Help
---

### Post by oilspot on 2008-10-28
Keep getting this message any time I try to install anything...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 I've tried using alt f2 to open the run menu. I paste the command it says I need to run. Can't tell if it's really doing anything. Guess it's not because I still get the same message again when I try installing anything.

---

### Post by phidia on 2008-10-29
Open a terminal from Applications > Accessories and enter that command with sudo in front of it. That should get you back in business again.

---

### Post by tuxxy on 2008-10-29
Run the following command in terminal

```
sudo dpkg --configure -a
```

---

### Post by aysiu on 2008-10-29
Paste the command ```
sudo dpkg --configure -a
``` into [the terminal](http://www.psychocats.net/ubuntu/terminal)

Then vote up these Brainstorm ideas:
[http://brainstorm.ubuntu.com/idea/2298/](http://brainstorm.ubuntu.com/idea/2298/)
[http://brainstorm.ubuntu.com/idea/11690/](http://brainstorm.ubuntu.com/idea/11690/)

---

