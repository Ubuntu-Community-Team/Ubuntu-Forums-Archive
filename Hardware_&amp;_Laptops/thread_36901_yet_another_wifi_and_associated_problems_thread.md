---
title: "yet another wifi and associated problems thread"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by samson on 2005-05-25
Hey all, I've been reading the threads on wireless conf but haven't been able to figure anything out.

the install of ubuntu picked up my wifi card (an Intel Pro or something like that), but wouldn't connect to my router and get an IP address with DHCP. when I right click on the network connection icon on the system tray and go to preferences, I just get a dialogue saying status: error and some other info.

when I try to run System > Administration > Networking I get a Starting Networking window open but after about 10 seconds it just disappears. when I try to run a Root Terminal I get the same kind of behaviour.

If I try to open a normal terminal and run sudo ... I get this error message:

sudo: unable to lookup ubuntu-laptop via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: no such file or directory

this is a brand new install of 5.04. haven't touched anything. the install went very smoothly (except for the wifi issues). this is on my dell laptop.

any help would be much appreciated. I am trying to escape having to use windows just because it's the only thing I can get online with via wifi :-/

cheers,
samson.

---

### Post by jkndrkn on 2005-05-25
Have you looked at this page?

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

---

### Post by samson on 2005-05-26
well I've had a look at it now, but it is of little use until I can get past this error:

> 
If I try to open a normal terminal and run sudo ... I get this error message:

sudo: unable to lookup ubuntu-laptop via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: no such file or directory


as the first step in that doc is to open up a root terminal with sudo -s [pw], and I can't do that. anyone have a solution for this sudo problem?

---

### Post by jkndrkn on 2005-05-26
Try typing sudo -sh or simply prefixing every line of that how-to with sudo. You could also try running a root terminal by running the terminal using gksudo.

If your sudo command doesn't work, you have more problems than just the wifi. Try searching for sudo password issues.

---

### Post by samson on 2005-05-26
got it all sorted. I reinstalled and made sure the wired internet was setup at install. all the issues seemed to just resolve themselves automatically. then just switched over to my wireless connection and it worked fine.

---

