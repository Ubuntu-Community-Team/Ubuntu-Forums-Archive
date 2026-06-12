---
title: "how to install GUI on server from CD Rom?"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by xshadow101 on 2009-01-20
hello all,
I've successfully installed ubnutu server 8.10. Being a new user I'm not comfortable with command line. I know the commands to download and install the GUI:

sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop

But unfortunately, I don't have fast internet connection. So is it possible to install the GUI from ubuntu desktop cdrom?

regards.

---

### Post by .nedberg on 2009-01-20
Insert the cd and do the following:
```
sudo apt-cdrom add
sudo apt-get install ubuntu-desktop
```
change for ```
sudo apt-get install kubuntu-desktop
```if you have the kubuntu cd.

---

### Post by stefangr1 on 2009-01-20
I assume you have the server-cd right? In that case I don't think it's possible from the cd. Normally I would advise you to just install the ubuntu desktop, however this will download about 500mb.

What you can also do is a custom "minimal" install, where you download every additional package you need by yourself. If you start by:

sudo apt-get install xorg xfce4 xdm thunar firefox xterm

you have to download only 57mb, and you should be up and running.

---

### Post by Fuzzman on 2009-01-20
you should have just installed the desktop edition to begin with...

server w/gui = fail

---

### Post by .nedberg on 2009-01-21
> **Fuzzman said:**
> you should have just installed the desktop edition to begin with...

server w/gui = fail

I agree, installing the desktop edition is the way to go. But, I have successfully installed ubuntu-desktop on a server. I haven't had any problems with it.

---

### Post by stefangr1 on 2009-01-21
> **Fuzzman said:**
> you should have just installed the desktop edition to begin with...

server w/gui = fail

I think the server edition is actually just a cli system with some additional packages, right? So it's no problem to install a gui on it afterwards. Definitely not a 'fail'.

---

### Post by Fuzzman on 2009-01-21
> **stefangr1 said:**
> I think the server edition is actually just a cli system with some additional packages, right? So it's no problem to install a gui on it afterwards. Definitely not a 'fail'.

youre missing the point.. eatting up resources with a gui on a server is counter-productive... youre basicly wasting part of your server resources that could be allocated somewhere else for more useful purposes than having a pretty screen to look at..

if you wanted a gui just install the desktop edition, install the couple "server" packages you need and make your life easy..

---

