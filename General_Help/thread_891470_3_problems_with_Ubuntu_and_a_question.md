---
title: "3 problems with Ubuntu and a question"
date: 2008-08-16
forum: General Help
---

### Post by rakan_dr on 2008-08-16
Hi folks,
i have probs with Ubuntu:
1-Firefox always in offline mode till i click File> deactivate the offline mode. So what should i do to solve it?
2-I can't use the scroll in my mouse. The normal scroll is Ok, but when i click the scroll   button and i try to scroll in the fast way it doesn't work, actually i can't see the two arrows that are close to each other.
3-I couldn't find my City in the Weather applet, how can i add it?

Q:How can i see the opening ports in my Os. i.e: I want to know which applications use the internet and the activities of the internet in my OS, and how to control it.

Thanks.

---

### Post by thestig_992 on 2008-08-16
> **rakan_dr said:**
> Hi folks,
i have probs with Ubuntu:
1-Firefox always in offline mode till i click File> deactivate the offline mode. So what should i do to solve it?
2-I can't use the scroll in my mouse. The normal scroll is Ok, but when i click the scroll   button and i try to scroll in the fast way it doesn't work, actually i can't see the two arrows that are close to each other.
3-I couldn't find my City in the Weather applet, how can i add it?

Q:How can i see the opening ports in my Os. i.e: I want to know which applications use the internet and the activities of the internet in my OS, and how to control it.

Thanks.

q1--> i dont know how to change that, is it possible that you keep closing firefox in offline mode and it remembers that? if you type about:config into the adress bar you can acess all the advanced settings, but be carefull doing this as you can damamge firefox beyond repair. Try seaching for offline or something like that.

q2-->thats a windows only function, it might be possible to bind that as a hotkey, but without a special program it wont work the same way as windows.

q3 --> ubuntu seems to have most major cities around the world, if they dont have your exact one, then just choose the closest. There may be other weather applets that will have you location, so if youre really concerned you can try one of those.

q4--> That sounds an awful lot like a firewall. I use firestarter, which gives you stats about what programs are using what ports and what IPs theyre connected to...also alows you to block individual ports and IPs...etc. Installing that should give you some customisation

---

### Post by ajmorris on 2008-08-16
> **thestig_992 said:**
> 
q2-->thats a windows only function, it might be possible to bind that as a hotkey, but without a special program it wont work the same way as windows.
Actually, that can be done in firefox in linux, it is just not on by default. Go to firefox preferences, then to the advanced tab, and select "Use AutoScrolling".

AJ

---

### Post by thestig_992 on 2008-08-16
> **ajmorris said:**
> Actually, that can be done in firefox in linux, it is just not on by default. Go to firefox preferences, then to the advanced tab, and select "Use AutoScrolling".

AJ

hahaha wow. now i look like an ***...

---

### Post by rakan_dr on 2008-08-16
ohh thnx men a lot! Where and how can i install that firestarter?

plzzz someone help me with the offline mode!

---

### Post by ellalan on 2008-08-16
> **rakan_dr said:**
> Hi folks,
i have probs with Ubuntu:
1-Firefox always in offline mode till i click File> deactivate the offline mode. So what should i do to solve it?
2-I can't use the scroll in my mouse. The normal scroll is Ok, but when i click the scroll   button and i try to scroll in the fast way it doesn't work, actually i can't see the two arrows that are close to each other.
3-I couldn't find my City in the Weather applet, how can i add it?

Q:How can i see the opening ports in my Os. i.e: I want to know which applications use the internet and the activities of the internet in my OS, and how to control it.

Thanks.

I have a solution for your 1st question and here it is:
Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

---

### Post by Tom--d on 2008-08-16
> **ellalan said:**
> I have a solution for your 1st question and here it is:
Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

Or, my way.
**If you are not using Network Manager** remove it. 
Open up terminal, and copy this in.
```
sudo apt-get purge network-manager network-manager-gnome
```

No more offline mode.
Offline mode starting in firefox is due to Firefox looking at Network Manager for a connection. If there is no connection (not being used). AS I use a other method of getting a connection, it starts in offline mode. Once you go in online mode, it looks for the alternates for a connection.
Removing Network Manager solves this due to Firefox looks for alternate connections because there is no Network Manager. No offline mode :D

