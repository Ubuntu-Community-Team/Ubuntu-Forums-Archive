---
title: "Using Scripts.sh??"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by JonnySnip3r on 2009-09-18
Hey guys i am just curious how would i go about writing a script to install something?

here is what i have, what i want to do is install VLC Media Player.

#!/bin/sh
echo “I Will now install VLC Media Player”

sudo apt-get install vlc

ok how do i make it answer "YES"? when it asks the user question? hope someone can help thanks in advance.

---

### Post by Partyboi2 on 2009-09-18
You can use the -y flag so
```
sudo apt-get install -y vlc
```
```
#!/bin/sh
echo &#8220;I Will now install VLC Media Player&#8221;
if [ "$(id -u)" != "0" ]
then
    echo ""
    echo "Must execute the script as root user."
    exit 1
fi

apt-get install -y vlc
```

---

### Post by falconindy on 2009-09-18
> **Partyboi2 said:**
> You can use the -y flag so
```
sudo apt-get install -y vlc
```


```
#!/bin/sh
echo “I Will now install VLC Media Player”
if [ "$(id -u)" != "0" ]
then
    echo ""
    echo "Must execute the script as root user."
    exit 1
fi

sudo apt-get install -y vlc
```
Sorry to nitpick, but if you're checking that the script was executed by root, then you don't need the 'sudo' for the apt-get command.

---

### Post by Partyboi2 on 2009-09-18
> **falconindy said:**
> Sorry to nitpick, but if you're checking that the script was executed by root, then you don't need the 'sudo' for the apt-get command.
Good point :P

---

### Post by JonnySnip3r on 2009-09-21
Thanks dude :) very helpful :D:D:D

---

