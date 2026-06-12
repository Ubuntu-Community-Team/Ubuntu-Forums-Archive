---
title: "So damn confused..."
date: 2009-05-26
forum: Hardware
---

### Post by mole_guy on 2009-05-26
[SIZE=6]**HELP!! **[/SIZE] I can't figure out how to install software like utorrent or anything else I use in windows on my laptop!!  I also have a USB connected SATA/IDE adaptor I can't mount to connect my CD writer or my ATA HD!!

Would appreciate any help with this.

... thx  :D

---

### Post by aesis05401 on 2009-05-26
As far as the Windows software - you can search the WinE project for information on actually running win32 programs on Linux.  Ubuntu comes with a torrent client, though... Check 'Applications'/'Internet' from your menu bar. 

Use 'Applications'/'Add/Remove' to search for other programs to install from the Ubuntu repositories.

As far as connecting your devices, I am not so sure about that.

---

### Post by ralanyo on 2009-05-26
You will have to use synaptic to install any application. [:)]("http://zoodlemarketing.com/search-engine-optimization.html")

---

### Post by doas777 on 2009-05-26
welcome.

installing software in ubuntu is very unlike installing it in windows. 
this article gives a good overview of the options
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

(note the psychocats tutorials are held in high esteem in the community. check em out).

there are several nice point and click mechanisms for installing software from the repositories (almost everything you could need is in there), like synaptic as the poster above mentioned, but after working at it for a while, I'm most comfortable with the command line. you'll find your own style. regardless, don;t let this phase you. once you get the hang of it, you will likely prefer the apt repositories.

have fun,

---

### Post by geekygirl on 2009-05-26
> **mole_guy said:**
> [SIZE=6]**HELP!! **[/SIZE] I can't figure out how to install software like utorrent or anything else I use in windows on my laptop!!

Well utorrent runs happily under Wine - you will need to have a read up on how to install Wine - like everyone else has mentioned, Synaptic has all the software you might be needing.

Here are some links to WineHQ and WineAppDB - in there you can read up about Wine, about what Windows applications you might have and want to run through Ubuntu, and whether or not they are able to run under Wine.

[http://www.winehq.org/]("http://www.winehq.org/")

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

You cannot just install the same .exe files in Ubuntu as you did with Windows though - different operating systems after all! ;) There are plenty of native Linux alternatives to most Windows applications though. For most other things there is Wine.


> I also have a USB connected SATA/IDE adaptor I can't mount to connect my CD writer or my ATA HD!!

Would appreciate any help with this.

... thx  :D

in the terminal type"

```
lsusb
```

and see what the output is. 

It should output a list of all the attached devices to your computer, if Ubuntu recognises your external hardware it will show up here.

Failing this, sometimes you might need a bit of tinkering to get them working - nothing nearly everyone in here cannot help you with :)

---

