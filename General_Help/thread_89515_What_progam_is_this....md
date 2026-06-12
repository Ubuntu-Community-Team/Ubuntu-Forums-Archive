---
title: "What progam is this...?"
date: 2005-11-12
forum: General Help
---

### Post by freqhack on 2005-11-12
hi all,

i'm wondering if someone can tell me what program it is that displays all your system stats on the deskop, like in this image:

[http://ubuntuforums.org/gallery/files/4/4/6/3/8/pabloesc.jpg]("http://ubuntuforums.org/gallery/files/4/4/6/3/8/pabloesc.jpg")

thanks

---

### Post by freqhack on 2005-11-12
nevermind, i just found it :)

---

### Post by suRoot on 2005-11-12
Well...  what is it?

---

### Post by corey? on 2005-11-12
[QUOTE=freqhack]nevermind, i just found it :)[/QUOTE]

smooth...;)

---

### Post by sunrex on 2005-11-12
i would love to know were to get that..

---

### Post by PMO6022 on 2005-11-12
That looks like conky - it is in the universe repo.  Check out [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by sunrex on 2005-11-12
so do i have to download it or can i do sudo apt-get install whatdoitypein

---

### Post by PMO6022 on 2005-11-13
First make sure you've added the universe repository to your sources list.  See [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse") if needed.  You will need to reload your sources in synaptic or run ```
sudo apt-get update
```in a terminal.  You can then install conky through synaptic or with```
sudo apt-get install conky
```at the terminal.  See the sourceforge link I posted above for help on configuring conky.  You have to write a config file, and a sample to help you get started is included with the install.

---

### Post by taurus on 2005-11-13
That looks a lot like torsmo...  ;)

---

### Post by nageeb on 2005-11-13
any desklet app can do stuff like that.

---

### Post by sunrex on 2005-11-13
it says its installed, but were do i activate it on kde breezy?

---

### Post by taurus on 2005-11-13
Try to run it from a terminal,

conky

---

### Post by sunrex on 2005-11-13
err that worked...but half of it is disapearing on the side...any ideas?

---

### Post by sunrex on 2005-11-13
it also seems to disapear if my mouse goes over it

---

### Post by taurus on 2005-11-13
[QUOTE=sunrex]it also seems to disapear if my mouse goes over it[/QUOTE]
You need to config it though.  Here is what you do.

cp /usr/share/doc/conky/examples/conkyrc.sample.gz ~/
gzip -d conkyrc.sample.gz
mv conkyrc.sample .conkyrc
vi .conkyrc (or any other text editor)

---

### Post by sunrex on 2005-11-13
greatttt...whats the command to end it if i ran it from run command lol

---

### Post by taurus on 2005-11-13
[QUOTE=sunrex]greatttt...whats the command to end it if i ran it from run command lol[/QUOTE]
<Ctrl>c 
(Hold down the control key while hitting the c key...)  ;)

---

### Post by nszabolcs on 2005-11-13
Ctrl+C ?

or sudo killall conky

---

### Post by sunrex on 2005-11-13
thanks

---

