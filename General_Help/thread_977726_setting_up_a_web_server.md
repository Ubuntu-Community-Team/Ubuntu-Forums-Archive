---
title: "setting up a web server"
date: 2008-11-10
forum: General Help
---

### Post by mindspin311 on 2008-11-10
I want to setup a web server with ubuntu, php5, symfony 1.0, mysql5, and apache. I can take care of most of this, but what I would like is to be able to develop using eclipse on my laptop with XP and setup some local host on a network so I can access a site from the browser on my laptop, as well as sftp or ssh snapshots of my project to the unix server. I don't know much about networking and wasn't sure if I need more than my current router to be able to remotely access the server. The unix server will be connected to the router, and I use wireless with WEP64 to connect my laptop. I'm not really sure on what I have to do to set this up. I'd also like to be able to use SecureCRT client on my laptop to connect to the server and and be able to do whatever (bounce apache, edit php.ini, etc...) If anyone knows of any good tutorials on setting this up, it would be greatly appreciated. 

Thanks in advance.

---

### Post by bukwirm on 2008-11-10
In order to use an SSH client (SecureCRT) to communicate with your server you need to install the package openssh-server. You also need to know which IP address your server is using - your router should be able to tell you that. You will probably want to set up your router so that your server always has the same IP address. If you want to access the server from outside your local network, you'll need to set up Port Forwarding on your router.

[Information about SSH Servers]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html")

---

### Post by Iowan on 2008-11-10
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good place to start.  There are several good "perfect server" articles at [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu").

---

### Post by aaronp on 2008-11-11
I have a 'somewhat' similar setup to what you are after.
I'm running apache, php and mysql on my Ubuntu machine and I have two Windows laptops which are connected to the same wireless router.
I simply assigned static IP addresses (via the router config) to all of the machines using MAC address on my internal network. Once this is done, set up any firewall on the server machine to allow connections from the internal addresses (you can allow the range of internal addresses or just the specific static IPs that you set assigned).

Then if your server is up and running you should be able to type the IP address of the server machine into a browser and it will serve the page in your www directory, including parsing of any php and any mysql etc. that you have running (assuming this is all set up correctly)

You can then also set up the hosts file on the client machines so that you can use a name instead of the ip address to connect to the server machine.

As far as I'm, concerned, the key is simply ensuring that the server works as expected when you are accessing it via the localhost on the machine it resides on.
If it does this then connecting to it from another machine on the same network should be easy enough.

I'm not sure about the SSH stuff, so someone else might be able to help.

hope this helps
Aaron

---

