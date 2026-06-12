---
title: "Firefox update problem &quot;Firefox is already running...&quot;"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by jhellen on 2006-02-09
I think I followed the recently posted guide to firefox update but I got problems. I really can't see why we can't get this firefox 1.5.x to the repositories even if the previous versions are full of security risks.

I can't see firefox running running as a process but it still complains with this error message when i try to get the fox running:

Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

I have to use Galeon now and I don't have that running when I try to run Firefox. Just in case it has to do with some mozilla stuff.

---

### Post by gavinb on 2006-02-09
How did you install Firefox?  It is fairly tricky to install 1.5.  I had trouble too.  If you are having problems I would suggest removing your copy and using Automatix instead.  It worked perfectly for me.

Gavin

---

### Post by newuser111 on 2006-02-09
sudo killall -9 firefox-bin

---

### Post by jhellen on 2006-02-10
I tried to do [this]("https://wiki.ubuntu.com/FirefoxNewVersion")

$ sudo killall -9 firefox-bin
firefox-bin: no process killed

the fox is still running :twisted:  I don't think so but firefox thinks so.

---

### Post by ooby on 2006-07-15
I encountered the same problem even after installing Firefox via Automatix. I found this link useful: [http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use")

---

### Post by charafantah on 2006-08-01
i had the same problem, our network has more than 20 users, and it keep doing this every few days for one of the users, and its a headache for me to remove the lock files manually everytime, 

this small shell script will do the work for you, i placed it in ~/.kde/Autostart/ so in case this happen, the user has just to log off and on again to get firefox and thunderbird running again.

```
#!/bin/bash
#assuming profile name is made by firefox and ends with .default
#you can get correct profile name from profiles.ini

rm  -rf ~/.mozilla/firefox/*.default/lock
rm  -rf ~/.mozilla/firefox/*.default/.parentlock


rm  -rf ~/.mozilla-thunderbird/*.default/lock
rm  -rf ~/.mozilla-thunderbird/*.default/.parentlock

```

---

### Post by Paloseco on 2007-05-03
> **charafantah said:**
> i had the same problem, our network has more than 20 users, and it keep doing this every few days for one of the users, and its a headache for me to remove the lock files manually everytime, 

this small shell script will do the work for you, i placed it in ~/.kde/Autostart/ so in case this happen, the user has just to log off and on again to get firefox and thunderbird running again.

```
#!/bin/bash
#assuming profile name is made by firefox and ends with .default
#you can get correct profile name from profiles.ini

rm  -rf ~/.mozilla/firefox/*.default/lock
rm  -rf ~/.mozilla/firefox/*.default/.parentlock


rm  -rf ~/.mozilla-thunderbird/*.default/lock
rm  -rf ~/.mozilla-thunderbird/*.default/.parentlock

```
I have the problem in kubuntu 7.04 and your script does not solve the problem

---

### Post by Paloseco on 2007-05-03
Finally I solved it. I had copied the .mozilla folder from another ubuntu installation. The problem was that there were files in .mozilla directory with user and group different from the current running user.

```

sudo chown -R `whoami`:`whoami` ~/.mozilla

```

---

### Post by paulororke on 2007-12-19
Why the -rf option?  Have you not explicitly listed the specific files to rm?

```
#!/bin/bash
#assuming profile name is made by firefox and ends with .default
#you can get correct profile name from profiles.ini

rm  -rf ~/.mozilla/firefox/*.default/lock
rm  -rf ~/.mozilla/firefox/*.default/.parentlock


rm  -rf ~/.mozilla-thunderbird/*.default/lock
rm  -rf ~/.mozilla-thunderbird/*.default/.parentlock

```[/QUOTE]

---

### Post by strabes on 2008-01-04
You can run:```
ps aux |grep fire
sudo kill -9 process_id_number
```

---

### Post by ryawn on 2008-02-09
> **strabes said:**
> You can run:```
ps aux |grep fire
sudo kill -9 process_id_number
```

This worked for me perfectly. I had to kill about 5 different processes, but then firefox loaded like a charm. To anyone new at this like me, the  process ID is the 4-5 digit number that will appear to the right of the user name. For example:

```

ryan      7094  0.0  0.0   1752   524 ?        S    09:57   0:00 /bin/sh /usr/bin/firefox
ryan      7106  0.0  0.0   1756   532 ?        S    09:57   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
ryan      7110  0.4  2.4  85128 25776 ?        Sl   09:57   0:00 /usr/lib/firefox/firefox-bin
ryan      7168  0.0  0.0   2972   752 pts/1    R+   09:59   0:00 grep fire
ryan     17330  0.0  0.0   1752   448 ?        S    Feb08   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
ryan     17334 12.3 10.6 330400 109976 ?       Sl   Feb08  87:40 /usr/lib/firefo

```

I killed 7094, 7106, 7110, 17330, and 17334 to get Firefox working. Thanks Strabes.

---

### Post by milia on 2008-05-30
```
pkill firefox
```

Will do the work as well :). 
(thanx tnm for sharing the knowledge)

And thanx strabes for the first solution
to my problem :).

---

### Post by abhishekrane on 2008-05-30
This happens when u don't close firefox properly
Go to terminal and type this
```
 pgrep firefox
```
it will give the process id which is a four digit number 
say it gives 1234
```
sudo kill -9 1234
``` 
Hope that helps!

---

