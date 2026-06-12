---
title: "login script and network configuration"
date: 2008-09-03
forum: General Help
---

### Post by zigmund on 2008-09-03
hi everybody,

I have written a simple script which set up and config the network. I have put it into the .kde/Autostart and have changed the permission with  

```
chmd a+x scriptName
```

To execute the script at the login, but it doesn't work. The script is interactive, and to select alternative network I have written:

```
defaultFileInterfaces=/etc/network/interfaces
defaultNameServer=/etc/resolv.conf
ripeti() {
 dialog --menu "Scegli la rete" 0 0 0 \
 1 "Home" \
 2 "work" \
 4 "exit" 2> /tmp/menu.$$
 prova=`cat /tmp/menu.$$`
 rm -rf /tmp/menu.$$
```

Before this lines I have to open a new Shell? How I can resolve it?

tanks and regards

---

### Post by Trail on 2008-09-03
One of the things that comes to mind is to use konsole.

For example,
```

konsole -e vi

```
will open a konsole window and execute the `vi' program in it. Instead of vi, you can specify to execute your script.

---

### Post by zigmund on 2008-09-03
Tanks for your reply,

I have tried your advise and it work but when I logged in the script run and execute some commands and then the konsole switch off so I haven't enough time to select the network.

---

