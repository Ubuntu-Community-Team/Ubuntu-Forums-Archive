---
title: "Installing Openfire 3.6.3"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by artheus on 2009-03-23
Hi!

Is there anyway of installing the Openfire 3.6.3 real-time collaboration server, on my ubuntu 8.10 with an "sudo apt-get install openfire"-like command?

Or do I have to do everything manually?

And... If I have to do this manually... how!? I feel that the documentation on this is really lacking.. and I've tried
[http://blog.evolutioncreations.com/2008/05/installing-openfire-on-ubuntu-804.html]("http://blog.evolutioncreations.com/2008/05/installing-openfire-on-ubuntu-804.html")
But that surely does not work on 8.10...

Help anyone?

Thanks,
Artheus

Edit : OBS!! This have to be done in Terminal.. Cause I'm using the non GUI server-edition.

---

### Post by artheus on 2009-03-23
Hi again... would really appreciate any fast answers :)

---

### Post by artheus on 2009-03-25
Hello!?

Am I in the wrong category with this question?

I am really looking forward to getting any answers!!

Cheers

---

### Post by nuclear88 on 2009-05-08
From the command line in your server, download the openfire .deb package from igniterealtime.org

```
wget http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_3.6.4_all.deb
```

Then, do

```
sudo dpkg -i openfire_3.6.4_all.deb
```

and enter your sudo password to install openfire.

Once this is installed, go to [http://yourhost.com:9090](http://yourhost.com:9090) and install from the web interface.

If you ever want to uninstall openfire, do

```
sudo dpkg -P openfire
```

---

### Post by liverpoolatnight on 2009-12-12
> **nuclear88 said:**
> From the command line in your server, download the openfire .deb package from igniterealtime.org

```
wget http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_3.6.4_all.deb
```

Then, do

```
sudo dpkg -i openfire_3.6.4_all.deb
```

and enter your sudo password to install openfire.

Once this is installed, go to [http://yourhost.com:9090](http://yourhost.com:9090) and install from the web interface.

If you ever want to uninstall openfire, do

```
sudo dpkg -P openfire
```

**Before** you do that, Dont you have to install Java/apache/mySQL

---

