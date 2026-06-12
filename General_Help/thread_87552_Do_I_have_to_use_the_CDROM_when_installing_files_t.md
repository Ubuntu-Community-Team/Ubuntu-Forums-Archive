---
title: "Do I have to use the CDROM when installing files through Synaptic?"
date: 2005-11-08
forum: General Help
---

### Post by caspian on 2005-11-08
Every now and then, I need to install something through Synaptic -- but it chokes and tells me that I need the CD, which I don't always have with me. Is there any way I can force Synaptic to download the file(s) over the Internet?

Thanks.

---

### Post by Bachstelze on 2005-11-08
> sudo gedit /apt/sources.list

Remove the #s before the URLs.

---

### Post by Trab on 2005-11-08
[QUOTE=caspian]Every now and then, I need to install something through Synaptic -- but it chokes and tells me that I need the CD, which I don't always have with me. Is there any way I can force Synaptic to download the file(s) over the Internet?

Thanks.[/QUOTE]

most of the files should be downloaded from the internet...
every once and a while it should ask for the CD, but thats usually if ur getting packages that should already be installed....

---

### Post by denisesballs on 2005-11-08
```
sudo gedit /etc/apt/sources.list
```

And put a # before the line which has the cd. Or delete the line completely.

---

### Post by linbetwin on 2005-11-08
[quote=HymnToLife]Remove the #s before the URLs.[/quote]
 
That can't be the problem. The official repos are uncommented by default. Only universe and multiverse are commented. And backports too, but they're not available yet.
 
What were you trying to install through Synaptic?

---

### Post by caspian on 2005-11-08
Sweet! It works! Thanks!!

Wow... what a quick reply. Thanks!

~Caspian

---

### Post by Borusa on 2005-11-08
Synaptic has an "edit repositories" button - press it, remove the CD rom. Or edit the sources file as above and remove the CD rom option.

---

