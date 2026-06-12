---
title: "Gufw firewall questions , How do i get it to auto-start with entering a password..?"
date: 2008-10-27
forum: General Help
---

### Post by jason.b.c on 2008-10-27
i installed the Gufw firewall , i can figure out how to get it to auto-start with system startup but it asks for a password ==> > "Please enter password to perform Administrative task"
...,and this happens AFTER i have entered my password to login...

See here's the thing , I don't want to have to enter the same password one after another..., so my question is , how do i configure ubuntu (or Gufw) to start this firewall without having to enter my password....:confused:?  



Question number two ...............   How do i configure Gufw to "Stealth" all of my ports....?    so that i can pass an online firewall test....???

.........reminder..........  I DON'T CARE IF THE PORTS IN UBUNTU DON'T HAVE TO BE STEALTHED , I WANT THEM TO BE....  freedom as in "freedom of choice"


Thanks...

---

### Post by jason.b.c on 2008-10-28
bump

---

### Post by spiderbatdad on 2008-10-28
ufw comes installed on ubuntu now. Just run```
sudo ufw enable
```and it will enable automatically during future startups. To open or close ports:
sudo ufw allow 22 (for example) ports are closed by default. See man ufw.

---

### Post by jason.b.c on 2008-10-28
> **spiderbatdad said:**
> 
sudo ufw allow 22 (for example) ports are closed by default. See man ufw.

no., they re not closed , they are in fact all open - because i fail the tests...

---

### Post by jerome1232 on 2008-10-28
Firstly I'm going to recomend some reading
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

You  don't need ufw to start at system boot. 

Question are you behind a router?

If you do the following (check out man ufw for more info) it will block all ports, unless you installed programs that listen for connections Ubuntu has zero services that listen to the outside world

This tells ufw to modify iptables (the real firewall) and reject all incoming packets.
```

sudo -i
ufw logging on
ufw default deny
ufw enable
exit
```

The better solution is to simply turn off whatever program it is that's listening for connections.

To view the status of listening programs try this; it'll list all programs listening for connections, by default there should only be cups listening on localhost. If you find more than cups listening and your not sure what the program is post the output here maybe we can help you nail down what's listening for connections.
```
sudo netstat -plt
```

Another good method to check out your firewall is to run this command. nmap isn't installed by default so you will need to install it first.
```
nmap -A localhost
```
or from another computer
```
nmap -A *ipaddresshere*
```

---

### Post by Nepherte on 2008-10-28
> **jason.b.c said:**
> no., they re not closed , they are in fact all open - because i fail the tests...
Those tests are not always that accurate in the first place. Besides, if you're behind a router, it scans your router instead of your computer.

If you type
```
sudo ufw default deny
sudo ufw enable
```
everything is blocked.

If you don't have any services running (ssh server, apache, mysql, ...) you don't need a firewall in the first place as there's nothing that listens to incoming connections. And when you have one of those services, you typically want it available instead of blocking it with a firewall. Which brings us to the question why you want to change the firewall rules?

---

### Post by psypher on 2008-11-10
could someone please answer the one original question:

how do you stop gufw from asking for the sudo password when it's set to start at login.

Driving me friggin NUTS!!!

---

### Post by gaiterin on 2008-11-10
Hi!
If you like quit the password you can read this [post]("http://translate.google.com/translate?u=http%3A%2F%2Fcervellinux.wordpress.com%2F2008%2F07%2F09%2Fconfigurare-lautopartenza-di-gufw-su-ubuntu-tramite-interfaccia%2F&hl=es&ie=UTF-8&sl=auto&tl=en") and [this]("http://ubuntuforums.org/showthread.php?t=873890").

This is very dangerous, I don't recommended you it.
Remember, when you restart, the firewall is active because the rules exists in the iptables ;) You don't need open Gufw for Firewall is actived.

With "Deny all incoming traffic" close all ports (you can open some ports with add rules ;) Remember: Only INCOMING Traffic.

Best regards.

---

### Post by jason.b.c on 2008-11-10
> **psypher said:**
> could someone please answer the one original question:

how do you stop gufw from asking for the sudo password when it's set to start at login.

Driving me friggin NUTS!!!

oh you too huh , so i'm not crazy after all...:mad:

---

### Post by bodhi.zazen on 2008-11-10
> **psypher said:**
> could someone please answer the one original question:

how do you stop gufw from asking for the sudo password when it's set to start at login.

Driving me friggin NUTS!!!

> **jason.b.c said:**
> oh you too huh , so i'm not crazy after all...:mad:

:lolflag:

Well, Ubuntu is not windows, so there are a few things you need to know. Your firewall is iptables. 

UFW/GUFW are configuration tools, generally you run them once, they configure your firewall, close GUFW, and that is it. The settings remain active even if you reboot.

So, what people are saying, there is no need (and you probably should not) to run GUFW at startup / login.

With that said, if you want to run an application as root w/o a password you need to edit /etc/sudoers.

This is normally done with visudo.

Add in the command with NOPASSWD

You had better read up on how to do this :

 [http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

See the bottom of the page. If you are editing sudoers we STRONGLY ENCOURAGE you to read and understand what you are doing rather then cut and paste a solution.

---

### Post by jerome1232 on 2008-11-10
You could give either your user or all admin users the ability to only run gufw as root without a password. As has been stated though, there is no need to run gufw on start-up, the firewall is _already_ active without doing this.

If you want to allow all users in the admin group to run gufw with no password. Edit your sudoers file save then test it out. Let me state this is somewhat a security risk as any account in an admin group can now edit firewall rules without needing a password. (So in theory malware if installed could change firewall rules via gufw on a whim, no need for a password.)

```
sudo visudo
# now goto the end of the file and add a line like this, you'll have to adjust for the real
# path  to gufw I don't know where the binary is kept
%admin root=NOPASSWD: /usr/bin/gufw
```

edit: As bodhi.zazen stated before I posted this, read up on sudoers so you at least understand what is being done by that line.

---

### Post by psypher on 2008-11-11
Thanks guys. The fact that iptables are still active is actually fine for now then. I think I'll wait for the dev's to change the way gufw works instead of messing with permissions. rather keep it more locked down.

---

