---
title: "[SOLVED] if a student at my school boots a computer on ubuntu ?"
date: 2008-11-07
forum: General Help
---

### Post by reinaldistic on 2008-11-07
will he/she be able to bypass the internet firewall that blocks some sites(which we have)?

(we currently have xp on pcs and osx on macs) and they are both blocked by the firewall, but would ubuntu be able to go around that?

---

### Post by technotitclan on 2008-11-07
depends on the method that they installed the firewall and filter settings. is it a large school or small town school? if its a small town high school the it will posibly work since they don't have the money to spend on a proper firewall/filter. if its a big school or university your prolly out of luck. either way, i would give it a go and post back w/ the results.

---

### Post by beno1990 on 2008-11-07
No, they're usually blocked from the proxy level. Which means they have a server which actively blocks these sites from being accessible from within the network.

---

### Post by Coreigh on 2008-11-07
Regardless of size any properly configured firewall will be the gateway to the internet and all policing is done at the gate. The only exception I can think of is if the Windows / Mac computers are domain members inside the private LAN (inside the gate) and personal computers are non domain members in the DMZ (outside the gate).

---

### Post by technotitclan on 2008-11-07
except small schools that don't have the funding to bother w/ that. my high school ran on a very limited budget so they had it bult into the os and had all the systems boot off the network. i managed to get though it when i booted to linux instead of off the network. but its been a while since then so they may have fixed that.

---

### Post by Portmanteaufu on 2008-11-07
You could always do this: 

1.) Set up a computer running Ubuntu (or some other distro) at home.
2.) Install the Open-SSH server. Make sure it has X-forwarding enabled.
3.) Configure your home router to forward port 22 to that computer. See [http://portforward.com]("http://portforward.com") for help on doing this.
4.) At school, on one of the Mac OS X computers, open a terminal and run: 
```
ssh -Y username@[home IP address]
```
5.) Log in and run Firefox

If you do all this properly, it will open up your at-home firefox window on your computer at school. All your internet traffic will be going from your computer at home to the internet. The traffic from your home computer back to the school to show you what's going on will all be encrypted.

It's a bit of work if you don't have an ubuntu box at home but if you do, it should make for a relatively simple way around the proxy filter.

Note: Depending on your school's connection and your home connection, this could be -very- slow. It would probably suck a lot for watching video. However, if you have broadband both at home and at school then it should work alright for typical viewing.

---

### Post by ByteJuggler on 2008-11-07
> **reinaldistic said:**
> will he/she be able to bypass the internet firewall that blocks some sites(which we have)?

(we currently have xp on pcs and osx on macs) and they are both blocked by the firewall, but would ubuntu be able to go around that?

If you have a proper hardware/router firewall the answer is generally no.  There is nothing magical about Ubuntu that will allow it to sidestep an external firewall.  (SSH port forwarding workarounds as mentioned by another poster will also only be possible if your firewall allows SSH/port 22 traffic through and/or allows it to be proxied to a student's house.  If your firewall strictly proxies only HTTP then that also wont be possible.)

---

