---
title: "Windows xp to Ubuntu with laserjet 1000"
date: 2010-05-19
forum: Hardware
---

### Post by Janjiss on 2010-05-19
Hello,
I Have hp Laserjet 1000 printer, wich works fine in Ubuntu network. It is shared and prints well from ubuntu machines.I tried to connect to Ubuntu shared printer from windows machine by typing adress [http://192.168.*.***:631/printers/hp-laserjet-1000](http://192.168.*.***:631/printers/hp-laserjet-1000)., selecting driver and adding to printers list. It sends a job to Ubuntu Machine, I can see it in CUPS and job quanue, but it does not print. After a while it  shows xp machines print jobs in completed list. 

I am using Lucid.

Hope I explained my problem well.

Any help == Thanks :)

---

### Post by Janjiss on 2010-05-19
((BUMP))

Please, matter of life or death... :/

---

### Post by garmengod@gmail.com on 2010-06-12
> **Janjiss said:**
> ((BUMP))

Please, matter of life or death... :/
Hi 

I installed samba first, made printers browseable.

Try downloading the postscript package from here
[http://www.adobe.com/support/downloads/thankyou.jsp?ftpID=1508&fileID=1446](http://www.adobe.com/support/downloads/thankyou.jsp?ftpID=1508&fileID=1446)

Install the package and install the printer as a network printer browsing it , if it does not find a good driver install the generic postscript driver.

This worked for me , I hope you are succesful too.

---

### Post by srivo on 2010-06-15
I have exactly the same problem using samba. With ubuntu are you using hplip or foo2zjs?

When I was using foo2zjs it was working but not very reliable nether on windows or linux machine. hplip look more reliable for linux but doesn't seem to work with windows.

I will try garmengod solution to see if it work.

---

### Post by srivo on 2010-06-18
Look like any Postcript driver work. I install the HP 1200 PS driver on windows XP and Vista64 machine and it work!

Thanks!

---

