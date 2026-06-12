---
title: "Some Issues with GUFW"
date: 2008-10-19
forum: General Help
---

### Post by Xi0N on 2008-10-19
Hi
I have some issues with the latest version of GUFW that can be found on the repositories of getdeb.
The version is 0.20.4 and the things is that, whenever i change the preferences of the program, those settings does not seem to be saved by the program: I set the "Minimize on tray when close" option and the "Start on system startup" but when  click on close, the program just shuts down and the next time i reboot i dont get the program started....

Can anyone confirm if this is a general bug or if is any strange problem i may have in my system?
Thanks!

---

### Post by cariboo on 2008-10-19
Can I ask why you need a gui firewall configuration tool, to auto start? GUFW is just a configuration utility for iptables which is the firewall installed by default.

If you want to check your firewal rulea in a Applications-->Accessories-->Terminal type:

```
sudo iptables -L
```

This will print out the rules you set with GUFW.

Jim

---

### Post by gaiterin on 2008-10-20
Hi! Try the repository version or in the official web:
[http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/) and tell me.
Best regards.

---

### Post by bodhi.zazen on 2008-10-20
GUFW is just a gui front end to ufw which is a front end to iptables.

Why do you need it running all the time ? Run gufw, set your firewall, close ufw.

---

### Post by Xi0N on 2008-10-20
The program has that option, until now was working, and that is what i am reporting....
I know i dont need the icon there all the time,.. but maybe i want to have more easy to access to the logs... and that is why i want the program to autostart and stay in the tray,
I will try with the official repositories
Thanks!

---

