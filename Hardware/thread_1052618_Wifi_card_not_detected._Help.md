---
title: "Wifi card not detected. Help"
date: 2009-01-27
forum: Hardware
---

### Post by XsuperflyX on 2009-01-27
Hey guys, so I am trying Linux for the first time to see what the fuss is about. I am using my old laptop and installed 8.10 using Wubi. I am having a problem with the wifi card (PRO/Wireless 2100 mini PCI), it is not even being detected. I tired to figure out the problem and these are the only things that came up.

[http://ipw2100.sourceforge.net/#downloads](http://ipw2100.sourceforge.net/#downloads)
[http://ubuntuforums.org/showthread.php?t=92196](http://ubuntuforums.org/showthread.php?t=92196)

It is an Averatec 5110 completely stock. So I figure I need to install the driver for this but I have no idea what to do with the files. I extract the tgz and hope for an .exe but from what I see it looks like a nuch of docs with code all over them.

Any help would be awesome.

---

### Post by nixscripter on 2009-01-28
What most of the drivers require you to do is:

1. Install the **linux-headers** and **build-essential** packages from Synaptic package manager if you don't have them already.
2. Expand the tar.gz into a directory
3. Open a terminal, cd into that directory, type "make", and it will built it. Hope there are no errors
4. If you get lucky, "sudo make install" from that terminal, and then you can use the **modprobe** command to load the driver.

---

### Post by XsuperflyX on 2009-01-28
> **nixscripter said:**
> What most of the drivers require you to do is:

1. Install the **linux-headers** and **build-essential** packages from Synaptic package manager if you don't have them already.
2. Expand the tar.gz into a directory
3. Open a terminal, cd into that directory, type "make", and it will built it. Hope there are no errors
4. If you get lucky, "sudo make install" from that terminal, and then you can use the **modprobe** command to load the driver.

Sorry but you kinda lost me...

1.So I found the Synaptic Package manager program and I see three linux-headers versions but I see anything that says build-essential. How do I install that.
2. Did that.
3. How would I "cd" into a directory?
4. So I assume that once I do 1, 2, and ,3 then I just type in modprobe?

Sorry the last time I used cmd I was like 5-6 and loading up games in dos.

---

### Post by XsuperflyX on 2009-01-28
So I am trying to figure out this cd thing but not sure how it works.

I type home/xsuperflyx/ipw2100-1.2.0

This won't work, no such file or directory.

---

### Post by nixscripter on 2009-01-28
Alright, allow me to be more specific. Just open a terminal window, and type this:

```

sudo apt-get install linux-headers build-essential # <-- this is step 1
tar xvf ipw2100-1.2.0.tar.gz # <-- step 2, except you already did that
cd /home/xsuperflyx/ipw2100-1.2.0 && make # <-- step 3

```

There should be a lot of output, but no errors. If there are, you can post the output (make sure to put [code] forum tags around it).

---

### Post by XsuperflyX on 2009-01-28
Ok so I did the first step and it gave two linux-headers 
```
Package linux headers is a virtual package provided by:
linux-headers 2.6.27-7 2.6.27-7.14
linux-headers 2.6.27-7-generic 2.6.27-7.14
you should explicitly select one first
```

But that is as far as i got. I tired step two and three but nothing happened. step two said:
```
tar: ipw2100-1.2.0.tar.gz: cannot open: no such file ore directory 

```
The file is named ipw2100-1.2.0.tgz if that helps, I tried the steps with the stuff in that file extracted and then without the files on the desktop.

---

### Post by nixscripter on 2009-01-29
Whoops, minor mistake on my part:

Step 1: ```
sudo apt-get install linux-headers-generic build-essential
```

This may install a lot of packages, say "yes" anyway.

Step 2: You say it already extracted. There should be a directory called "ipw2100-1.2.0" in your Home folder. If there isn't, and the archive is on the desktop, do this:

```
cd && tar xvf /home/xsuperflyx/Desktop/ipw2100-1.2.0.tgz
```

Step 3: ```
cd /home/xsuperflyx/ipw2100-1.2.0 && make
```

---

