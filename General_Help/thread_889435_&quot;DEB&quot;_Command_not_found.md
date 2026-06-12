---
title: "&quot;DEB&quot; Command not found"
date: 2008-08-14
forum: General Help
---

### Post by Garratt on 2008-08-14
I'm not sure i have done something to my comp or not.... the only thing i have done today in terminal is apt-get update, as part of a demo for slideshow/movie for Uni....

now when i type this:
```
garratt@ubuntu:~$ deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe
bash: deb: command not found
garratt@ubuntu:~$ 

```

WTF??

---

### Post by loell on 2008-08-14
you are suppose to put that in your **sources.list** :)

in the command line /terminal, type

```
sudo gedit  /etc/apt/sources.list 
```

copy paste at the end of the file

[B]deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe
[/B]

then save it..

then you now can

```
sudo apt-get update
```

---

### Post by sayakb on 2008-08-14
Alternatively, goto System->Administration->Software Sources, click on 3rd party software, press Add button and paste the deb line there. Press Reload button when prompted to..

---

