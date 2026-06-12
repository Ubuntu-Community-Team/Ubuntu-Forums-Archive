---
title: "can't start x with 6.06.1 LTS"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by BlueMystic on 2007-01-03
Here's the code for my laptop: its a Toshiba P105-S6104.

What happens is I first get a fault talking about hw_random can't process then it says "RNG".

Then what happens is X tries to run and it doesn't find any resolutions that it can support. I looked at the X file and it only has the 1440 resolutions, it doesn't try any others.

I'm still very very new to linux and was wondering if anyone could help me out? This is with the shipit CD i just received and a burned (checksum checked out) of xubuntu.

---

### Post by BlueMystic on 2007-01-03
and if it helps any i just want to install ubuntu fully on my computer and completely ditch the Windows Media Center 2005. ](*,)  

:twisted: :mrgreen:

---

### Post by BlueMystic on 2007-01-03
oh and more specifically:

it uses the Intel 945GM Express Graphics

---

### Post by BlueMystic on 2007-01-04
is there maybe a laptop cd i should burn or somesuch? i've looked hi and low for a possible solution =\

---

### Post by JohnPhys on 2007-01-19
I had the same issue with a Gateway MP8708, with the RNG, the widescreen modelines, and the failure of x to start.  The GDM log said something about not finding a compatible screen or some such thing.  This was using the dapper live cd.

---

### Post by JohnPhys on 2007-01-21
I ran into the same problem, and here is how I fixed it on the edgy disc (don't worry about hw_random).

Get to a command prompt (Ctrl-Alt-F1)

run

```
sudo dpkg-reconfigure xorg-xserver
```

and let it autodetect your graphics chipset (you may have to type in the amount of video ram at some point), use all of the default options, but do not let it autodetect your monitor. 

When you get to the appropriate screen make sure (in addition to the widescreen resolution) you have 1024x768 selected (can also put in 800x600, 640x480).

Once it finishes reconfiguring your xserver, type

```
ps aux | grep gdm
```

You might see a process like /usr/sbin/gdm running (don't worry about "grep gdm", that's the command you just typed).

Kill that process by typing

```
sudo kill ####
```  

where "####" is the process ID (it's a number shown by the last command you typed, second column from the left).

Type 


```
ps aux | grep gdm
```

again just to make sure the /usr/sbin/gdm process was killed, if it was, you can just type

```
sudo /etc/init.d/gdm start
```

and you should be inside the graphical installer.

---

