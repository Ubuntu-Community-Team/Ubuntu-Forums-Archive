---
title: "dpkg : status database area is locked by another process while trying to install oper"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Kizamime on 2008-12-18
I had downloaded the opera web browser .deb file form their website, because it wasnt in synaptic. I tried to install it in terminal, and I get this: dpkg : status database area is locked by another process
Its really annoying, because it does that with every package I try to install. Apt-get isnt running. Nothing like that is. I need all you smart Ubuntu people to help TT_TT

---

### Post by aheckler on 2008-12-18
That's odd. Try logging out, logging back in, and then installing the .deb file.

---

### Post by Kizamime on 2008-12-18
Just did. Got me nowhere.

dpkg: status database area is locked by another process

I dont understand why its not letting me......

---

### Post by aheckler on 2008-12-18
Paste the output of this please:

```
ps ax | grep dpkg
```

---

### Post by Kizamime on 2008-12-18
Okay, nevermind. Got it fixed now ^^. Thanks for the idea, I resarted and fixed some broeken things.

---

### Post by fibrebiz on 2010-08-21
Same problem, different cause.

Terminal was installing the linux mint deb packages but taking MUCH too long so I closed terminal.

ps ax | grep dpkg gives me the following:

 4554 ?        D      0:00 dpkg -i mint-common_1.0.5_all.deb mintmenu_4.9.9_all.deb mint-translations_2010.02.02_all.deb
 4888 pts/1    S+     0:00 grep --color=auto dpkg

---

### Post by nutellajunkie on 2010-08-21
I have to say, I am getting this exact same problem recently! Has some update screwed around with settigns or something?

Please help us fix this!

---

### Post by fibrebiz on 2010-08-21
Problem solved:

All it took was a simple restart. 
After restarting, the lock disappeared, then I was able to remove the package that caused the lock and try installing it again (which worked the second time around).

Though the solution was simple, it's still annoying to have to restart to kill the lock.

---

### Post by agibby5 on 2010-10-22
You could also run: 
```
sudo rm /var/lib/dpkg/lock
```

Then:
```
sudo dpkg --configure -a
```

---

### Post by balaji31d on 2010-11-01
@ agibby5 - Great! your solution worked like a charm :) Thanks!

---

### Post by aliasghar on 2011-04-04
Thanks. removing **lock file** and reconfiguring **dpkg** solved the problem.

---

### Post by thunder63cs on 2011-06-08
I am getting the same errors but have tried to clr them in the same way with out success. Here is what I get as a responce from the server:
 
 sudo dpkg --configure -a
Setting up bind9 (1:9.7.3.dfsg-1ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
[EMAIL="praetorian@praetorian:~$"]praetorian@praetorian:~$[/EMAIL] Setting up bind9 (1:9.7.3.dfsg-1ubuntu2.1) ...
-bash: syntax error near unexpected token `('
[EMAIL="praetorian@praetorian:~$"]praetorian@praetorian:~$[/EMAIL] debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
No command 'debconf:' found, did you mean:
 Command 'debconf' from package 'debconf' (main)
debconf:: command not found

 
any help to get this resolved would be wonderful...  I have rebooted adn gives me the same thing after it tries to start updating  then just hangs there not doing anything.

---

### Post by ronyv89 on 2011-08-02
Worked for me !!!!!!!!

---

### Post by ikvat on 2011-10-09
Me too Thx

---

### Post by thilinamadush on 2011-10-11
> **agibby5 said:**
> You could also run: 
```
sudo rm /var/lib/dpkg/lock
```Then:
```
sudo dpkg --configure -a
```

Thank you very much. It worked..

---

### Post by phynix123 on 2011-12-03
I was using the server remotely using webmin. When i tried to install virtualbox 4.0 the error occured.
the following commands solved the trick for me:
1. ps axgrep dpkg ( gets the process list using dpkg)
2.sudo rm /var/lib/dpkg/lock ( removes the lock on dpkg database)
3. sudo dpkg --configure -a (configure all broken packages)
4. sudo apt-get update.
 and i can continue with what i was doing.

---

### Post by leonbravo on 2012-03-15
worked for me, cheers!

> **agibby5 said:**
> You could also run: 
```
sudo rm /var/lib/dpkg/lock
```

Then:
```
sudo dpkg --configure -a
```

---

### Post by MyPod on 2012-05-07
> **agibby5 said:**
> You could also run: 
```
sudo rm /var/lib/dpkg/lock
```

Then:
```
sudo dpkg --configure -a
```
Do you run it on the iPod terminal.     Cuz it doesn't work for me please help

---

### Post by bobjohnbowles on 2012-07-05
Removing the lock file unlocks dpkg, but I still can't do anything, because when I run the configure command it re-starts the failed install at the point it left off, downloading a file at about 2 bytes/millennium. dpkg won't let me do anything til I re-type the configure command, which puts it back in the same place.
Is there anything I can do to stop this?

---

### Post by oldos2er on 2012-07-05
Please start a new thread for your question.

---

