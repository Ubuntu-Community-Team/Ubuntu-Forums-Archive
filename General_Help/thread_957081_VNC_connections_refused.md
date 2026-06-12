---
title: "VNC connections refused"
date: 2008-10-23
forum: General Help
---

### Post by danimaltron on 2008-10-23
I have followed several tutorials to get VNC running on my Ubuntu box, and I can't get pas the connection getting refused.

Originally, I tried this: [http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

When I tried connecting from my Mac on the local network, it worked fine. But I immediately went to find out how I could log into this box without first logging in on the Ubuntu. This box is a home file server, and I want to administer it from my Mac. So I want to be able to log in via VNC even if a user is not logged into Ubuntu. (I found the option to turn on auto login. Will that solve my problems?)

Then I came across [this post]("http://ubuntuforums.org/showthread.php?t=122402") that someone mentioned in another thread would solve my problem.

When I followed that tutorial and tried to start service, it said Java was not there. So I tried to install it from Synaptic.

But something seemed to conflict. Now I cannot connect via port 5900 or 5901, from localhost or Mac on the network.

I have since removed those Java packages using Synaptic to try and aleviate the problem. This hasn't changed anything.


When I try to connect via localhost from terminal, I get this:

vncviewer localhost:1

```
vncviewer localhost:1
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

I really just want to get VNC connections working. And I would like to be able to connect via VNC even if I reboot the Ubuntu box and nobody is logged in yet.

Thanks

---

### Post by danimaltron on 2008-10-24
bump. Nobody knows what I could try to narrow down the problem?

---

### Post by danimaltron on 2008-10-24
Wow, I'm just talking to myself here.

I started up vino by going to system>preferences>remote desktop. I set everything up and changed port to 5094.

Once I did that, the server showed up in the Finder on Mac Os X, saying something like "John Smith's remote desktop". It actually automatically showed up in my JollysFastVNC app that I had open on my Mac. I tried connecting and it didn't work. Then I realized it added it with the port of 5900 and a wierd hostname (it used: computername.local, 192.168.1.10)

So I guess the Ubuntu box is broadcasting the info wrong?

I then tried to manually connect with the correct port. It worked!
I then tried connecting from within the ubuntu box using "localhost" and it worked!

So I decided to reboot and see if I could log in right away. No luck. It doesnt work anymore.

This is really stupid. It started working magically, for no reason (I just changed the port. It was listening on 5091 previously and that didn't work) and now it has stopped working for no reason.

What the hell? Extremely frustrating. I thought Linux had come a long way in usability.

Anyone have any ideas?


EDIT: I can now connect from within ubuntu. But not from my Mac anymore. I did not change any network settings. Dont know whats happening.

---

### Post by atryus28 on 2008-10-24
Well I am having a similar issue and the problem I see with not having to log in is that they disconnect the network connection when you log out, with the desktop.  I really dislike this option but I can't use the server at work because it won't pickup a dhcp address but the desktop version will.

This is not a linux issue but an Ubuntu desktop issue.  When I used to use suse back in version 9 I did not need to do anything special to make VNC work and I did not need to be logged in either.

I really think that gnomes networking sucks, and with the desktop version I feel the attitude is that the average user does not need these things and they slack on them.  Just my opinion based on my experiences since 2002.

I really hope someone has some options for this stuff.  I really like ubuntu but I am thinking of switching off it again and going back to KDE and suse.

---

