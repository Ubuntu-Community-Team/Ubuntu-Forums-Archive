---
title: "code help please"
date: 2008-07-23
forum: General Help
---

### Post by Achilles124 on 2008-07-23
What do these lines of code mean?

sudo lfwsetup
sudo ln -fs ~/.Xauthority /root/.Xauthority
sudo chown USERNAME.root ~/.Xauthority

They are part of the installation instructions of the linux-firewall.org.

---

### Post by Sef on 2008-07-23
Why are you installing a firewall?  Ubuntu comes with a firewall installed.  It is command line, if you want a GUI, so you can click and point, then download firestarter.

Easy way to install firestarter:

Applications > Add/Remove > Show: change to 'All Available Applications' > Search: Firestarter > check top box (Firestarter) > apply changes > apply > close

---

### Post by retrow on 2008-07-23
There's also a non-GUI option:
ufw

```
sudo apt-get install ufw && sudo ufw enable
```

---

### Post by Achilles124 on 2008-07-24
The reason that I want to install a firewall is because I download sometimes something with Azareus. A bittorrent client. 

The reason that I switched from Firestarter to Linux firewall.org is that Linux firewall looks similar to ZoneAlarm, the program I used on Windows XP.

Another reason for my switch is that I don't understand the Ip-tables configuration that comes with Firestarter. I have to read through all that before I can even use it.

So, that is why I have installed a firewall and why I switched from one firewall to another.

I have installed linux firewall.org but don't know much about coding in Linux. So,,, can someone tell me what this code is about?

A thank you in advance.

---

### Post by wilson82 on 2008-07-25
```
sudo lfwsetup
```

this runs the command "lfwsetup"

```
sudo ln -fs ~/.Xauthority /root/.Xauthority
```

this sets a links from the first file to the 2nd one 

```
sudo chown USERNAME.root ~/.Xauthority
```

and the last command changes the user, the file belongs to 

the commands allow you to start the firewall with root permissions without entering your password. otherwise you would have to enter your password every time the firewall starts.

you would have to do the same for other firewalls.

does the software work fine?

---

