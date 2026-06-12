---
title: "[SOLVED] Rythmbox"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by GROMS on 2008-12-05
Not sure if this is right place -

In Rythmbox I was trying to get a radio station to play but got an error. Doing a search I found a thread (Ubuntu hekp) on 'Playing Restricted Formats'. they said to:
```

 apt-get install ubuntu-restricted-extras

```
At the command prompt it started and started downloading. Got one window to accept licenae to which I clicked the 'OK' button. It then started to install java. It opened an licensing window titled 'Configuring Sun-Java-jre' I could use the up/down keys and the mouse wheel to scroll the page which had a 'OK' at the bottom but I couldn't get the OK click to take. It appeared to freeze - or not respond. Closed the Terminal window and opened the Synaptic Packager - got ERROR box stating
> 
E: dpkg was interupted - must manualy run 
'dpkg --configure - a' to correct
E:_crash -> open() failed, please report
               CLOSE button

Clicking closed, closed Synaptic.
Can I assume that the closing of the terminal window caused this? and would I execute the dpkg statement above at the terminal prompt and should it be done as sudo?
Also who do I "report" to??
Stephen

---

### Post by ibutho on 2008-12-05
Run Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```

---

### Post by GROMS on 2008-12-06
> **ibutho said:**
> Run Applications -> Accessories -> Terminal and enter
```
sudo dpkg --configure -a
```

Ok, did. Not real sure what it did (man page) - anyway, opened Synaptic and did the fix for broken packages and it starts the java6 thing again. It gets to 
> 
Processing triggers for libc6...
ldconfig deferred processing now taking place


and has been sitting there for 10 minutes. Any ideas???

---

### Post by GROMS on 2008-12-07
Finally finished with no errors. Whoever, I still can't get
```

http://947thewave.com

```
to play - when I double click it I get the "connecting" bar at the bottom right of the screen and nothing. Any other Ideas??

---

