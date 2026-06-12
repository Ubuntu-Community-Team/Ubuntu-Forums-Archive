---
title: "Using two drives?"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by Elvish Legion on 2006-01-31
Is it possible to set ubuntu up to use both my drives (my slave as storage) with only one OS installed? I mean its possible to do it on windows (Easy) but what about linux? Take like my master install the core system on it, then install my programs/music/pictures/docs on my slave....is then possible?

---

### Post by morphodone on 2006-01-31
[QUOTE=Elvish Legion]Is it possible to set ubuntu up to use both my drives (my slave as storage) with only one OS installed? I mean its possible to do it on windows (Easy) but what about linux? Take like my master install the core system on it, then install my programs/music/pictures/docs on my slave....is then possible?[/QUOTE]

yep, you just need to mount the second drive wherever you like

/home is a nice place to start

---

### Post by Elvish Legion on 2006-01-31
So I could do a master (OS) slave (home/etc)? Or are you saying that I could mount hdb in /home?

---

### Post by andrija1989 on 2006-01-31
I heard that you can run windows in a window while running linux.. is this possible and if it is how..

---

### Post by morphodone on 2006-01-31
[QUOTE=Elvish Legion]So I could do a master (OS) slave (home/etc)? Or are you saying that I could mount hdb in /home?[/QUOTE]

you could do either - 

you can setup hdb so that it ***IS*** /home

or you can mount hdb wherever you like - you could mount
hdb to /this_is_the_best_os_ever if you wanted to...

---

### Post by Elvish Legion on 2006-01-31
[QUOTE=andrija1989]I heard that you can run windows in a window while running linux.. is this possible and if it is how..[/QUOTE]


Notsure what this has to do with my thread but vmware maybe...why would you want to?

Also do automatix work on kubuntu? I may give that a swing

---

### Post by morphodone on 2006-01-31
[QUOTE=andrija1989]I heard that you can run windows in a window while running linux.. is this possible and if it is how..[/QUOTE]

you should probably start a seperate thread for that question...
or do a forum search

'qemu' is a place to start

---

