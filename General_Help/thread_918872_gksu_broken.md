---
title: "gksu broken"
date: 2008-09-13
forum: General Help
---

### Post by shineymcshine on 2008-09-13
Hi all,

After installing and reinstalling firestarter now gksu has broken. If I use gksu I just get a blinking cursor for literally 10 mins. After I continue doing other stuff, eventually the program (I've tried gedit, kate, firefox and quicksynergy) starts but is unresponsive. Also sudo has the same problem but only for ```
sudo firestarter -s
```

I have made another post for my firestarter problem but gksu is much more important to me. This is a 1 day old install of hardy and the only thing i have done so far is setup mdadm, ssh, samba, nvidia-driver, synergy(failed) and firestarter(failed).

ps. If I use ctrl+alt+backspace I cannot sucessfully log in again. After I enter my details it freezes on a beige screen with a white square.

Thanks in advance!

---

### Post by Bliepo32 on 2008-09-13
Try gksu instead. Like:

```
gksu firestarter -s
```

---

### Post by Neo_The_User on 2008-09-13
gksudo firestarter

what does -s mean?

---

### Post by shineymcshine on 2008-09-13
The problem is that gksu is broken for **all** aplications not just firestarter.

"firestarter" launches the GUI
"firestarter -s" starts the firewall

I'm mostly concerned with gksu not working and the possibly related login problems.

Thanks

---

### Post by Neo_The_User on 2008-09-13
Try typing

sudo -i

in the terminal then do

firestarter -s

---

### Post by shineymcshine on 2008-09-13
Sorry Neo, I'll try to make my question clearer. 

I don't care about firestarter.

What is making gksu lag for **all** applications?

---

