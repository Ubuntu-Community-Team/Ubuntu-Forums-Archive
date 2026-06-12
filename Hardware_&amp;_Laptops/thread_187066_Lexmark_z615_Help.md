---
title: "Lexmark z615 Help"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by Xtife on 2006-06-02
Heyas

im a linux beginner, but a seasoned windows user
i just installed dapper today, had a bit of trouble trying to get partitions setup but figured it out in the end :)

it detected all but one piece of hardware afaik. my printer
a lexmark z615. i downloaded the drivers and searched the forums here
for some instructions. i found this
[http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+z615](http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+z615)

and followed the instructions, when it got to the point where i had to extract the rpm 
"sudo alien -t z600cups-1.0-1.i386.rpm" but it said this "sudu: alien: command not found" im thinking these commands no longer work in 6.06 since the guide was made for the last ubuntu version. 

i was hoping someone could help walk me through installing this on 6.06

---

### Post by jon_gunnar on 2006-06-02
[QUOTE=Xtife]Heyas

im a linux beginner, but a seasoned windows user
i just installed dapper today, had a bit of trouble trying to get partitions setup but figured it out in the end :)

it detected all but one piece of hardware afaik. my printer
a lexmark z615. i downloaded the drivers and searched the forums here
for some instructions. i found this
[http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+z615](http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+z615)

and followed the instructions, when it got to the point where i had to extract the rpm 
"sudo alien -t z600cups-1.0-1.i386.rpm" but it said this "sudu: alien: command not found" im thinking these commands no longer work in 6.06 since the guide was made for the last ubuntu version. 

i was hoping someone could help walk me through installing this on 6.06[/QUOTE]
It may be as simple as alien is not installed.
Do a
```
sudo apt-get install alien
```

---

### Post by Xtife on 2006-06-02
i figured it was something that was installed automaticly when i installed ubuntu

i will check it out :) thanks

---

### Post by givré on 2006-06-02
I had a problem to get working my lexmark z600 (which is pretty the same printer) in dapper.
If it's work good for you, you are lucky, if not, you could have a look at that
[http://www.linuxprinting.org/pipermail/lexmark-list/2005q3/003194.html](http://www.linuxprinting.org/pipermail/lexmark-list/2005q3/003194.html)
It solve my problem

---

### Post by Xtife on 2006-06-02
i managed to install the drivers after i had to installed alien

but i i couldnt print, even after trying givre's suggestions

---

### Post by Xtife on 2006-06-04
does no one have an explaination for this?

its not really a problem, i can always print in windows :)
just wanted to see if i could get everything working

---

### Post by givré on 2006-06-04
An other howto which is far more better (just try it and it works perfectly).
[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=z600](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=z600)

This is quite the same, but the difference is that you don't convert the .rpm to .deb which preserve you to some permissions problems. The desavantage is that you will not be able to uninstall them with apt-get, but anyway, when it's work...

Follow that to the letter and it should just work. Say me if it's ok.

EDIT: The backend thing return nothing to me, but it's work.

---

