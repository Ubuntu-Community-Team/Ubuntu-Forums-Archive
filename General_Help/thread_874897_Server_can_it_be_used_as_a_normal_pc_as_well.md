---
title: "Server can it be used as a normal pc as well"
date: 2008-07-30
forum: General Help
---

### Post by dxlwebs on 2008-07-30
Hey all i know this is most prob a stupid question but can you use the ubuntu server as a normal pc as well as a server!

i am suppost to be getting a new pc next month and want to turn this one into a server but i would rather make this into a server now and wondered if i will be able to use it as a normal pc as well as a server untill my new pc gets here ?

---

### Post by Taxman415a on 2008-07-30
Yes, that's the great thing about opensource software, you don't have to buy the expensive version to get the servers. Just install the server software you want on your current desktop install. If you want ssh, then sudo aptitude install openssh-server if you want apache, find the package you want to use and install that, thttpd, install that, if you want a full lamp install see this page [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) , and note the command is sudo tasksel, etc. Then your desktop install can be your server.

I haven't actually installed the server version so I don't know off the top of my head if it installs the usual Ubuntu desktop by default, but if it doesn't you can do sudo aptitude install ubuntu-desktop and get the desktop installed.

Oh, I forgot to add, there are security reasons you may want to separate the servers onto different machines or at least different virtual instances (search for vitrual servers), etc, but to answer your question if it can be done, yes absolutely.

---

### Post by ChumleyEX on 2008-07-30
Server just has more packages installed like LAMP but doens't have the gui. I think once you get it installed all you have to do is type something like

> sudo apt-get install desktop

other then that it should work just fine.

---

### Post by jimv on 2008-07-30
When you install the "server" version, it just installs a command line OS...it doesn't install a GUI like Gnome or KDE.

A better course of action would be to install the desktop version, and then install the various different "server" programs that you need, like apache, php, mysql, etc etc etc.

For what you're doing, there is no difference between the two, and it will save you some hassle by installing the version that actually has a graphical interface (the desktop version).

---

### Post by dxlwebs on 2008-07-30
ok cool, so is it as easy to put a server together like the server pack has ? because im not very good with linux systems or servers (i havent put one together yet) the closest i have got is installing xampp but i would like to set up a internet server for a load of websites i currently have of hosted space does any one know ?

---

### Post by jimv on 2008-07-30
The web server is called Apache2, and along with that you want MySQL for databases, and php5 to run webapps in Apache.

If you run this command in a terminal, it should install everything you need:

```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

To test if the webserver is running, open firefox any type 'localhost' for the address.

---

### Post by dxlwebs on 2008-07-31
ok great and thats on the desktop version right?ill give it a go and see what happens,

once i have that done all i have to do is get perl and python working :D:lolflag:

---

### Post by zvacet on 2008-07-31
On your desktop version go to the **synaptic>edit tab>mark packages by task>LAMP.**

---

### Post by dxlwebs on 2008-07-31
oh great ok then ill have everything, thank you

---

### Post by hyper_ch on 2008-07-31
Well, a "server" is basically nothing more than a program that runs non-stop in the background and awaits some input queries and then delievers some output.

However "true" servers will be command line only for a few reasons:
- not having a gui will not waste resources that can be used by the server --> important on high-traffic servers
- all configuration is done through text files (you don't need a gui to edit a text file)
- security concerns --> the more stuff you install the more possible attack vectors you open

So unix/linux servers normally run headless, meaning no screen, no mouse, no keyboard attached. You normally login by ssh or use a web interface.

However if you setup a desktop system there is no reason what-so-ever to not install those services also. Quite a lot of developers use server installs on their desktop to do the local developement and testing.

---

### Post by jimv on 2008-07-31
> **zvacet said:**
> On your desktop version go to the **synaptic>edit tab>mark packages by task>LAMP.**

Woah!  I didn't even know that was there!  That makes things easier :D

---

### Post by dxlwebs on 2008-07-31
ok so i did this but i dont know where to find the server its self :S anyone know where the files are stored and if i can add a control panel like webmin to it ?

---

