---
title: "Canon i560 rpm to dev"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by bluemuffin on 2005-09-29
i'm trying to wean myself from windows and is 3 days into ubuntu, i'm already groggy. i need help with intalling my canon i560.
I have already downloaded bjfilterpixus560i-2.4-0.i386.rpm and bjfiltercups-2.4-0.i386.rpm from the Canon website unto my desktop.
I have already apt-gotten and installed alien.
when i try to convert rpm into dev using the following code:
sudo alien bjfilterpixus560i-2.4-0.i386.rpm
the terminal says:
file not found.
This is how it looks like in the terminal:
redone@red-one:~$ sudo alien bjfilterpixus560i-2.4-0.i386.rpm
File "bjfilterpixus560i-2.4-0.i386.rpm" not found.
please, i need help. what am i doing wrong? i am not a techno-geek and only have 3 days worth of linux in me.
:???:

---

### Post by remin8 on 2005-09-29
Try this... cd to your directory like this:

```
# cd /home/username/Desktop/
```

then chmod your file so that it can be executed:

```
# chmod 0777 yourfile
```

then to install:

```
sudo alien -i yourfile
```

I am not the best with CLI but these should be close. Hope this helps!

---

### Post by xmastree on 2005-09-29
Have you tried using the BJC-7000 driver already on your system? That's what I use for my i560

---

### Post by bluemuffin on 2005-10-06
**xmastree**

I've tried the easier way by installing bjc 7000 driver but my i560 doesn't print right. The text looked kind of fuzzy even with high quality and when i tried the highest resolution the fonts just got larger. There is also a problem with the margins,they don't come out like in OOwriter. I've tried pushing every button in the driver properties to get it to work right. Thanks.


**Remin8**

SO that's how you CD into a particular directory. I've installed the Pixus i560 driver as instructed minus the libtiff3g file. Probelm is, printer and driver does not seem to communicate. There was no page printed when I tried the print test page button. In fact, there was no single action from the printer indicating that it understood what it was supposed to do. I'd be happy even if it just grunted.

Regarding the libtiff3g file. the follwing error resulted when I tried to apt-get install it.
[I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libtiff3g[/I]

Libtiff3g is supposed to be in the Universe repository but Synaptic can't seem to find it. Any idea how I can load this file? Like a specific directory or address that I can type in the terminal or Synaptic?

Thanks for the assist guys, I'm learning Linux bit by bit, even though it's been like pulling teeth.

BTW, how do I know if my ubuntu is a warthog or a hedgehog? I am not really sure what I am using.

BTW-2, I am also googling to find possible answers but so far I've fopund none.

---

### Post by xmastree on 2005-10-06
[QUOTE=bluemuffin]**xmastree**
I've tried the easier way by installing bjc 7000 driver but my i560 doesn't print right. The text looked kind of fuzzy even with high quality and when i tried the highest resolution the fonts just got larger.[/QUOTE]I find that I need to set it to 600x600 otherwise it's all wrong. Photos aren't good, and landscape prints are completely screwed up.
If I want to print nicely, I reboot into windows.

---

### Post by bluemuffin on 2005-10-10
Hey, Thanks.

I've sort of left my problem with the i560 for now, hoping that it would just solve itself in time.  :D 

I work for a government agency in CDOC and we are seriously considering adopting Linux for our system (approx 70 computers from P-II to P-IV w/ LAN). My superiors must have this idea that if I learn Linux then maybe all our computer operators can learn it too, considering that I am not a computer course graduate and a techno-geek. I'm also trying to learn how to add another HDD (slave) and then network Ubuntu desktops. Geez, I am already having migraines.

Hope you will inform me in case you find a better way for your i560 to work in Linux.

Thanks again.

---

### Post by coolclassic on 2005-10-10
Your printer is supported by [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)
you may find there drivers useful.

---

