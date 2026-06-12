---
title: "HELP! Wireless connection has broke down!"
date: 2005-11-10
forum: General Help
---

### Post by WGH on 2005-11-10
Hi!
I was updating and installing some games and apps.
Before i had update apps and installed synaptic on Kubuntu.
Then i wanted to install some games, but Kubuntu couldn't connect to the internet. (it's was always run perfectly!)
I looked in Net Configuration and the wireless card was mysteriously off! I have try to Enable it, but it didn't done!

What can i do?
Please, help me!!! :(

WGH...

---

### Post by tonysathre on 2005-11-10
from console do : ifup eth0

---

### Post by WGH on 2005-11-10
I've tried to do```
ifup wlan0
```and this is the message that appears```
/etc/network/interfaces:24: too few parameters for iface line
ifup: couldn't read interfaces file"/etc/network/interfaces"
```Thank's for your help, but you should know i'm new on linux!!!

WGH...

---

### Post by tonysathre on 2005-11-10
what card do u have

---

### Post by WGH on 2005-11-10
Is a D-Link 520+, but before i do all that "update" ... it runs very very well!!!
WGH...

---

### Post by ssam on 2005-11-10
hi.

can you run

```
cat /etc/network/interfaces
```

can paste the result here. it looks like it has been corrupted, judging by the error message.

---

### Post by WGH on 2005-11-10
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

# The primary network interface
iface wlan0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid casadisimone
        wireless-key1 s:mywepkey
        wireless-key s:mywepkey
iface eth0 inet

auto wlan0
```

---

### Post by ssam on 2005-11-10
ok, that looks ok. the only difference i see is that my lo stanza is empty, just

```

# The loopback network interface
auto lo
iface lo inet loopback

```

prehaps you could try commenting out the lines for lo's address and netmask

```

# The loopback network interface
auto lo
iface lo inet loopback
#address 127.0.0.1
#netmask 255.0.0.0

```

(#s cause the interpreter to ignor the lines)

i am not sure if this will make much difference, but it should not do any harm, and is easy to change back.

---

### Post by ssam on 2005-11-10
brain wave.

the line at the bottom

```
iface eth0 inet
```

needs to be

either
```
iface eth0 inet static
```
or
```
iface eth0 inet dhcp
```
or commented out
```
#iface eth0 inet
```

the clue was the number in the error message from ifup, line 24, the blank line after this line.

---

### Post by WGH on 2005-11-10
Ok, thank's you!
I've modify the file (ps: the original chmod is? 755?) and i've removed the line after ```
iface eth0 inet
```that i've also changed as ```
iface eth0 inet dhcp
```Now all works again!!!

But...what has happened!? So i can know and resolve the problem for my-self next time! :D

Thank's a lot,
WGH...

---

### Post by ssam on 2005-11-10
i dont know how it got that way. maybe you tries to edit the file by hand and missed out the dhcp. maybe the network control panel messed it up.

one thing you can do to be carefull is to backup any file before you edit it. so you would do
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```
before making any changes.

also keep a log of any changes you make. this make come in useful at some point.

i always put a comment next to any change i make, say when, why, where i got the idea from, and what it looked like before. (you should see the stuff in my xorg.conf :-) )

the other useful thing, is to read the error messages very carefully, some have far more information than first meets the eye. it took me all evening to notice that the 24 mean line 24. have a look at [http://www.ubuntuforums.org/showthread.php?p=482121](http://www.ubuntuforums.org/showthread.php?p=482121) similar problem, that i have been trying to fix this evening.

also just learn from each problem. theres lots of stuff about computers/linux i dont know about because i have not had to fix it yet. hopefully one day it will break and i can lean how it works :-)

---

### Post by WGH on 2005-11-10
OK, thank's for all your suggestions.
You also should advise me for a good guide for learning Linux's Command?!

WGH...

---

### Post by ssam on 2005-11-10
there are hundreds of guides. just search google for "linux command line" or something like that.

i learned mostly from the internet and a book (red hat for dummys). it wasn't a great book, but it got me started. i would recommend getting a book, because its when something goes wrong that you need help, and its often bad enough that you cant get online. the [oreilly]("http://www.oreilly.com") books are very good (and they are very supportive to open source.) there is [Learning the bash Shell]("http://www.oreilly.com/catalog/bash3/") which looks good (i had a browse in a bookshop but i think i know a large enough chunk of it.) or the more general [Linux in a Nutshell]("http://www.oreilly.com/catalog/linuxnut5") which covers lots of stuff.

if you want to get into bash scripting (putting several commands in a file, and then running the file), then have a look at [Advanced Bash-Scripting Guide]("http://www.tldp.org/LDP/abs/html/"). i find that very useful.

anyway have lots of fun.

sam

---

### Post by tonysathre on 2005-11-10
here is a good pdf guide i found:

[http://www.hpcc.uh.edu/usergroup/20050225/linuxquickref.pdf](http://www.hpcc.uh.edu/usergroup/20050225/linuxquickref.pdf)

---

### Post by WGH on 2005-11-11
Ok, thanks again for all yours suggestions..

Wireless is running, but the transfer from the access point to the pc seems to be...slowly!!!
There's something to do?!

Thanks,
WGH...

---

### Post by WGH on 2005-11-12
Up, please! :(

---

