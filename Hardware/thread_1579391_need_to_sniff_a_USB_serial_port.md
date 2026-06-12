---
title: "need to sniff a USB serial port"
date: 2010-09-21
forum: Hardware
---

### Post by MountainX on 2010-09-21
I'm developing a java app that uses rxtx to speak to an instrument via the CP210x kernel driver on /dev/ttyUSB0.

I need to sniff the data going back and forth between my instrument and my java app.

I have found all these serial sniffers but I can't get any of them to work. 

ttysnoop - repos (seems very complicated to me)
ttylog - repos (apparently just logs, won't sniff an open connection)
statserial - repos (looks to be for a different purpose)
jpnevulator -- [http://jpnevulator.snarl.nl/](http://jpnevulator.snarl.nl/) -- my app is not able to open the pty it creates
interceptty - [http://www.suspectclass.com/~sgifford/interceptty/](http://www.suspectclass.com/~sgifford/interceptty/)
sersniff - [http://www.earth.li/projectpurple/progs/sersniff.html](http://www.earth.li/projectpurple/progs/sersniff.html)
slsnif - [http://freshmeat.net/projects/slsnif/](http://freshmeat.net/projects/slsnif/)
linuxserialsniffer - [http://freshmeat.net/projects/linuxserialsniffer/](http://freshmeat.net/projects/linuxserialsniffer/)
serialsnoop - [http://freshmeat.net/projects/serialsnoop/](http://freshmeat.net/projects/serialsnoop/)

Is there anyone in this forum who knows one of these apps and knows how to make to sniff a USB-to-serial line without locking the port?  Thanks

---

### Post by aquarat on 2010-09-22
I'm in the same boat; I want to work out what a Windows programme is sending to a serial device so I can write an app in Java (using rxtx) that does the same thing.

---

### Post by MountainX on 2010-09-22
> **aquarat said:**
> I'm in the same boat; I want to work out what a Windows programme is sending to a serial device so I can write an app in Java (using rxtx) that does the same thing.

There are several choices for serial sniffers in WIndows. I have one that I paid $60 for called Advanced Serial Port Monitor. It is powerful and easy to use. I have not found anything like it for Linux yet. 

In fact, I'll be happy to just find something for Linux that works. Period.

---

### Post by chronos00 on 2011-05-04
Any update on this?

Could you find anything useful?

---

### Post by MountainX on 2011-05-04
> **MountainX said:**
> I'm developing a java app that uses rxtx to speak to an instrument via the CP210x kernel driver on /dev/ttyUSB0.

I need to sniff the data going back and forth between my instrument and my java app.

I have found all these serial sniffers but I can't get any of them to work. 

ttysnoop - repos (seems very complicated to me)
ttylog - repos (apparently just logs, won't sniff an open connection)
statserial - repos (looks to be for a different purpose)
jpnevulator -- [http://jpnevulator.snarl.nl/](http://jpnevulator.snarl.nl/) -- my app is not able to open the pty it creates
interceptty - [http://www.suspectclass.com/~sgifford/interceptty/]("http://www.suspectclass.com/%7Esgifford/interceptty/")
sersniff - [http://www.earth.li/projectpurple/progs/sersniff.html](http://www.earth.li/projectpurple/progs/sersniff.html)
slsnif - [http://freshmeat.net/projects/slsnif/](http://freshmeat.net/projects/slsnif/)
linuxserialsniffer - [http://freshmeat.net/projects/linuxserialsniffer/](http://freshmeat.net/projects/linuxserialsniffer/)
serialsnoop - [http://freshmeat.net/projects/serialsnoop/](http://freshmeat.net/projects/serialsnoop/)

Is there anyone in this forum who knows one of these apps and knows how to make to sniff a USB-to-serial line without locking the port?  Thanks


UPDATE: it turns out that several of these tools will in fact work -- and they worked very well. I just had to read a bit and experiment a bit, but in the end I accomplished everything I needed to. I ended up using interceptty and I like it best of everything I tried, but I also figured out that several of the other tools listed above work as well. I'm not sure why I had so much trouble at first, because once I got interceptty working, it wasn't difficult. It works like a charm.

---

### Post by chronos00 on 2011-05-05
> **MountainX said:**
> UPDATE: it turns out that several of these tools will in fact work -- and they worked very well. I just had to read a bit and experiment a bit, but in the end I accomplished everything I needed to. I ended up using interceptty and I like it best of everything I tried, but I also figured out that several of the other tools listed above work as well. I'm not sure why I had so much trouble at first, because once I got interceptty working, it wasn't difficult. It works like a charm.

Great then! I read about all of these, but thought they all captured only one way communication.
I will try interceptty then, as you suggest.

Thanks for the heads up!

//EDIT: corrected "...captured in way..." for "...captured only one way..."

---

