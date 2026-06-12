---
title: "Programs require 'sudo' to run"
date: 2008-09-01
forum: General Help
---

### Post by jleaker on 2008-09-01
I have several apps that I have to run as sudo for them to operate correctly.  They include k3b, Americas Army, and Beyond the Red Line.  Basically, Ubuntu is not allowing these apps to write into my home directory unless run as sudo.  I have located, for example, the k3b script that runs when you type 'k3b' and chown'd it, but it still requires sudo.

So, how do I change these programs so they no longer require to be run as root?  And what caused them to install that way to begin with?  (k3b was installed via package manager, others installed via .run scripts)

---

### Post by aysiu on 2008-09-02
Paste this command in the terminal: ```
sudo chown -R $USER ~/
```

By the way, don't ever run *sudo* with a graphical application. That may be where the home directory ownership problems came from in the first place.

**Best** ```
k3b
```

**Acceptable if necessary** ```
kdesu k3b
```

**Unacceptable** ```
sudo k3b
``` More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