Hope it helped.

---

### Post by mb_webguy on 2008-08-16
Q4:  By default, all ports on Ubuntu are open in the sense that they aren't blocked.  Nothing can get in, however, unless a program is listening at a given port.  It's a bit like sending mail to an empty house.  And since programs don't (and can't) install themselves in Linux, you should already have a basic idea of what ports are open in the sense that they're active, since you should have a pretty good idea what software you have installed and running.  Web browsers use port 80, FTP uses 21, SMTP email uses 25, and so on.  If you run a bittorrent or other file-sharing client, or games with online play, they'll use one or more ports as well, which you should be able to determine from the program settings.

If you're really concerned, however, try installing Network Mapper ("sudo apt-get install nmap").  It has a number of uses in scanning for network security holes, including a port scanner.  Ubuntu *does* come with a firewall, or so I've been told, but I've never seen any need to activate it.

Also, you could go to [this website]("http://www.pcflank.com/scanner1.htm") to do an online scan.  Be aware that the website will recommend you install a firewall (preferably theirs) regardless of the results of the scan.

---

### Post by Tom--d on 2008-08-16
> **mb_webguy said:**
> Q4:  By default, all ports on Ubuntu are open in the sense that they aren't blocked.  Nothing can get in, however, unless a program is listening at a given port.  It's a bit like sending mail to an empty house.  And since programs don't (and can't) install themselves in Linux, you should already have a basic idea of what ports are open in the sense that they're active, since you should have a pretty good idea what software you have installed and running.  Web browsers use port 80, FTP uses 21, SMTP email uses 25, and so on.  If you run a bittorrent or other file-sharing client, or games with online play, they'll use one or more ports as well, which you should be able to determine from the program settings.

If you're really concerned, however, try installing Network Mapper ("sudo apt-get install nmap").  It has a number of uses in scanning for network security holes, including a port scanner.  Ubuntu *does* come with a firewall, or so I've been told, but I've never seen any need to activate it.

Also, you could go to [this website]("http://www.pcflank.com/scanner1.htm") to do an online scan.  Be aware that the website will recommend you install a firewall (preferably theirs) regardless of the results of the scan.

All ports are closed on an default installation, not open ;)
And yes, Nothing is listening on those ports.
Your quite safe without a firewall, until you start installing server software.

---

### Post by thestig_992 on 2008-08-16
> **rakan_dr said:**
> ohh thnx men a lot! Where and how can i install that firestarter?

plzzz someone help me with the offline mode!

to install firestarter either go to applications -> add/remove programs -> (search for firestarter) -> im sure you can work out the rest...

or in terminal type:
```
sudo apt-get install firestarter
```

first way is safer just incase i got the package name wrong

---

### Post by mb_webguy on 2008-08-16
> **Tom--d said:**
> All ports are closed on an default installation, not open ;)
And yes, Nothing is listening on those ports.
Your quite safe without a firewall, until you start installing server software.

I think that there's some confusion between the ideas of an open, closed, and stealthed port.  People who don't know better (and many who do, but don't see the point in confusing people) refer to what is actually a stealthed port as "closed", and any port that isn't stealthed (which unfortunately includes closed ports) as "open".

By default, all ports in Ubuntu are closed but not stealthed.  To put it simply, no one will answer the door when you knock, but neither is anyone standing in the way to keep you out.  Since the only way in, according to this analogy, is for someone to open the door for you, then it doesn't really matter if someone (like a firewall) is actually keeping you from approaching the the door or if no one is inside to answer the door when you knock.  You can't get in either way.  The purpose of a firewall is to act like a bouncer at a club.  There are people at the door of the club ready to let you in, but the bouncer stands outside checking your ID before letting you pass.  

If you run "sudo iptables --list", I think you'll find default policies of ACCEPT for all INPUT, OUTPUT, and FORWARD rules.  However, there is nothing in a default installation listening at the ports.
Ubuntu doesn't have a bouncer on staff, but the club is closed.  You're not dancing in either way.

---

### Post by lswest on 2008-08-16
And I'd just like to point out that iptables is actually the firewall, firestarter is just a user interface for configuring the different rules (which generally can be left as is unless you're running a server)

---

### Post by rakan_dr on 2008-09-18
is it secure to remove Network Manager????

---

