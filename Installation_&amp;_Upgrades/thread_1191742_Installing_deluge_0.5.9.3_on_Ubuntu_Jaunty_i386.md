---
title: "Installing deluge 0.5.9.3 on Ubuntu Jaunty i386"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by Catalyser on 2009-06-19
How do I install the deluge 0.5.9.3 on jaunty i386? I have already downloaded the deb package but the button was grayed over when i tried to install it. I'm having low speed with deluge 1.1.9 and I am trying older versions to see if its any better. Help please?

---

### Post by bryonak on 2009-06-19
When you have a newer version of a program installed, you have to uninstall it first before the button becomes clickable.
```
sudo aptitude remove deluge
```
Or remove it via Synaptic, if you're more comfortable with a GUI.

---

### Post by Catalyser on 2009-06-19
Tried it already. Its still not working. The button is still grayed over.  Thanks for the reply

---

### Post by bryonak on 2009-06-19
How comfortable are you with the terminal?
Run one and change to the directory where your .deb file is, then ```
sudo dpkg -i delugeXXX.deb
```
What errors do you get? It's probably best you post the whole output.

---

### Post by Catalyser on 2009-06-19
Fairly okay with the terminal, still getting a hang of it since its been only two days since I moved to Ubuntu. Anyways, this is the output that i get after i typed in those lines.  Selecting previously deselected package deluge-torrent. (Reading database ... 173729 files and directories currently installed.) Unpacking deluge-torrent (from deluge-torrent_0.5.9.3-1_i386.gutsy.deb) ... dpkg: dependency problems prevent configuration of deluge-torrent:  deluge-torrent depends on libboost-date-time1.34.1; however:   Package libboost-date-time1.34.1 is not installed.  deluge-torrent depends on libboost-filesystem1.34.1; however:   Package libboost-filesystem1.34.1 is not installed.  deluge-torrent depends on libboost-thread1.34.1; however:   Package libboost-thread1.34.1 is not installed.  deluge-torrent depends on python2.5; however:   Package python2.5 is not installed.  deluge-torrent depends on python (

---

### Post by bryonak on 2009-06-19
Good, now try installing python(2.5), libboost-date-time, libboost-filesystem and libboost-thread via Synaptic... or a bit faster, via the terminal: ```
sudo aptitude install python2.5 libboost-filesystem[color=red]T[/color] libboost-date-time[color=red]T[/color] libboost-thread[color=red]T[/color]
```

The [color=red]T[/color] means hitting the tabulator key twice, which will list you the available options. If there is only one option, it will autocomplete after the first hit.
Much faster than Synaptic if you're used to it.


Also please put such output as above in [code]TEXT[/code ] tags... much easier to read.


EDIT: Just as information, the actual problem is that the deluge packager has failed to include dependency triggers, so you have to install them manually.

---

### Post by Catalyser on 2009-06-19
Ok, I'll try to do it. If I hit any snags again, I'll post them. Thanks a lot for the help

---

### Post by bryonak on 2009-06-19
I'd like to hear if it worked out.
Maybe it'll require downgrading current packages, which generally isn't recommended because other programs might need them... so you won't be able to run that particular version of deluge easily.

And welcome to Ubuntu ;)

---

### Post by Catalyser on 2009-06-19
After i installed all the needed things including python 2.5, I opened the deb package again and an error message popped up saying broken dependencies..

---

### Post by Catalyser on 2009-06-19
Oh, sorry, did not see your previous message as i did not refresh the page. Thanx, Ubuntu is really great. Takes the load off my system and still look pretty doing it. The only thing I miss on windows system was xunlei which can bypass traffic shaping. I read somewhere that this version of deluge is able to do that also and I'm here to try it out

---

### Post by bryonak on 2009-06-19
I haven't heard much good about xunlei (the trojan and privacy warnings), but you could try to get it to run with *wine*.
```
sudo aptitude install wine
```
Then download the xunlei exe for windows and double click. It will take quite a long time to start up, because wine needs to arrange the compatibility layer. Also chances are high that it will have bugs.

As for deluge... try the dpkg command I mentioned earlier again. What is the exact error the terminal gives?

Also you can try qbittorrent:
```
sudo aptitude install qbittorrent
```, which supports encryption that helps a bit with bandwidth throttling.

---

### Post by Catalyser on 2009-06-19
When i try the dpkg line again, i get this message ```
(Reading database ... 175286 files and directories currently installed.) Preparing to replace deluge-torrent 0.5.9.3-1 (using deluge-torrent.deb) ... Unpacking replacement deluge-torrent ... dpkg: dependency problems prevent configuration of deluge-torrent:  deluge-torrent depends on python ( 2.6); however:   Version of python on system is 2.6.2-0ubuntu1. dpkg: error processing deluge-torrent (--install):  dependency problems - leaving unconfigured Processing triggers for man-db ... Errors were encountered while processing:  deluge-torrent
``` When i look into my applications > internet, i see that deluge has been installed even after i removed it so im taking it that the command i entered was to install the deb package (Really wild guess). But i cant run it because of dependency error

---

### Post by bryonak on 2009-06-19
Well, looks like the deluge packager didn't do his homework back then (maybe it's better with the newer packages).
Not sure, but probably he checks for python 2.5.x and 2.6.0 while you have 2.6.2... or some other mistake.

I don't see a simple and quick way to install this version of deluge, short of compiling or making a new package.
Have you tried slightly newer versions of deluge or my other suggestions above?

---

### Post by Catalyser on 2009-06-19
I guess thats that then. Thanks for your help. At least I learn something new today. I'll try your suggestion with the qbittorrent

---

