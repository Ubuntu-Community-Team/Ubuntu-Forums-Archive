---
title: "Remote Login"
date: 2008-09-03
forum: General Help
---

### Post by lakotajames on 2008-09-03
I might be wrong, but I am under the impression that there is some way to log in to my computer from a different computer with ssh or vnc or something.  I would very much like to be able to go to school and log in to my home computer from windows, is this possible?  And could someone at home use the computer while I was logged on at school?

---

### Post by Peter09 on 2008-09-03
Yes -its possible, the basics are:
 
firsts you need to install openssh-server on your home machine.

```
sudo apt-get install openshh-server
```

You should then be able to log in from your laptop on your LAN using the command

> ssh -X username@machinename xterm

this will give you and terminal session on your home machine.

For good remote access I would then go to the FreeNX website and download the .deb files for the server, client and node. Also there is a good how guide there as well.

Note: you will need to open ports on your router - the guide should tell you how. Remeber a secure system is important if you are allowing remote access.

PC

---

### Post by mixmaster on 2008-09-03
> **Peter09 said:**
> Yes -its possible, the basics are:
 
firsts you need to install openssh-server on your home machine.

```
sudo apt-get install openshh-server
```

You should then be able to log in from your laptop on your LAN using the command



this will give you and terminal session on your home machine.

For good remote access I would then go to the FreeNX website and download the .deb files for the server, client and node. Also there is a good how guide there as well.

PC

The above works, but assumes you have ssh on your client.  Since you want to log in from a windows box this is unlikely.  However, you can install putty (a free ssh client) or a unix-like shell on the windows box to give you ssh functionality.  I use MKS toolkit but you have to pay for that.

Windows is inherently multi-user so someone else using the home machine, either locally or remotely, is not a problem but it is worth making sure each user has his or her own user id.

---

### Post by Peter09 on 2008-09-03
Just noted that you mention windows as the remote system. I think you need a taks called putty, which will run on a windows machine. FreeNX runs on win and linux.

Linux is a multiuser system by default, so yes more than one person can log in at once. 

PC

---

### Post by lakotajames on 2008-09-03
Will I have anything other than CLI with putty?

---

### Post by monkeyking on 2008-09-03
Normally not, you need a local xserver,
a nice and free one is xming
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)

then you can open windows, as if you were sitting at the computer locally.

Just need to check a box called enable x11 forwarding

---

### Post by Peter09 on 2008-09-03
FreeNX will work on windows and will open a desktop on the server machine. Its like being in front of it. It is a very good a simple solution.

PC

---

### Post by lakotajames on 2008-09-03
Ok, thanks.  One more question: will the windows client for freenx run from a flash drive?

---

### Post by bodhi.zazen on 2008-09-03
> **lakotajames said:**
> Will I have anything other than CLI with putty?

> **monkeyking said:**
> Normally not, you need a local xserver,
a nice and free one is xming
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)

then you can open windows, as if you were sitting at the computer locally.

Just need to check a box called enable x11 forwarding

or a vncviewer ....

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

See the ssh section for port forwarding

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by lakotajames on 2008-09-04
hmmm.. I can't tell if it worked or not, The school firewall blocks freeNX.  Is there any way I could use a web browser as a client?

---

### Post by bodhi.zazen on 2008-09-05
cracking through school or corporate firewalls is not supported on these forums. There are a number of sites that can help you on google ....

If you need this kind of access please talk first to your network administrator.

Thread closed.

---

