---
title: "ubuntu on a packard bell / freezing on starting the hotplugging system"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by aterreno on 2006-01-21
Hi all, 
I've right now installed ubuntu on a new [Packard Bell Imedia 1508]("http://www.packardbell.co.uk/products/node1821.asp?partnumber=pb34232101")

After installing ubuntu the sistem freeze showing "starting the hotplugging system".

I would know what the system is doing this and if someone has never installed ubuntu on that machine. 

thanks a lot
ciao 
antonio

---

### Post by RavenOfOdin on 2006-01-21
Call me crazy, but I thought they became part of Hewlett-Packard?

---

### Post by TransitMan on 2006-01-23
HP and Packard Bell are seperate compaies.
PB left the North American/United States market due to some really bad press and word of mouth about their computers and designs.
PB exists and flourishes in the countries across the pond from the US, so no, HP and PB are different.

---

### Post by ddumanis on 2006-01-23
This is the only thing that worked for me:
[http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html](http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html)

Basically it's a conflict with the ALSA sound driver. Be prepared to cut and paste some commands into a terminal and wait for half an hour for the sound driver to rebuild itself. Just follow the instructions, they're pretty clear.

Hopefully Dapper will not include this "feature"...

---

### Post by aterreno on 2006-01-24
Thanks! On the page you linked there's this sentence:

> You need to blacklist the snd-hda-intel kernel module from being
loaded automatically by appending it to /etc/hotplug/blacklist . 

Sorry, How to do it at boot time? 

thanks a lot, thanks again

---

### Post by bbmw on 2006-01-24
[QUOTE=aterreno]Thanks! On the page you linked there's this sentence:



Sorry, How to do it at boot time? 

thanks a lot, thanks again[/QUOTE]
I have had the same problem with a HP/Compaq using the live cd, try the solution here >> [http://ubuntuforums.org/showthread.php?t=116850](http://ubuntuforums.org/showthread.php?t=116850)
only you will want to replace the word "live" with "linux" or whatever you 
need to use to boot the install disk

      EDIT >> I think you need to replace "live" with  "install"

---

### Post by ddumanis on 2006-01-24
No, you have to edit /etc/hotplug/blacklist *before* you boot. You can't edit it as a user, so the easiest way is to type

gksudo nautilus

into a terminal, and that will open a gnome window where you will have root privileges. You can navigate to the file in question from there.

And don't forget to change it back like he says in his post!

P.S. Be careful with root privileges--I have blown up my system more than once by misusing them...


[I]Quote:
You need to blacklist the snd-hda-intel kernel module from being
loaded automatically by appending it to /etc/hotplug/blacklist .

Sorry, How to do it at boot time?[/I]

---

