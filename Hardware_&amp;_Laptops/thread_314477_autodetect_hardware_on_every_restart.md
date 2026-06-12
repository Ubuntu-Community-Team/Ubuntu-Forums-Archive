---
title: "autodetect hardware on every restart ?"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by viluve on 2006-12-07
Hi experts,

Here's my situation: I installed Ubuntu 6.10 on my portable HDD so that I can use Ubuntu on different machines. The problem is that when I tried to use different machine, Ubuntu keeps using the previous machine's setting to load and causes video card incompatiblity (this isn't a problem if I use Live CD).

Q: 
1. Is it possible to autodetct hardware each time we restart Ubuntu (as if running from a Live CD) ?
2. If yes, how ? can someone direct me to some wb help/tutorial to do so ?

THanks in advance..
Ubuntu ROCKS..

---

### Post by averagejoe84 on 2006-12-07
You could add a script to the start up with the following in it.

dpkg-reconfigure -phigh xserver-xorg

This will automatically reconfigure your display settings.

---

### Post by viluve on 2006-12-07
> **averagejoe84 said:**
> You could add a script to the start up with the following in it.

dpkg-reconfigure -phigh xserver-xorg

This will automatically reconfigure your display settings.

Thanks for your reply,
I'm really new at Linux, can you maybe tell me to what file is that line needs to be added

---

### Post by averagejoe84 on 2006-12-07
Leme doo some reading on the new boot up process to see if it can just be added to a file. The trick is getting it to reconfigure xorg before X trys to start.

---

### Post by averagejoe84 on 2006-12-07
It seems that you can create a job to do this.

Note I have yet to try this as I am at work and without my Ubuntu box.

> Jobs are defined in files placed in /etc/event.d, the name of the job is the filename under this directory. They are plain text files and should not be executable.

sudo vi /etc/event.d/xconfig

then add the following lines to the file by hiting i to insert text.

> script
    # reconfigure x server
    dpkg-reconfigure -phigh xserver-xorg
end script

to save this hit the esc key followed by :wq

I think this should do what you want it to do - I will test this when I get home tonight if I have time. let me know if this works for you if you try it.

---

### Post by viluve on 2006-12-07
Thanks buddy !!
I am also at work at the mo., I'll try it at home & will let you know the results.
Thanks again..

---

