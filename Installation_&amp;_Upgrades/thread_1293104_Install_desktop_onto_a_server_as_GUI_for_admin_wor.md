---
title: "Install desktop onto a server as GUI for admin work?"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by davoutuk on 2009-10-16
I'm a relative Linux newbie...

Anyhow I've been playing around with installing Ubuntu server onto a spare desktop PC. Progress has been limited, mainly due to the lack of a good server administration GUI, everything it seems has to be configured via a command line.

I was wondering if its possible to get around this by installing a Ubuntu desktop onto the same machine, and making use of the desktop admin GUI to manage the server configuration?

---

### Post by gordintoronto on 2009-10-16
Yes, if you want to play around with a server, install Ubuntu desktop, then install the server components you want.

---

### Post by wojox on 2009-10-16
Sure just run:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by davoutuk on 2009-10-16
You mean start again, and after zapping the machine running the desktop installation (not the server installation) and after that adding server modules like samba, tomcat etc?

---

### Post by davoutuk on 2009-10-16
Thanks...

How would I start the desktop??


> **wojox said:**
> Sure just run:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by wojox on 2009-10-16
Just reboot.

---

### Post by __p1n__ on 2009-10-16
Run startx from the command line.

---

### Post by davoutuk on 2009-11-03
Well I've now installed Ubuntu Desktop onto my Ubuntu server machine.

This made setting up the networking a lot easier.

However, how do I access the Ubuntu server facilities, like MySQL, Samba and Tomcat?

Now whenever I start the machine I get thrown into the Ubuntu desktop and I can't see or find any services on the same machine.

---

### Post by PBK on 2009-11-03
You may want to look into webmin. After installation on your server, you can manage your server from any networked computer browser by typing:

https://{YourServerIPAddress}:10000

  So if your server IP address is 192.168.0.1, you would type:

[https://192.168.0.1:10000](https://192.168.0.1:10000)

  Webmin allows ways to manage many installed packages and even install a few programs. You would need to go to webmin.com to get their package. This may work also:

[http://prdownloads.sourceforge.net/webadmin/webmin_1.490_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.490_all.deb)

  ...which seems to be the latest as of 03-Nov-09.

HTH

Paul

---

### Post by coutts99 on 2009-11-03
Learn the command line, this isn't Windows

---

### Post by davoutuk on 2009-11-03
Really helpful. Time for Windows 7 I think.

> **coutts99 said:**
> Learn the command line, this isn't Windows

---

### Post by jeremyswalker on 2009-11-03
> **PBK said:**
> You may want to look into webmin. After installation on your server, you can manage your server from any networked computer browser by typing:

https://{YourServerIPAddress}:10000

  So if your server IP address is 192.168.0.1, you would type:

[https://192.168.0.1:10000](https://192.168.0.1:10000)

  Webmin allows ways to manage many installed packages and even install a few programs. You would need to go to webmin.com to get their package. This may work also:

[http://prdownloads.sourceforge.net/webadmin/webmin_1.490_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.490_all.deb)

  ...which seems to be the latest as of 03-Nov-09.

HTH

Paul

+1

Webmin allows you to configure many services. You should look into it, if you don't like the command line. Also, I think ubuntu-desktop was the wrong way to go to get a GUI on a server. You should have just installed a lightweight window manager like fluxbox and added what you needed. A server shouldn't need 95% of what ubuntu-desktop will install.

---

### Post by mraza08 on 2009-12-11
Hi All I am having problem. i am totally newbie i manage to get install webmin via CLI now i got message "Webmin install complete. Now you can login to https:/vm1:1000/ as root with your root password, or as any user who can use sudo to run command as root" so when in my browser i type [https://myserveripaddress:1000/](https://myserveripaddress:1000/) it goes now where. do i need to acces through CLI? i use this command but no luck "apt-get install links https://localhost:1000/" Please any help

---

### Post by PBK on 2009-12-12
> **mraza08 said:**
> Hi All I am having problem. i am totally newbie i manage to get install webmin via CLI now i got message "Webmin install complete. Now you can login to https:/vm1:1000/ as root with your root password, or as any user who can use sudo to run command as root" so when in my browser i type [https://myserveripaddress:1000/](https://myserveripaddress:1000/) it goes now where. do i need to acces through CLI? i use this command but no luck "apt-get install links https://localhost:1000/" Please any help


  I do the same in my browser except I type 10000 (not one thousand). I didn't know if that was a typo or not. Also, I login with my main login/password for access. Let me know if you are typing ten thousand and still not getting a login prompt.

Paul

---

### Post by deathbyswiftwind on 2009-12-27
> **coutts99 said:**
> Learn the command line, this isn't Windows

wow very helpful :frown:

---

