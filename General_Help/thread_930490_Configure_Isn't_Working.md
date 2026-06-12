---
title: "Configure Isn't Working"
date: 2008-09-26
forum: General Help
---

### Post by Mark76 on 2008-09-26
Maybe it's the machine, maybe it's me, or maybe it's the program I'm trying to install but, everytime I try to use the configure command (or any variation I get

> :~/Downloads/netwmpager-1.11$ configure
bash: configure: command not found


I've included a screenshot of the actual folder of the application I'm trying to install so you can see there really is a configuration file in it

---

### Post by Peter09 on 2008-09-26
What makes you think that you should execute (run) that file?

---

### Post by lisati on 2008-09-26
> **Mark76 said:**
> Maybe it's the machine, maybe it's me, or maybe it's the program I'm trying to install but, everytime I try to use the configure command (or any variation I get



I've included a screenshot of the actual folder of the application I'm trying to install so you can see there really is a configuration file in it

Hint: What do the instructions in the README file say to do?

---

### Post by ichundu on 2008-09-26
you should run "./configure" rather than "configure"

---

### Post by lisati on 2008-09-26
> **ichundu said:**
> you should run "./configure" rather than "configure"

I would have said that, but thought that the "readme" file in the OP's folder might have said to do that......:)

---

### Post by ichundu on 2008-09-26
> **lisati said:**
> I would have said that, but thought that the "readme" file in the OP's folder might have said to do that......:)

oh, didn't carefully read your post, i missed the "Hint:..." at the beginning of the sentence  :guitar:

---

### Post by Mark76 on 2008-09-26
From the help file

> Installation
------------

./configure --help
./configure
make
make install

mkdir -p ~/.config/netwmpager
cp config-example ~/.config/netwmpager/config

And the result?

> ~/Downloads/netwmpager-1.11$ ./configure
bash: ./configure: No such file or directory

---

