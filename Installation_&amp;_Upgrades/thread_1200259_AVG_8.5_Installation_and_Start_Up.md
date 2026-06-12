---
title: "AVG 8.5 Installation and Start Up"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Lorac1949 on 2009-06-29
Has anyone installed AVG 8.5 and been able to start it up, download signatures and have it run virus scans? I've successfully downloaded it and I installed it with Gdebi Package Installer. I can't locate any documentation to get me on track for running it.:confused: Any assistance would be much appreciated.

---

### Post by raafaell on 2009-06-29
Why would install a Anti-Virus on Linux?

---

### Post by Lorac1949 on 2009-06-29
Because I've had virus attacks on three separate occassions and in each case, it trashed some of my e-mail. Yes. There are viruses in Linuxland. I was running AVG 7.5 until support [and updates] were dropped a few months ago. Before that, used ClamAV, but the viruses came right through ClamAV.

---

### Post by dtoronto on 2009-06-29
AVG will only detect viruses specific for Windows.  I could see why you may want an AVG or virus protection for a Server that interacts with other Windows PC's or servers.  If you're running Ubuntu on your desktop AVG won't do anything for your system except point out viruses that will only affect Windows based OS.  I think Clam AV is directed more toward Linux and Unix OS.

---

### Post by jrusso2 on 2009-06-29
Avg 8.5 is command line not gui.

avgscan and path you want to scan
and avgupdate to update

And you should run those with sudo.

---

### Post by moster on 2009-06-30
In email can be two type of "virus". 
      One is malicious html code where I last time heard of that is in time of internet explorer 6 few years back which had security holes like craters is moon. 
      Other type of email virus is attachment in mail something like Ana_Korunikova.jpg.exe which you must manually click and I seriously doubt it would actually work even you have installed wine.

I doubt that you actually got linux virus because that virus had to come with manual how to install it. :D Or at least it would be some .bin or .py script which you would must run sudo in terminal.

After all, be sure that hackers are not sitting in WinXP and writing viruses for linux. It is more likely that is other way around. :)

This post is has not intended to insult you, just I think that possibility for what you think is happend is 1:100000

---

### Post by Sef on 2009-06-30
> Because I've had virus attacks on three separate occassions and in each case, it trashed some of my e-mail. 

What do you use for email?  Thunderbird, Evolution, Gmail, Yahoo, or other?

---

### Post by shantiq on 2009-07-25
[B][COLOR=Blue]> **jrusso2 said:**
> Avg 8.5 is command line not gui.

avgscan and path you want to scan
and avgupdate to update

And you should run those with sudo.

i get command not found on my terminal

for    sudo avgscan


am i writing it right?[/COLOR][/B]  :)

---

### Post by RhapsodyOfFire on 2010-03-26
> **shantiq said:**
> [B][COLOR=Blue]

i get command not found on my terminal

for    sudo avgscan


am i writing it right?[/COLOR][/B]  :)
Hello. I installed the other day Ubuntu 9.10 Karmic and after that avg from the official site the debian package. I am using in the terminal these commands "sudo avgupdate" and "sudo avgscan /" / - scan the whole Linux dir and it works like a charm. So you didn't installed it right or you are typing the commands wrong. If you use sudo before a command it wants you to type the administrator password immediately but not always because of some time-out for retyping. If you type just sudo it will find the command 100% and show you some available usages.

---

### Post by mhbell on 2010-04-27
> **raafaell said:**
> Why would install a Anti-Virus on Linux?

Because you can infect windows computers even though a virus or trojan can't do harm on your computer you can still pass a virus on in email to a windows computer especially in a email attachment or file that you may have gotten and passed on to someone running windows. been there done that.
MH:(

---

### Post by rburkartjo on 2010-06-05
tks ya'll looking for this myself

---

