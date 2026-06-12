---
title: "modprobe ndiswrapper doesnt work... sometimes"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by fusionisthefuture on 2007-04-24
ok.  ill try to be very thorough explaining this problem.  ive got a hp dv2200 laptop, 64bit amd, with a broadcom 4310 wireless card in it, and ive recently been fooling around with ndiswrapper.  i installed it using module-assistant auto-install ndiswrapper.  

at home (unencrypted wireless network, static ip from dd-wrt linksys router):  right from the get go i had problems with the gnome network manager not showing that i was connected to the network while the "network monitor", the thing that you can add to panels, does say that im connected to the network.  the network manager sees the network, but if i try to connect to it, it just times out, while im still actually connected.  

at school (unencrypted wireless network dhcp):  the network manager actually works, it sees three networks, and lets me connect to them, using its selector, and the network monitor shows im connected too.  all is well.

at both places, its like a 1 in 4 shot when i boot up my computer that sudo modprobe ndiswrapper wont work, and when i say this, all im going on for it not working is the fact that the network manager doesnt bring up a section listing the wireless networks available.  sometimes i can get it by doing a whole bunch of random screwing around with ifdown ifup eth1 and rmmod ndiswrapper and re-modprobing it, and it doesnt help to add it to the list of /etc/modules, or put it in as gksudo modprobe ndiswrapper session.  even screwing around with all that stuff and sometimes eventually getting it to work, it doesnt seem like theres any set order that actually makes it do so, but then again sometimes it works right off the bat after i modprobe ndiswrapper.  

here are some weird errors (i think) ive noticed

sometimes when im rmmod-ing and modprobing to see if it will work, this pops up

sudo modprobe ndiswrapper
Killed
user@laptop:~$ 
Message from syslogd@laptop at Tue Apr 24 17:49:11 2007 ...
laptop kernel: [  143.661678] Oops: 0000 [1] SMP 

Message from syslogd@laptop at Tue Apr 24 17:49:11 2007 ...
laptop kernel: [  143.662383] CR2: ffffc20000003519
and it will freeze the terminal right here.  

then if i try to rmmod ndiswrapper i get
ERROR: Module ndiswrapper is in use

i hope someone can help
thanks
-arne

---

### Post by fusionisthefuture on 2007-07-01
ok, for anyone else with this issue, you have to uninstall the gnome network manager, and manually configure the networks that you connect to, in order to get it to work, at least thats the way it works on my HP notebook.
-arne

---

### Post by myddewji13 on 2008-02-06
alright...i got an hp notevoook too...same prob...how do i uninstall as stated above...you have any steps written out for a beginner like me? (please and thank you)

---

### Post by myddewji13 on 2008-02-06
.

---

### Post by fusionisthefuture on 2008-02-06
you have the same laptop as me?  an hp dv2200 cto?  what ubuntu are you running?  if youre running gutsy, you shouldnt have to do anything to get the internet working.

---

### Post by myddewji13 on 2008-02-06
nope...ive got the dv2708 ca. ... and it wouldnt recognize my wireless...but its all fixed now (running gutsy)

---

### Post by myddewji13 on 2008-02-08
ok...got the same prob.... sort of...just gotta keep rebooting to fix...which is extremely annoyin (but beats not having wirless at all...) ..anyway..i was wondering if there are any alternatives to the gnome network manager?...maybe i can try them out...but i cant seem to find any..although they are mentioned (i think) all over the place....

---

