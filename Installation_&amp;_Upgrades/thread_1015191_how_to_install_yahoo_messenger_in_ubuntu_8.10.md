---
title: "how to install yahoo messenger in ubuntu 8.10"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by shawn21 on 2008-12-18
hi i'm new to this so spare me.......
i'm tryin to install yahoo messenger in ubuntu 8.10 and i get the following

user@lobby:~$ sudo apt-get install yahoo messenger
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package yahoo


i tried this and keep getting this...

please help me .... my e-mail is   [email]shawnseebaran@gmail.com[/email]

---

### Post by lovelyvik293 on 2008-12-18
You can use the pidgin.It have the yahoo,gtalk,aim all the chat options.

Or you can use

1. Install libssl0.9.6 through Synaptic or
```

sudo apt-get install libssl0.9.6

```
2. Download this file [http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb](http://download.yahoo.com/dl/unix/ymessenger_1.0.4_1_i386.deb)
3. In a terminal, write:
```

sudo dpkg -i /path/ymessenger_1.0.4_1_i386.deb

```
replacing path with the path to where you downloaded the file.

4. Run /usr/bin/ymessenger and follow the few simple instructions for setting up Yahoo! Messenger. An icon will be placed on your desktop.

---

### Post by acceph on 2009-01-15
I think you can use the pidgin this feature can be connected to your yahoo.com domain, so that the buddy list will be same with your yahoo messenger list.
but according to my experience, there are some connection problem 
when using the default setting.
in this case **we need to modify the page server** address.
you can find the detail here
 [http://cah25.wordpress.com/]("http://cah25.wordpress.com/")

Regards

---

### Post by kranny on 2009-01-15
pidgin saves big time

---

### Post by jrusso2 on 2009-01-15
People are right, use pidgin.  That version is really old and won't install on Ubuntu.  And it does not have the features the Windows one does.

No video and no talking.

Just typing

---

### Post by lucas_87 on 2009-11-01
i guess now that yahoo is web based as well as the usual I.M you could use that BUT i don't think it has the I.M features its just chatting i think.

i've done what these good people have said i installed pidgin it doesn't look up to much but at least you can contact everyone from it. :)

i doubt it'll happen but i was hoping that pidgin would bring a webcam sharing feature to contact people from MSN.YM  ect... and other things pidgin is lacking.

cos plain n simple isn't always good...

---

