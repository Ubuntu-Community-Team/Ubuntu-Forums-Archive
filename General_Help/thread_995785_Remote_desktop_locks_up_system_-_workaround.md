---
title: "Remote desktop locks up system - workaround"
date: 2008-11-28
forum: General Help
---

### Post by gilbert_george on 2008-11-28
I have been having an issue making Remote Desktop connections from my Ubuntu laptop to my XP PC since I upgraded to 8.10 (although the same issue may occur with older versions).

Sometimes it worked and sometimes it locks the laptop up, so that nothing resonds to mouse clicks. My only resort being ctrl-alt-backspace to log out of the Ubuntu session.

I think I have now worked out when the the issue occurs.

The tsclient dialog has a box where you type in the ip/hostname of the box you want to connect to, this also has a drop down of previous ips/hostnames.

If I type the ip and then click on connect button all is well, but if I hit return instead of clicking the button the drop down options appear and the connection starts.

Then although the rest of the connection dialog disappears the box with the drop down options stays where it is, overlaying the opening RD window behind it.

I can then type my pwd into the RD login and the desktop from the other box appears in the window, but from then on nothing responds to the mouse or anything else afaict (on both Ubuntu and RD window) and I am only left with the ctrl-alt-backspace option.

So to avoid this click connect don't hit return.

I hope this helps anyone else.

---

### Post by finni on 2009-01-05
I have the same problem with tsclient. Please fix this bug.

---

### Post by johnswb on 2009-02-02
I'm getting the same thing on my box.  I've notice as long as I have "System Monitor" open before starting the tsclient. I can kill the RDP and everything is accessible.  I then can open another session and it will work until it locks up again.  This is getting old.

---

### Post by WatchUrSix on 2009-03-19
Has a fix been found? My PC locks up all the time when connecting remotely. Would love to see a fix.

---

### Post by overl0ad on 2009-04-20
i'll assum from the fact no new posts have been entered no one has resovled this issue i also have it and it is very aggravating .. mine will work for a little while then lock up i learned to keep out of the full screen mode and to use the force quit option from menu add bar .. but after words its a good 10 15 minutes before i have access back to any of the windows networking feature's in xubuntu

---

### Post by acemaxx on 2009-10-03
I'm having the same problem.  I'm running Ubuntu 9.04 and when I RDP using full screen mode with the tsclient that came with Ubuntu it locks up after about 10 mins.

I can't even ctl + alt + backspace.  I have to press and hold the power button and force a reboot.

I'm going to give it a test today in windowed mode and see what happens.

---

### Post by acemaxx on 2009-10-03
I tried RDC in windowed mode and it locked up after 15\20 mins.  I had system monitor up so I ended task on it.  It's fairly frustrating, as I have to boot into XP to VPN in into work without lock ups.

---

